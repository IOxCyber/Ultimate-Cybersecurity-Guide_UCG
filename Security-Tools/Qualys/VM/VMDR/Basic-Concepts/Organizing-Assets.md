## 1. Asset Groups: [I'm here](https://docs.qualys.com/en/vm/10.29.0.0/asset_groups/win_asset_group.htm) `VM > Asset > Asset Group > Define Config`
- `User-defined groupings of host assets (IP addresses).`
- You can group hosts by importance, location, ownership, device type, System Priority or Criticality, asset ownership, and geographical/network segregation.
- Only the hosts in the group can be scanned when you scan an asset group.
- Access Privileges: `Edit user > Add group` in User profile settings to scan.

### Scan by hostname: `DNS or NetBIOS`
- Must enable "Scan by hostname" in Qualys Subs.
- Scanner Appliance must config a DNS server to resolve the hostname to IPs.
  
### Add hostname to Asset Group:
- After "Scan by hostname" enabled: `VM > Assets > Asset Groups > New > Asset Group > DNS/NetBIOS > Add & Save`
- eg. DNS: FQDN (Fully Qualified Domain Name) `demo123.svg.qualys.com`


## 2. Asset Tagging: [I'm here](https://docs.qualys.com/en/vm/10.29.0.0/host_assets/tags_asset_tagging.htm) `AssetView > Tags > Tag Details > Define Config > Done` OR `VM > Asset Search > Create Tags`
- Another method for organizing and tracking the assets in your account. Asset tagging must be enabled for your account to create the tags.
- You can assign tags to your host assets, and can select when setting up a scan.
- Dynamic approach to ensure you include all hosts that match certain criteria, even if your network constantly changes as hosts are added and removed.

### Types:
1. Static (Manually add host assets): Parent One
eg. `AssetView > Tags > Tag Details > Tag Rule` For Static: No Dynamic Rule > Done

2. Dynamic (Host added by Asset Tag Rule Engine): Child Dynamically added to Parent Tag
eg. `AssetView > Tags > Tag Details > Tag Rule > Select Rules > S/w Installed > Regular Expr(*mysql*) > Re-evaluate rule on save > Ignore Case > Test Rule > Continue` 

> Verify: `To your account Setting > Setting in setup > Scroll down to "New data security model" > Asset tagging must be enabled` | If Not Enabled > A manager user can enable it for you.

## 3. Other Options:
- Domain: useful for `external-facing assets`, such as websites or other internet-facing services.
- Virtual Host: To manage and scan virtual `hosts that run multiple domains or services on a single physical server or IP address.`

## FAQs:
- Can we scan an asset group with a mix of external and internal IP addresses `NO`
- A scan is automatically `canceled after 4 hours if it remains in queued` status due to platform issues.
- Qualys Cloud Agent scan executes every four hours ie 240 mins.
- External scanning is always available using our cloud scanners set up around the globe at our Security Operations Centers (SOCs). `External from the Scanner Appliance menu`.
- Internal scanning uses scanner appliances placed inside your network. Choose the "Build my list" option to select one or more scanner appliances for your scan task.


