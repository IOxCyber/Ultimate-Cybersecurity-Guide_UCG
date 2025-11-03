1. What is best agent based or IP based scan?
- It is based on the environment, for static IP & Network based devices we can choose IP based.
- & for Dynamic IP, Remote Devices, Endpoints etc.

2. How to set up/configure Scanner.
3. How to configure/set up QGS?

4. What port/services are required to perform scans in Windows/Linux?
- For Linux: SSH 22, Sudo user account
- For Win: SMBv2 445 enabled, Service Account, NTLM v2, WMI

5. Any experience withh Certificate Assessment?
6. How to identify the assets accross Client environments?
- with Manual asset inventory, Discovery scans

7. Use of External/Internal Scanner?
8. How to prioritise the findings?
- With help of QDS, Trurisk, Severity etc

9. What all modules you have experienced on?
- VMDR, SCA, Agent Module, WAS etc

10. What's the use of QGS(Qualys Gateway Service)?
- To store Cache findings before pushing it to Qualys UI
- To configure encryption, filter the data findings

11. How to handle exception for a vulnerability which can't be remediated & how we ensure that these vulnerabilities don't come in report?
- Handle the exception with RTP (Risk Treatment Plan), ARD(Acceptable Risk Data)
- To ensure the findings doesn't come in report, by excluding the QID & fetch the report only for included QIDs.

12. What's Zero Day & what we do as VM?
- Any vuln where the vendor isn't aware of the vulnerability and the patching is also not available.

13. How to troubleshoot the agent based scan issues?
- Asset is decom, Cred is correct, Agent is configured correctly, Port is open (22, 445,443 etc)
 
14. what encryption used when share data from Qualys agent to Qualys UI?
15. Auth and Unauth Scans?
- Auth is using credentials & Unauth 
16. Why IP based and Agent based scan findings are different?

17. What's false positives and False negative findings?