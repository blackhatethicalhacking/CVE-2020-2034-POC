# CVE-2020-2034-POC
Determine the Version Running on the Palo Alto Network Firewall for the Global Protect Portal

Recently a lot of critical vulnerabilities were announced by Palo Alto Networks here:
https://security.paloaltonetworks.com/?severity=CRITICAL&product=PAN-OS&sort=-date

This is a PoC to determine the version used by the firewall, by examining the etag from a curl scan on their favicon, and login.esp

Reference:

CWE-78 Impact:
https://cwe.mitre.org/data/definitions/78

By the Register:
https://www.theregister.com/2020/07/09/palo_alto_fix/

 By Vulmon
https://vulmon.com/searchpage?q=paloaltonetworks

![alt text](https://avatars1.githubusercontent.com/u/39441336?s=280&v=4)

Instructions:

Make sure to have latest Python3




Demo:

curl -skI https://example.com/global-protect/login.esp

HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Connection: keep-alive
ETag: "5e4c6-2f3g-5b650798"

In order to determine this, we have to do some examination of the etag of some of the URLs, by doing so, we will gather the last 8 characters from the Etag, and it will be in hexadecimal, so converting it to decimal, then from epoch time, to human readable time, we will be able to decipher the version it is used, and check if it is vulnerable or not to this OS Command Injection recently released by Palo Alto Networks.

So from the demo example, we are interested in the last 8:

5b650798

Convert this from hexadecimal to decimal, then from decimal epoch time to human readable.

You will get this:
Sat Aug  4 04:55:36 EEST 2018

Then Check if its vulnerable based on the versions announced.

This will attempt to do this once you run it.


Legal disclaimer
Usage of this tool for testing targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state, and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program.
