# Server Side Request Forgery (SSRF)

**What is SSRF?**

Server Side Request Forgery or short SSRF is a web security vulnerability that allows an attacker to induce the server and make requests to locations that 
are only not intended for admins or authenticated users.

In an typical SSRF attack the attacker might cause the server to connect to internal services of the system. In other cases they might force the server
to connect to external systems and leak sensitive data such as passwords and other authentication credentials.
