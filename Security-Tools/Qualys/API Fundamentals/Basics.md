1. QUALYS API:
- Use to automate activities, Asset Importing, Data Exporting and Integration with external tools.

2. Concepts & Terms:
- Web Flow: Client App <> API CALL (html request) <> API URL <> QUALYS Cloud Platform.

### API URL: FQDN of Qualys API server.
### API Endpoint: Path which provides access to the resource or operation.

eg. Scheme_Protocol://FQDN_API_SERVER/API_ENDPOINT
    HTTP://<API SERVER URL>/API ENDPOINT

3. Request Methods:
Get (to get the data from the server)
Post (to update/send the data to server)

4. Examples Of Working API: (Auth Required)
- Request Method,API URL (Scheme_Protocol://FQDN_API_SERVER/API_ENDPOINT)

- eg. To list out all Users in Qualys:
Post,https://qualysapi.qg3.apps.qualys.com/msp/user_list.php

5. Supported API AUTHENTICATION Method:
- API Client Call <> http Request (API request Basic Auth) <> API Service
## 2 Types:
- Basic http (Creds included in each request)
- Session-Based (Using Qualys Session Resource, a user can login & the API will use the same session cookies to make API calls)

6. Supported API Versions:
- API Version 1 & 2
- Recommended is API v2 as it supports both types of Auth Methods.
> X-Requested-With needs to be send with each HTTP headers in Http Request.








