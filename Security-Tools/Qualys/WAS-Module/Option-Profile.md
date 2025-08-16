## To Set Up a New Option Profile:
-  `Default: Initial WAS Option`
- Option Profile > New > Provide details.

1. Profile Details:
- Add tag & Name


2. Scan Parameter:
- Form Submission (Define Form Action URI & Form Field Names) - None, Post, Get, **Post & Get**
- Form Crawl Scope `(Max links to crawl i.e 8000)`
- User Agent (Browser Version/Header) - Can specify the Browser header
- Crawling Options: Enhanced Crawling, `SmartScan (for Single Page App)`
- Behaviour Settings: Set timeout, Errors to allowed
- Performance Settings: Scan Intensity (Lowest-1 > Low-2 > Medium-5 > High-7 > Max-10 (# of http Threads) `Start with Low`
- Bruteforcing Settings: Use custom List or System List (to check PWDs) - Increases Time to Scan
- Detection Scope: Specify the QIDs to scan (`Core`, based on a specific `Category`(eg. OWASP top 10, Apache related etc), `Custom Search List`, `XSS Power Mode`, or EVERYTHING)

3. Search Criteria:






















