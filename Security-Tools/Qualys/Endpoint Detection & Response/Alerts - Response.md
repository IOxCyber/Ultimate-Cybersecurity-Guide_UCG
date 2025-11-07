# How to Set up Alerts for Incidents & Potential malicious events:

## Alerts (Way to inform) & Actions (What to do)

> Before creating an Alert, an Action needs to be created.

### To Create an Action::
- `EDR > Response > Actions` > New Action > Fill configuration details (Name, Description) > select action (Send Email via Qualys, Post to Slack, Teams, PagerDuty) > For Emails (Subject, Msg, Recipients)


### To Create an Alert::
- `EDR > Response > Rule Manager` > New Rule > Fill Configuration details (Name, Description, Rule Severity (Low, Mid, High) > Rule Query (what data points will trigger the alert) > Test Query > 
Trigger Criteria > Action Settings > Action > Enable Auto-remediation (Default Action: Kill Process, Quarantine File OR Quarantine Asset)

- Trigger Criteria: Single Match, Time Window Count (if 3 matches within 15 mins), Time Window Scheduled (Alert with all matches in a scheduled window from 9-5)


> Rule Query: indicator.severityscore:[5,6,7]