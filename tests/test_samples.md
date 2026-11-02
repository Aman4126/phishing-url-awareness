# Test Results Python version used: 3.13.15  |   Operating system: windows 11  |   Date:02/11/2026 
| # | Input | Expected result | Actual result | Pass/Fail |
|---|-------|-----------------|---------------|-----------|
| 1 | https://www.example.com/login | No listed warning signs | No listed warning signs found. This does NOT prove safety. | PASS |
| 2 | http://192.0.2.10/account | IP address + HTTP | Uses an IP address instead of a familiar domain. Uses HTTP. REVIEW CAREFULLY: 2 warning sign(s) found. | PASS |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | Contains an @ symbol; inspect carefully. Uses HTTP. REVIEW CAREFULLY: 2 warning sign(s) found. | PASS |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Contains many hostname segments/subdomains. REVIEW CAREFULLY: 1 warning sign(s) found. | PASS |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Contains a punycode-style hostname. REVIEW CAREFULLY: 1 warning sign(s) found. | PASS |

## Notes 
a link with no warning signs can still be dangerous, or that http://[bad crashed
the first version until I added try/except.]