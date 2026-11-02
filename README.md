# EWB Phishing URL Awareness Checker

## Overview
Phishing is a trick where fake links or messages try to make people share
passwords, card numbers or OTPs. This command-line Python tool reads the text of
a URL and points out a few visible warning signs. It never opens the URL.

## Features
- Detects an @ symbol in the URL
- Flags unusually long URLs (over 100 characters)
- Flags IP-address hostnames
- Flags many hostname segments (5 or more)
- Flags punycode-style hostnames (xn--)
- Flags the HTTP scheme
- Loop mode: check many URLs in one run, type q to quit
- "REVIEW CAREFULLY" summary with the number of warnings found
- Malformed input is handled instead of crashing

## Requirements
Python 3.10 or later. No extra packages.

## How to Run
Windows: python phishing_checker.py
Mac/Linux: python3 phishing_checker.py

## Example Output
```
Enter a sample URL (or type q to quit): http://192.0.2.10/account

Result:
- Uses an IP address instead of a familiar domain.
- Uses HTTP. HTTPS alone does not prove trust.

REVIEW CAREFULLY: 2 warning sign(s) found.
Never enter passwords from unexpected links.
```

## Testing
| # | Input | Expected | Actual | Result |
|---|-------|----------|--------|--------|
| 1 | https://www.example.com/login | No warning signs | No listed warning signs found | PASS |
| 2 | http://192.0.2.10/account | IP address + HTTP | IP address and HTTP flagged | PASS |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | @ symbol and HTTP flagged | PASS |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Many segments flagged | PASS |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Punycode flagged | PASS |

Full table: tests/test_samples.md

## Screenshots
![Sample run](screenshots/sample_run.png)
![Test results](screenshots/test_results.png)

## Improvements
1. **Loop with quit (A)** - [Write in your words: why you added it. Tested by
   entering several URLs in one run and typing q.]
2. **Malformed input handling (C)** - [Why: typing http://[bad raised a
   ValueError and stopped the program. Fix: a try/except around urlparse. Tested
   by typing http://[bad and re-running all five samples.]
3. **Review carefully summary (B)** - [Why, and how you tested it.]

## Limitations
This is an educational tool. It only reads URL text. It does not visit
URLs, scan for malware or prove that a URL is safe. No warning signs
found does NOT mean a URL is safe.

## Ethical Use
Use sample strings only. Do not collect credentials. Do not use this
project to deceive anyone or to test websites without permission.

## Author
[AMAN YADAV], [Ewb AI POWERED CYBERSECURITY INTERNSHIP], EWB Courses