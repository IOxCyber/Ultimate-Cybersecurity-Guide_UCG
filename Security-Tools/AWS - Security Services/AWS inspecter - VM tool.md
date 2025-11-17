Amazon Inspector is an Amazon Web Services (AWS) security service that continuously assesses your workloads for vulnerabilities. It automatically scans the Amazon Elastic Compute Cloud (Amazon EC2) instances, container images and repositories residing in the Amazon Elastic Container Registry (Amazon ECR), and AWS Lambda functions in your AWS environment. After the assessment, it produces a detailed list of security findings that is organized by level of severity.


Integrate with AWS Security Hub and Amazon EventBridge to automate workflows, ticket routing, and remediation.

Amazon Inspector stores your active findings until it detects that they are remediated, deleted after 30 days if resolved. States (Active, Supressed(excluded as per matching criteria), Closed)

Support compliance requirements and best practices for the NIST Cybersecurity Framework (CSF), Payment Card Industry Data Security Standard (PCI DSS), and other regulations with Amazon Inspector scans. All our compliance-related information and reports can be found on AWS Artifact

Amazon Inspector is a Regional service. Config needs to be repeated for each regions.

Amazon ECR and Lambda function scanning do not require the use of an agent.

Amazon Inspector can provide CVE data for your EC2 instances only if the AWS Systems Manager Agent (SSM Agent) is installed and activated

An IAM user identity with administrator permissions in an AWS account can enable Amazon Inspector. 

> AWS Organizations is primarily designed to manage multiple AWS accounts. It provides features like consolidated billing, account management, and policy enforcement across AWS accounts.

To review the coverage: Inspecter > Settings > Account Management

To view findings: Inspecter > Findings > by vulnerability, account, instance, repo etc





