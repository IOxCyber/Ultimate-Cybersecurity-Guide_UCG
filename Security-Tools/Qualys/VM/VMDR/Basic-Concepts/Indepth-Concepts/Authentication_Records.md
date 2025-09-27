# Authenticated Scan: Requires Creds to Scan the assets.

## Windows: `Username, Password, NTLM v1/v2 OR Kerberos, SMB Signing`
- If using Domain (Domain Name, Type), `Username, Password, NTLM v1/v2 OR Kerberos, SMB Signing`  (MS Network Security Auth Protocol)
- For local host authentication, NTLMv2 and NTLMv1 protocols are supported. NTLM is Challenge Based Auth Protocol.
- SMB Signing: protect the integrity of SMB communication between clients and servers by adding a digital signature to each SMB message.

## Linux: `Username, Password, Kerberos, Private Keys/Certificates`
- Linux: `Username, Password, Kerberos, Private Keys/Certificates` Root Delegation(for Elevated Privilege): Sudo, Pimsu, PowerBroker
- ![image](https://github.com/user-attachments/assets/e8da228b-414f-4d5b-91c5-b15760d8b343)
- Creds Required: For Vuln Scan: The account must be able to execute certain commands. `Compliance scans: superuser (root) privileges.`
- Target Type: define the non-shell-based target types in the SSH2 authentication record.
- `Kerberos is a network authentication protocol`, ticket based & designed to provide secure and encrypted authentication for your systems and services.
- ![image](https://github.com/user-attachments/assets/6f1a4270-593a-4075-8cdf-2a1d1df87f7d)

### Using private keys/certificates:
- Private Keys/Certificates: Multiple private keys and/or certificates for authentication can be used. Any combination of private keys (RSA, DSA, ECDSA, ED25519) and certificates (OpenSSH, X.509).
- The `user account must be added to all target hosts along with the public key`, which will be `appended to the “.ssh/authorized_keys2” file in the user’s home directory.`

### Root Delegation: for Elevated Privilege
- You can use multiple root delegation tools for authentication: Sudo, Pimsu and PowerBroker.
- There's an option to get password for root delegation from a vault you've configured.
- `For compliance scans, root level privileges are required.`
- For vulnerability scans, root level privileges are not required.

> # By default, Any one of these services is sufficient for authentication: 22 (SSH), 23 (telnet) and 513 (rlogin). 

- `Enable agentless tracking` to track the hosts in this record by host ID. During the scanning process, the service assigns a unique host ID to each target host.
- TACACS server support: Password based authentication to a TACACS server is supported. This server follows the SSH user authentication specification.
- The List of Commands that Qualys can execute during a Vuln scan [I'm here](https://qualys.my.site.com/discussions/s/article/000006220)
