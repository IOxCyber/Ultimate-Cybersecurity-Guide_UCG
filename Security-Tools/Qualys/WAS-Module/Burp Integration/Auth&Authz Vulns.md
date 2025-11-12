## Point of Authentication Attack

- What: Attacks that target the login or identity verification step itself.
- Goal: Trick the system into thinking you are someone else (gain access).

### Examples:

1. Brute-forcing / Credential stuffing — guessing valid username–password pairs.


2. SQLi on login form — bypass login without valid creds.


3. Session fixation — hijack another user’s session at login.


4. 2FA bypass — manipulating token verification process.



> Think of it as: breaking the door lock before entering.


---

## Point of Authorization Attack

- What: Attacks after successful authentication — when a logged-in user tries to access something they’re not allowed to.
- Goal: Escalate privilege or access unauthorized resources.

-- Examples:

1. IDOR (Insecure Direct Object Reference) — Normal user accesses /admin/user/2 data.


2. Force browsing — Directly visiting /admin without being admin.


3. Privilege escalation — Changing a “role” parameter from user → admin.


4. Bypassing access control checks via predictable endpoints or weak logic.



> Think of it as: you’re inside the building, but now breaking into a locked office.


---

### Category	Phase	Goal	Example

- Authentication Attack	Before login	Gain unauthorized entry	SQLi in login form
- Authorization Attack	After login	Access restricted data	IDOR on /admin endpoint
