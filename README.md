TOTP Library Pure C for ALL MCU
====================

Library to generate Time-based One-Time Passwords.

Implements the Time-based One-Time Password algorithm specified in [RFC 6238](https://tools.ietf.org/html/rfc6238). 
Supports different time steps and it's compatible with tokens that uses the same standard (including software ones, like the Google Authenticator app).

Tesed with 16-bit MCUs (MSP430)

Installation & usage:
--------------------
First include header to your file
```
#include <totp.h>
```
After included, define key ex. Key is MyLegoDoor
```
uint8_t hmacKey[] = {0x4d, 0x79, 0x4c, 0x65, 0x67, 0x6f, 0x44, 0x6f, 0x6f, 0x72};               // Secret key
```
And this if you want to get code From timestamp
```
TOTP(hmacKey, 10, 30);                                     // Secret key, Key length, Timestep (30s)

setTimezone(9);                                            // Set timezone +9 Japan
uint32_t newCode = getCodeFromTimestamp(1557414000);       // Timestamp Now
```
Or this if you want to get code From struct tm (Time Struct in C), 
```
struct tm datetime;
datetime.tm_hour = 9;
datetime.tm_min = 0;
datetime.tm_sec = 0;
datetime.tm_mday = 13;
datetime.tm_mon = 5;
datetime.tm_year = 2019;
uint32_t newCode = getCodeFromTimeStruct(datetime);
```

You can see Example in blink.c

Thanks to:
----------

* Jose Damico, https://github.com/damico/ARDUINO-OATH-TOKEN
* Peter Knight, https://github.com/Cathedrow/Cryptosuite
* Maniacbug, https://github.com/maniacbug/Cryptosuite
* lucadentella, https://github.com/lucadentella/TOTP-Arduino
