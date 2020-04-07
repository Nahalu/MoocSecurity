# Vulnerabilities

## Server vulnerability / Communication vulnerability

We saw before while browsing the internet, that it is possible to have data stolen or server having vulnerability, but, what are the cause ?

### MITM

**man-in-the-middle attack (MITM)** is an attack where the attacker secretly relays and possibly alters the communications
between two parties who believe that they are directly communicating with each other. One example of a MITM attack is active
**eavesdropping**, in which the attacker makes independent connections with the victims and relays messages between them to make them
believe they are talking directly to each other over a private connection, when in fact the entire conversation is controlled by the attacker.

A MITM attack is generally used to rondabout a safe access point to make a false one. When a users connected to it, a hackers can see what he's doing.
The dangerous part of that attack is that the users do not know that even on a HTTPS website the hackers can see what he is doing.

### Slow Lorris

Slowloris is a type of denial of service attack tool invented by Robert "RSnake" Hansen which allows a single machine to take down another machine's web server
with minimal bandwidth and side effects on unrelated services and ports.

Slowloris tries to keep many connections to the target web server open and hold them open as long as possible.
It accomplishes this by opening connections to the target web server and sending a partial request.
Periodically, it will send subsequent HTTP headers, adding to�but never completing�the request.
Affected servers will keep these connections open, filling their maximum concurrent connection pool, eventually denying additional connection attempts from clients.

### Communication trust

The problems using communication system is that, sometimes, it can be used against us.

#### How ?

Sometimes when we want to access a new website and create a new account, we need to give our email address, and enter
a new password, and we used without thinking the same password over and over again... Which is a problem here.

When we encounter a malicious website, it can exploit our email account sometimes without us knowing it, and searching
for precious information, Those information leaked can be anything, its even worse when its related to the company of
the users...

#### Why ?

Those data are considerated precious in the dark web, and is exchanged for money.

#### How to protect ourself ?

The first thing to do is to be sure to use a different password for our account on website and email, and use a strict 
password in any case (Password, number, special character...).

### Conclusion

To conclude this part of the MOOC **Browsing The Internet**, we saw that they are multiples threat wich is due to website not having a good security set,
however, there is also a possibility that a good website can have vulnerabilties unknow for users or that an access point that you are using is infact one that a
hackers set, that is why you need to be sure on what you are willing to share on those website and the access point that you are using.
