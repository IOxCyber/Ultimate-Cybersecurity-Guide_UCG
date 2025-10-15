## 1. Selenium Scripts: 
- Qualys Browser Recorder (QBR), to record your task like Excel Macros in Selenium Script Format which can be upload in "Selenium Scripts" of Crawling Settings.


## 2. Form Crawl Scope: 
- Determines the Form Uniquenes, if it's new or already discovered.

## 3. Enhanced Crawling:
-
 It improves the Crawling by making requests & crawl to each directory Recursively.
```
Eg. www.example.com/foo/boo/zoo

1st Request: www.example.com/foo/boo/zoo
2nd Request: www.example.com/foo/boo/
3rd Request: www.example.com/foo/

Whatever New Object will be discovered, will be added in the scan scope.
```

## 4. Smart scan:
- It's for Single Page Websites ie. used Ajax, AngularJS, Bootstrap framework. Page content gets updated without reloading the page by JS.

> QID 150148 "Ajax Links Crawled"


## 5. Progressive Scanning: "Scan Settings"
- `One scan performed in multiple stages, the findings are updated in stages with each scan.`

- Used where a scan typically exceed the amount of time of available within a scanning window.

eg.
Traditional Web App Scans (3 hrs)
Progressive Scan 1, Scan 2, Scan 3
Partial Results, Partial Results, Final Results
