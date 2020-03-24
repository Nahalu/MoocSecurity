# Defining the Storage

Create a stick table by adding a **stick-table** directive to a **backend** or **frontend**.  
In the following example, we use a placeholder backend named per_ip_rates. Dedicating  
a backend to holding just a stick-table definition allows you to reference it in multiple  
places throughout your configuration.

_Consider the following example:_

![Alt Text](../assets/storage.png)

This sets up the storage that will keep track of your clients by their IP addresses. It initializes a counter that tracks each user’s request rate.

_Begin tracking a client by adding an **http-request track-sc0** directive to a **frontend** section, as shown:_

![Alt Text](../assets/frontend.png)

With this configuration in place, all clients visiting your website through HAProxy via the **fe_mywebsite** frontend will be stored  
in the **per_ip_rates stick table.** All of the counters specified in the stick table definition will be automatically maintained and updated by HAProxy
