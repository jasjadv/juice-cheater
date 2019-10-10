# juice-cheater
OWASP Juice Shop (Cheat Module) - Why you shouldn't use the Juice Shop for CTF-events rewarding prizes.

# Introduction
OWASP Juice Shop is a very nice way to train security/hacking skills. However when using the shop in CTF-events be aware of the fact it is fairly simple to abuse the continue-code of the shop to fake any progress without figuring out a challenge at all. 

This python program is a proof-of-concept abusing the continue-code feature of the juice-shop. 

NOTE: Please only use this program on an instance of the OWASP Juice Shop you control yourself or has been setup for you alone. So don't be a jerk and use this on public instances of the OWASP Juice Shop!

# Usage
#### Get started
Be sure to install hashids:
```sh
$ pip install hashids
```
#### Usage
General:
```sh
$ ./juice-cheater [urL] -[option]  
```
Where [url] is the address where the OWASP Juice Shop instance can be found and [option] is one of these choices:
  - check : run a test to see if the OWASP Juice Shop can be reached and the progress per challenge;
  - challenge [num]: "solve" a specific challenge given by the provided [num];
  - all: solve all challenges at once.

#### Examples
Example to check to see if things work correctly and/or the current progress:
```sh
$ ./juice-cheater http://127.0.0.1:3000/ -check

OWASP Juice Shop cheater 0.11 PoC
[OK] OWASP Juice Shop found at provided URL
[OK] Challenges found: 88

[UNSOLVED] Challenge 01 (API-only XSS)
[UNSOLVED] Challenge 02 (Access Log)
[UNSOLVED] Challenge 03 (Admin Registration)
[UNSOLVED] Challenge 04 (Admin Section)
[UNSOLVED] Challenge 05 (Arbitrary File Write)
[UNSOLVED] Challenge 06 (Bjoern's Favorite Pet)
[UNSOLVED] Challenge 07 (Blockchain Hype)
[UNSOLVED] Challenge 08 (Blocked RCE DoS)
[UNSOLVED] Challenge 09 (CAPTCHA Bypass)
[UNSOLVED] Challenge 10 (Change Bender's Password)
[UNSOLVED] Challenge 11 (Christmas Special)
[UNSOLVED] Challenge 12 (Classic Stored XSS)
[UNSOLVED] Challenge 13 (Client-side XSS Protection)
[UNSOLVED] Challenge 14 (Confidential Document)
[UNSOLVED] Challenge 15 (DOM XSS)
[UNSOLVED] Challenge 16 (Database Schema)
[UNSOLVED] Challenge 17 (Deprecated Interface)
[UNSOLVED] Challenge 18 (Easter Egg)
[UNSOLVED] Challenge 19 (Email Leak)
[UNSOLVED] Challenge 20 (Ephemeral Accountant)
[UNSOLVED] Challenge 21 (Error Handling)
[UNSOLVED] Challenge 22 (Expired Coupon)
[UNSOLVED] Challenge 23 (Extra Language)
[UNSOLVED] Challenge 24 (Five-Star Feedback)
[UNSOLVED] Challenge 25 (Forged Coupon)
[UNSOLVED] Challenge 26 (Forged Feedback)
[UNSOLVED] Challenge 27 (Forged Review)
[UNSOLVED] Challenge 28 (Forged Signed JWT)
[UNSOLVED] Challenge 29 (Forgotten Developer Backup)
[UNSOLVED] Challenge 30 (Forgotten Sales Backup)
[UNSOLVED] Challenge 31 (Frontend Typosquatting)
[UNSOLVED] Challenge 32 (GDPR Data Erasure)
[UNSOLVED] Challenge 33 (GDPR Data Theft)
[UNSOLVED] Challenge 34 (HTTP-Header XSS)
[UNSOLVED] Challenge 35 (Imaginary Challenge)
[UNSOLVED] Challenge 36 (Leaked Access Logs)
[UNSOLVED] Challenge 37 (Leaked Unsafe Product)
[UNSOLVED] Challenge 38 (Legacy Typosquatting)
[UNSOLVED] Challenge 39 (Login Admin)
[UNSOLVED] Challenge 40 (Login Amy)
[UNSOLVED] Challenge 41 (Login Bender)
[UNSOLVED] Challenge 42 (Login Bjoern)
[UNSOLVED] Challenge 43 (Login CISO)
[UNSOLVED] Challenge 44 (Login Jim)
[UNSOLVED] Challenge 45 (Login MC SafeSearch)
[UNSOLVED] Challenge 46 (Login Support Team)
[UNSOLVED] Challenge 47 (Manipulate Basket)
[UNSOLVED] Challenge 48 (Misplaced Signature File)
[UNSOLVED] Challenge 49 (Multiple Likes)
[UNSOLVED] Challenge 50 (Nested Easter Egg)
[UNSOLVED] Challenge 51 (NoSQL DoS)
[UNSOLVED] Challenge 52 (NoSQL Exfiltration)
[UNSOLVED] Challenge 53 (NoSQL Manipulation)
[UNSOLVED] Challenge 54 (Outdated Whitelist)
[UNSOLVED] Challenge 55 (Password Strength)
[UNSOLVED] Challenge 56 (Payback Time)
[UNSOLVED] Challenge 57 (Premium Paywall)
[UNSOLVED] Challenge 58 (Privacy Policy)
[UNSOLVED] Challenge 59 (Privacy Policy Inspection)
[UNSOLVED] Challenge 60 (Product Tampering)
[UNSOLVED] Challenge 61 (Reflected XSS)
[UNSOLVED] Challenge 62 (Repetitive Registration)
[UNSOLVED] Challenge 63 (Reset Bender's Password)
[UNSOLVED] Challenge 64 (Reset Bjoern's Password)
[UNSOLVED] Challenge 65 (Reset Jim's Password)
[UNSOLVED] Challenge 66 (Reset Morty's Password)
[UNSOLVED] Challenge 67 (Retrieve Blueprint)
[UNSOLVED] Challenge 68 (SSRF)
[UNSOLVED] Challenge 69 (SSTi)
[UNSOLVED] Challenge 70 (Score Board)
[UNSOLVED] Challenge 71 (Security Policy)
[UNSOLVED] Challenge 72 (Server-side XSS Protection)
[UNSOLVED] Challenge 73 (Steganography)
[UNSOLVED] Challenge 74 (Successful RCE DoS)
[UNSOLVED] Challenge 75 (Supply Chain Attack)
[UNSOLVED] Challenge 76 (Two Factor Authentication)
[UNSOLVED] Challenge 77 (Unsigned JWT)
[UNSOLVED] Challenge 78 (Upload Size)
[UNSOLVED] Challenge 79 (Upload Type)
[UNSOLVED] Challenge 80 (User Credentials)
[UNSOLVED] Challenge 81 (Video XSS)
[UNSOLVED] Challenge 82 (View Basket)
[UNSOLVED] Challenge 83 (Vulnerable Library)
[UNSOLVED] Challenge 84 (Weird Crypto)
[UNSOLVED] Challenge 85 (Whitelist Bypass)
[UNSOLVED] Challenge 86 (XXE Data Access)
[UNSOLVED] Challenge 87 (XXE DoS)
[UNSOLVED] Challenge 88 (Zero Stars)

Summary: 0/88 challenges solved.

```
Example to "solve" a specific challenge (in this case challenge number 15):
```sh
$ ./juice-cheater http://127.0.0.1:3000/ -challenge 15

OWASP Juice Shop cheater 0.11 PoC
[OK] OWASP Juice Shop found at provided URL
[OK] Challenges found: 88

Trying to solve:
Id          : 15
Category    : XSS
Name        : DOM XSS
Description : Perform a <i>DOM</i> XSS attack with <code>&lt;iframe src="javascript:alert(`xss`)"&gt;</code>.
Status      : Solved
```
Example to "solve" all challenges at once:
```sh
$ ./juice-cheater -u http://127.0.0.1:3000/ -all

OWASP Juice Shop cheater 0.11 PoC
[OK] OWASP Juice Shop found at provided URL
[OK] Challenges found: 88

Trying to solve all challenges at once:
[SOLVED] Challenge 01 (API-only XSS)
[SOLVED] Challenge 02 (Access Log)
[SOLVED] Challenge 03 (Admin Registration)
[SOLVED] Challenge 04 (Admin Section)
[SOLVED] Challenge 05 (Arbitrary File Write)
[SOLVED] Challenge 06 (Bjoern's Favorite Pet)
[SOLVED] Challenge 07 (Blockchain Hype)
[SOLVED] Challenge 08 (Blocked RCE DoS)
[SOLVED] Challenge 09 (CAPTCHA Bypass)
[SOLVED] Challenge 10 (Change Bender's Password)
[SOLVED] Challenge 11 (Christmas Special)
[SOLVED] Challenge 12 (Classic Stored XSS)
[SOLVED] Challenge 13 (Client-side XSS Protection)
[SOLVED] Challenge 14 (Confidential Document)
[SOLVED] Challenge 15 (DOM XSS)
[SOLVED] Challenge 16 (Database Schema)
[SOLVED] Challenge 17 (Deprecated Interface)
[SOLVED] Challenge 18 (Easter Egg)
[SOLVED] Challenge 19 (Email Leak)
[SOLVED] Challenge 20 (Ephemeral Accountant)
[SOLVED] Challenge 21 (Error Handling)
[SOLVED] Challenge 22 (Expired Coupon)
[SOLVED] Challenge 23 (Extra Language)
[SOLVED] Challenge 24 (Five-Star Feedback)
[SOLVED] Challenge 25 (Forged Coupon)
[SOLVED] Challenge 26 (Forged Feedback)
[SOLVED] Challenge 27 (Forged Review)
[SOLVED] Challenge 28 (Forged Signed JWT)
[SOLVED] Challenge 29 (Forgotten Developer Backup)
[SOLVED] Challenge 30 (Forgotten Sales Backup)
[SOLVED] Challenge 31 (Frontend Typosquatting)
[SOLVED] Challenge 32 (GDPR Data Erasure)
[SOLVED] Challenge 33 (GDPR Data Theft)
[SOLVED] Challenge 34 (HTTP-Header XSS)
[SOLVED] Challenge 35 (Imaginary Challenge)
[SOLVED] Challenge 36 (Leaked Access Logs)
[SOLVED] Challenge 37 (Leaked Unsafe Product)
[SOLVED] Challenge 38 (Legacy Typosquatting)
[SOLVED] Challenge 39 (Login Admin)
[SOLVED] Challenge 40 (Login Amy)
[SOLVED] Challenge 41 (Login Bender)
[SOLVED] Challenge 42 (Login Bjoern)
[SOLVED] Challenge 43 (Login CISO)
[SOLVED] Challenge 44 (Login Jim)
[SOLVED] Challenge 45 (Login MC SafeSearch)
[SOLVED] Challenge 46 (Login Support Team)
[SOLVED] Challenge 47 (Manipulate Basket)
[SOLVED] Challenge 48 (Misplaced Signature File)
[SOLVED] Challenge 49 (Multiple Likes)
[SOLVED] Challenge 50 (Nested Easter Egg)
[SOLVED] Challenge 51 (NoSQL DoS)
[SOLVED] Challenge 52 (NoSQL Exfiltration)
[SOLVED] Challenge 53 (NoSQL Manipulation)
[SOLVED] Challenge 54 (Outdated Whitelist)
[SOLVED] Challenge 55 (Password Strength)
[SOLVED] Challenge 56 (Payback Time)
[SOLVED] Challenge 57 (Premium Paywall)
[SOLVED] Challenge 58 (Privacy Policy)
[SOLVED] Challenge 59 (Privacy Policy Inspection)
[SOLVED] Challenge 60 (Product Tampering)
[SOLVED] Challenge 61 (Reflected XSS)
[SOLVED] Challenge 62 (Repetitive Registration)
[SOLVED] Challenge 63 (Reset Bender's Password)
[SOLVED] Challenge 64 (Reset Bjoern's Password)
[SOLVED] Challenge 65 (Reset Jim's Password)
[SOLVED] Challenge 66 (Reset Morty's Password)
[SOLVED] Challenge 67 (Retrieve Blueprint)
[SOLVED] Challenge 68 (SSRF)
[SOLVED] Challenge 69 (SSTi)
[SOLVED] Challenge 70 (Score Board)
[SOLVED] Challenge 71 (Security Policy)
[SOLVED] Challenge 72 (Server-side XSS Protection)
[SOLVED] Challenge 73 (Steganography)
[SOLVED] Challenge 74 (Successful RCE DoS)
[SOLVED] Challenge 75 (Supply Chain Attack)
[SOLVED] Challenge 76 (Two Factor Authentication)
[SOLVED] Challenge 77 (Unsigned JWT)
[SOLVED] Challenge 78 (Upload Size)
[SOLVED] Challenge 79 (Upload Type)
[SOLVED] Challenge 80 (User Credentials)
[SOLVED] Challenge 81 (Video XSS)
[SOLVED] Challenge 82 (View Basket)
[SOLVED] Challenge 83 (Vulnerable Library)
[SOLVED] Challenge 84 (Weird Crypto)
[SOLVED] Challenge 85 (Whitelist Bypass)
[SOLVED] Challenge 86 (XXE Data Access)
[SOLVED] Challenge 87 (XXE DoS)
[SOLVED] Challenge 88 (Zero Stars)

Summary: 88/88 challenges solved.
```
