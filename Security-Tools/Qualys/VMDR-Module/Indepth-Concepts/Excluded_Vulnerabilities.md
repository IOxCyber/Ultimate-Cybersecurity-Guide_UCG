# Excluded Vulnerabilities

These are categories of vulnerabilities that you might want to exclude from the vulnerability results shown in the interface. Here’s what each option means:

## Information
- **What it is:**  
  Vulnerabilities classified as "Information" typically don't represent a direct threat but provide additional details about the system, such as software versions or configuration settings.
- **Why to exclude:**  
  You might exclude these to focus only on more critical vulnerabilities that require action.
- **Example:**  
  A report on the presence of a specific software version without any associated risk.

## Fixed
- **What it is:**  
  These are vulnerabilities that were previously detected but have since been resolved or remediated.
- **Why to exclude:**  
  Excluding fixed vulnerabilities allows you to concentrate on those that still require attention.
- **Example:**  
  A vulnerability in a web server that was patched in the latest software update.

## Disabled
- **What it is:**  
  Vulnerabilities that have been manually disabled or marked as irrelevant or not applicable.
- **Why to exclude:**  
  To prevent clutter from vulnerabilities that have been deemed irrelevant for your specific environment.
- **Example:**  
  A known vulnerability in a service that has been disabled or uninstalled on the asset.

## Ignored
- **What it is:**  
  These are vulnerabilities that have been manually ignored or marked as accepted risks.
- **Why to exclude:**  
  Ignored vulnerabilities are typically those that have been acknowledged but aren't going to be fixed for various reasons, such as business decisions.
- **Example:**  
  An outdated protocol that is still required for legacy systems and cannot be disabled.

## Non-Running Kernel
- **What it is:**  
  This option filters out vulnerabilities related to kernels that are no longer in use (for example, after a system reboot with an updated kernel).
- **Why to exclude:**  
  To focus on vulnerabilities affecting the currently running kernel, rather than old, non-running ones.
- **Example:**  
  A vulnerability in an old Linux kernel version that is no longer active after an update.
