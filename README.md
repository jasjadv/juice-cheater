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

OWASP Juice Shop cheater 0.1 PoC
[OK] OWASP Juice Shop found at provided URL
[OK] Challenges found: 86
[UNSOLVED] Challenge 01 (Score Board)
[UNSOLVED] Challenge 02 (Email Leak)
[UNSOLVED] Challenge 03 (Error Handling)
[UNSOLVED] Challenge 04 (Forged Review)
[UNSOLVED] Challenge 05 (Login Admin)
[UNSOLVED] Challenge 06 (Login Jim)
[UNSOLVED] Challenge 07 (Login Bender)
[UNSOLVED] Challenge 08 (Password Strength)
[UNSOLVED] Challenge 09 (Five-Star Feedback)
[UNSOLVED] Challenge 10 (Forged Feedback)
[UNSOLVED] Challenge 11 (Redirects Tier 1)
[UNSOLVED] Challenge 12 (Redirects Tier 2)
[UNSOLVED] Challenge 13 (Basket Access Tier 1)
[UNSOLVED] Challenge 14 (Basket Access Tier 2)
[UNSOLVED] Challenge 15 (Payback Time)
[UNSOLVED] Challenge 16 (Confidential Document)
[UNSOLVED] Challenge 17 (Forgotten Developer Backup)
[UNSOLVED] Challenge 18 (Forgotten Sales Backup)
[UNSOLVED] Challenge 19 (Admin Section)
[UNSOLVED] Challenge 20 (Product Tampering)
[UNSOLVED] Challenge 21 (Vulnerable Library)
[UNSOLVED] Challenge 22 (Weird Crypto)
[UNSOLVED] Challenge 23 (Easter Egg Tier 1)
[UNSOLVED] Challenge 24 (Easter Egg Tier 2)
[UNSOLVED] Challenge 25 (Forged Coupon)
[UNSOLVED] Challenge 26 (Upload Size)
[UNSOLVED] Challenge 27 (Upload Type)
[UNSOLVED] Challenge 28 (Arbitrary File Write)
[UNSOLVED] Challenge 29 (Extra Language)
[UNSOLVED] Challenge 30 (CAPTCHA Bypass Tier 1)
[UNSOLVED] Challenge 31 (Zero Stars)
[UNSOLVED] Challenge 32 (Imaginary Challenge)
[UNSOLVED] Challenge 33 (Login Bjoern)
[UNSOLVED] Challenge 34 (Login CISO)
[UNSOLVED] Challenge 35 (Login Support Team)
[UNSOLVED] Challenge 36 (Login MC SafeSearch)
[UNSOLVED] Challenge 37 (Premium Paywall)
[UNSOLVED] Challenge 38 (Reset Jim's Password)
[UNSOLVED] Challenge 39 (Reset Bender's Password)
[UNSOLVED] Challenge 40 (Reset Morty's Password)
[UNSOLVED] Challenge 41 (Reset Bjoern's Password Tier 2)
[UNSOLVED] Challenge 42 (NoSQL Injection Tier 1)
[UNSOLVED] Challenge 43 (NoSQL Injection Tier 2)
[UNSOLVED] Challenge 44 (NoSQL Injection Tier 3)
[UNSOLVED] Challenge 45 (Retrieve Blueprint)
[UNSOLVED] Challenge 46 (Typosquatting Tier 1)
[UNSOLVED] Challenge 47 (Typosquatting Tier 2)
[UNSOLVED] Challenge 48 (JWT Issues Tier 1)
[UNSOLVED] Challenge 49 (JWT Issues Tier 2)
[UNSOLVED] Challenge 50 (Misplaced Signature File)
[UNSOLVED] Challenge 51 (Deprecated Interface)
[UNSOLVED] Challenge 52 (XXE Tier 1)
[UNSOLVED] Challenge 53 (XXE Tier 2)
[UNSOLVED] Challenge 54 (RCE Tier 1)
[UNSOLVED] Challenge 55 (RCE Tier 2)
[UNSOLVED] Challenge 56 (Blockchain Tier 1)
[UNSOLVED] Challenge 57 (Security Policy)
[UNSOLVED] Challenge 58 (Steganography Tier 1)
[UNSOLVED] Challenge 59 (Supply Chain Attack)
[UNSOLVED] Challenge 60 (Christmas Special)
[UNSOLVED] Challenge 61 (User Credentials)
[UNSOLVED] Challenge 62 (Admin Registration)
[UNSOLVED] Challenge 63 (XSS Tier 0)
[UNSOLVED] Challenge 64 (XSS Tier 1)
[UNSOLVED] Challenge 65 (XSS Tier 2)
[UNSOLVED] Challenge 66 (XSS Tier 3)
[UNSOLVED] Challenge 67 (XSS Tier 4)
[UNSOLVED] Challenge 68 (Change Bender's Password)
[UNSOLVED] Challenge 69 (XSS Tier 5)
[UNSOLVED] Challenge 70 (Multiple Likes)
[UNSOLVED] Challenge 71 (SSTi)
[UNSOLVED] Challenge 72 (SSRF)
[UNSOLVED] Challenge 73 (Login Amy)
[UNSOLVED] Challenge 74 (XSS Tier 1.5)
[UNSOLVED] Challenge 75 (Reset Bjoern's Password Tier 1)
[UNSOLVED] Challenge 76 (Access Log)
[UNSOLVED] Challenge 77 (DLP Failure Tier 1)
[UNSOLVED] Challenge 78 (DLP Failure Tier 2)
[UNSOLVED] Challenge 79 (XSS Tier 6)
[UNSOLVED] Challenge 80 (Two Factor Authentication)
[UNSOLVED] Challenge 81 (Expired Coupon)
[UNSOLVED] Challenge 82 (Privacy Policy Tier 1)
[UNSOLVED] Challenge 83 (Privacy Policy Tier 2)
[UNSOLVED] Challenge 84 (Repetitive Registration)
[UNSOLVED] Challenge 85 (GDPR Compliance Tier 2)
[UNSOLVED] Challenge 86 (GDPR Compliance Tier 1)

Summary: 0/86 challenges solved.
```
Example to "solve" a specific challenge (in this case challenge number 10):
```sh
$ ./juice-cheater http://127.0.0.1:3000/ -challenge 10

OWASP Juice Shop cheater 0.1 PoC
[OK] OWASP Juice Shop found at provided URL
[OK] Challenges found: 86

Trying to solve:
Id          : 10
Category    : Broken Access Control
Name        : Forged Feedback
Description : Post some feedback in another users name.
Solved      : True
```
Example to "solve" all challenges at once:
```sh
$ ./juice-cheater -u http://127.0.0.1:3000/ -all
```
