## To Set Up a New Option Profile:

- WAS > Configuration > Option Profile > New > Provide Profile Details, Scan Parameter, Search Criteria

### 1. Profile Details:
- Add tag & Name

### 2. Scan Parameter:
- Form Submission (Define Form Action URI & Form Field Names) - None(Sensitive Site), Post(Login related forms), Get(Append Data), **Post & Get (UAT/QA)**

- Form Crawl Scope - `Exclude ut for more efficient scans`
- Maximum Links to Crawl - `Max links to crawl is 8000`

- User Agent (Browser Version/Header) - to specify the Browser header.

- Request Parameter Set: `Help identify forms & other request param used by the application.`

- Document Type: `to ignore any Binary associated with your web application.`

> Crawling Options: Increases the scan time

- Enhanced Crawling: helps in crawling the links by slicing/chopping the URL further to find the hidden links. eg. www.example.com/Admin/#product will be sliced to find the URLs in www.example.com/Admin & www.example.com/ URLs

- SmartScan: Set the depth of the scan, the scanner will crawl the URL till 5th depth.
eg. www.example.org1/app2/teams3/members4/projects5


- Behaviour Settings: Set timeout, Errors to allowed

- Performance Settings: Scan Intensity (Lowest-1 > Low-2 > Medium-5 > High-7 > Max-10 (# of http Threads) `Start with Low`

- Bruteforcing Settings: Use custom List or System List (to check PWDs) - Increases Time to Scan

- Detection Scope: Specify the QIDs to scan (`Core`, based on a specific `Category`(eg. OWASP top 10, Apache related etc), `Custom Search List`, `XSS Power Mode`, or EVERYTHING)

### 3. Search Criteria:
- Detection Scope, Sensitive Content and keyword URL Search (specify keywords ie. string or regular expr to search for links containing these keywords)
