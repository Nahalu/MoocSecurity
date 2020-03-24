# Limiting Request Rates

Let’s say that you wanted to block any client making more than 10 requests per second. The http_req_rate(10s) counter that you added will report the number of requests over 10 seconds. So, to cap requests at 10 per second, set the limit to 100.

In the following example, we add the http-request deny directive to reject clients that have gone over the threshold:

![Alt Text](../assets/DDos/limit.png)

This rule instructs HAProxy to deny all requests coming from IP addresses whose stick table counters are showing a request rate of over 10 per second. When any IP address exceeds that limit, it will receive an HTTP 429 Too Many Requests response and the request won’t be passed to any HAProxy backend server.
These requests will be easy to spot in the HAProxy access log, as they will have a termination state of PR–, which means that the session was aborted because of a connection limit enforcement:

Feb 8 17:15:07 localhost hapee-lb[19738]: 192.168.1.2:49528 [08/Feb/2018:17:15:07.182] fe_main fe_main/<NOSRV> 0/-1/-1/-1/0 429 188 - - PR-- 0/0/0/0/0 0/0 "GET / HTTP/1.1"
view raw
If you’d like to define rate limit thresholds on a per URI basis, you can do so by adding a map file that pairs each rate limit with a URL path. See our blog post Introduction to HAProxy Maps for an example.

Maybe you’d like to rate limit POST requests only? It’s simple to do by adding a statement that checks the built-in ACL, METH_POST.

![Alt Text](../assets/DDos/iptable.png)

You can also tarpit abusers so that their requests are rejected with a HTTP 500 status code with a configurable delay. The duration of the delay is set with the timeout tarpit directive. Here, you’re delaying any response for five seconds:
timeout tarpit 5s
http-request tarpit if { sc_http_req_rate(0) gt 100 }
view raw

When the timeout expires, the response that the client gets back after being tarpitted is 500 Internal Server Error, making it more likely that they’ll think that their assault is working.
