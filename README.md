 AWS Security Hardening & Event-Driven Alerts 
 Overview
This project implements AWS account security hardening and real-time security alerting using native AWS services.
It focuses on detecting high-risk account activity without requiring billing access or paid services.

Architecture
CloudTrail captures management events and delivers them to EventBridge.
EventBridge evaluates security rules and routes matching events to SNS.
SNS delivers alert notifications via email.

CloudTrail - EventBridge - SNS - Email

 Security Detections Implemented

 Root Account Usage
Detects any API activity performed using the AWS root account.
Root usage should be extremely rare and may indicate misconfiguration or compromise.
This alert was validated with a live trigger.

 Failed AWS Console Login Attempts
Detects failed AWS Management Console authentication attempts.
Useful for identifying brute-force or credential misuse attempts.
Events are delivered  by AWS.

IAM Permission and Configuration Changes
Detects non-read-only IAM API calls such as user, role, or policy modifications.
IAM changes represent a high risk of privilege escalation.
Monitoring relies on CloudTrail management events.

 Alerting
Alerts are delivered using Amazon SNS email subscriptions.
Each EventBridge rule uses a dedicated execution role with least privilege.
Input transformation is disabled to preserve full event context.

 Cost and Access
 Runs entirely on the AWS Free Tier
 No Billing or Cost Explorer access required
 No EC2, Lambda, or paid services

 Key Takeaways
 Event-driven security monitoring using native AWS services
 CloudTrail management events are delivered asynchronously
 IAM and authentication monitoring require real API write events

 Skills shown
 AWS account security hardening
 Event-driven monitoring
 IAM least privilege
 CloudTrail auditing
 Debugging AWS event pipelines
