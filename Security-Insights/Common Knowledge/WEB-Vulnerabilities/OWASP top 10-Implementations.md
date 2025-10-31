
## 2. Cryptography Failure:
### Prevention:
- The Python `hashlib` library allows you to hash your passwords securely and apply a salt.

```
import os
import hashlib

# Step 1: Generate a random salt (32 bytes)
salt = os.urandom(32)

# Step 2: Take user input for password
psw = input("Enter password: ").encode()

# Step 3: Hash using PBKDF2-HMAC with SHA-256
secure_hash = hashlib.pbkdf2_hmac('sha256', psw, salt, 10000)

# Step 4: Display results
print(f"Salt (hex): {salt.hex()}")
print(f"Secure Hash (hex): {secure_hash.hex()}")
```



## 3. 