# juice-cheater
OWASP Juice Shop (Cheat Module) - Why you shouldn't use the Juice Shop for CTF-events rewarding prizes.

# Introduction
OWASP Juice Shop is a very nice way to train security/hacking skills. However when using the shop in CTF-events be aware of the fact it is fairly simple to abuse the continue-code of the shop to fake any progress without figuring out a challenge at all. 

This python program will show you how to abuse the continue-code feature of the juice-shop. 

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
$ ./juice-cheater -u [urL] -[option]  
```
Where [url] is the address where the OWASP Juice Shop instance can be found and [option] is one of these choices:
  - check : run a test to see if the OWASP Juice Shop van be reached and the progress per challenge;
  - challenge [num]: "solve" a specific challenge given by the provided [num]
  - all: solve all challenges at once

#### Examples
Example to check to see if things work correctly and/or the current progress:
```sh
$ ./juice-cheater -u http://127.0.0.1:3000/ -check 
```
Example to "solve" a specific challenge (in this case challenge number 10):
```sh
$ ./juice-cheater -u http://127.0.0.1:3000/ -challenge 10
```
Example to "solve" all challenges at once:
```sh
$ ./juice-cheater -u http://127.0.0.1:3000/ -all
```
