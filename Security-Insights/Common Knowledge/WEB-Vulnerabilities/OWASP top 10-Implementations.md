
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

### Secure Algorithms:
- SHA-1 (Secure Hash Algorithm-1), and the
SHA-2 family of hash algorithms: SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, and SHA-512/256.


## 3. 