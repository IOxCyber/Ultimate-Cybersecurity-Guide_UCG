# Basic App Set Up::

## 1. Basic Information: `Define Web App Entry Point`
- Qualys > Web App Security > WAS > Web App > New > Add `URL` eg. `protocol://hostname:Port/PATH to Directory`
- Also can be used `FQDN or IP Address`
- <img width="425" height="101" alt="image" src="https://github.com/user-attachments/assets/71796be2-327a-404a-97a7-408241bdd934"/>
- Custom attributes (name/value) can be defined for your web app to easy filter out your web app.
- Apply Tags

## 2. Crawl Settings: [In details](https://github.com/IOxCyber/Ultimate-Cybersecurity-Guide_UCG/blob/main/Security-Tools/Qualys/WAS-Module/Crawl%20%26%20Detection%20Scope.md)
- `what level needs to be crawled/test in the site.`
### Crawl Links:
1. Do not use: Ignore Robot.txt file.
2. Crawl All links and directories: Crawl all links & directory regardless of any restriction on robot.txt
3. Do not crawl links and directories: Respect the robot.txt & avoids crawling any links or directories it blocks.

- Add Selenium Scripts: Use to crawl web applications that require dynamic interaction or JS rendering.

## 3. Default Scan Settings:
- Select Option Profile.
- Choose Scanners i.e External(Internet), Individual (Internal i.e Virtual/Physical), Tags(Scanner Pool)
- Cancel Scan Option: Set default time to cancel ❌ scan.
- Progressive Scanning: Scans performed in stages with each scan. (Only for VulnA)
- Proxy: record all of the requests made by scanner. 

## 4. Additional Config:
- Add `Auth Reports` to run scan as auth user.
- Header Injection, API Endpoints, Set up Exclution List (Global), Redudant Links etc.

> Run Discovery Scan before Vulnerability scan Always.
