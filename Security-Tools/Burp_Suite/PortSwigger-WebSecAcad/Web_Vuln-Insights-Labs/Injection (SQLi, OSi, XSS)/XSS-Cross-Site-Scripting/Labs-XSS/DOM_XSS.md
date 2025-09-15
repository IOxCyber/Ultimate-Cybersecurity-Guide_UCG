All Labs: https://portswigger.net/web-security/cross-site-scripting/dom-based

## Lab 1: [DOM XSS in document.write sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)
- Search for Any Random String > Inspect in Firefox (better) > Find the Searched String

![image](https://github.com/user-attachments/assets/1e9f6014-208e-4b8f-a1ce-db9fa2c1e7bf)

- Inspect the query > the Query is directly passing by Document.write() to DOM via <img> tag.
- Injection: `" onload="alert("qwerty")">` in search section
- <img src="/resources/images/tracker.gif?searchTerms=`" onload="alert("qwerty")">`
---
OR
---
- Injection: `">< svg onload="alert("qwerty")>` in search section
- <img src="/resources/images/tracker.gif?searchTerms=`">< svg onload="alert("qwerty")>`

## Lab 2: [DOM XSS in document.write sink using source location.search inside a select element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)
- Analyse the JS code, `source location.search` updating the DOM: ![image](https://github.com/user-attachments/assets/b66c8c00-f07b-416e-8d3c-5fab24d55c78)
- Insert the storedId random value in URL query & observe the DOM: ![image](https://github.com/user-attachments/assets/2d92d551-25ba-478b-a78d-8144a66e0b8e)
- Inserted value will show up in app functionality: ![image](https://github.com/user-attachments/assets/abfc1427-ffe8-4296-a333-f2b5fa5c65f8)
- Give storeId `"><script>alert(123)</script></select>` ![image](https://github.com/user-attachments/assets/8d729fdf-619d-46f7-8544-db9f982a5edc)
- The innerHTML sink doesn't accept script elements on any modern browser, nor will svg onload events fire.
- This means you will need to use alternative elements like `img or iframe` Event handlers such as onload and onerror can be used in conjunction with these elements.
- For example: `element.innerHTML='... <img src=1 onerror=alert(document.domain)> ...'`

## Lab 3: [DOM XSS in innerHTML sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)
- Check innerHTML, Analyse the JS code
- ![image](https://github.com/user-attachments/assets/dd879d32-3a94-481e-87ba-67adf72e6780)
- `<img src=1 onerror=alert(123)>` will the break the Search function.

# Lab 4: 
-  jQuery's attr() function can change the attributes of DOM elements.

# Lab 5: `Lab: Reflected XSS into HTML context with most tags and attributes blocked`
- Most Tags & attributes are filtered by the firewalls.
- Find out the which tag & attributes is not filtered, Capture the search request > send to Intruder > Start Attack with all tags, attributes as payload simple list.




