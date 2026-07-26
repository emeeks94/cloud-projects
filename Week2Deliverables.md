Let's call the name of our company **Meridian** and run along with it

Meridian is a Coffee cafe portal built as a standard three-tier web application. The presentation tier is a CloudFront distribution and an ALB fronting web containers on ECS Fargate; the application tier is a separate Fargate service holding the business logic; and the data tier is a S3 bucket (for meridian-uploads) for customer receipts. This document lists every principal that touches the system, the role each one holds.

Principal            Roles held

meridian-web-task-role	>>>	Read non-secret config from SSM Parameter Store /meridian/web/*; write to its own CloudWatch log group. No S3, no database, no secrets.

meridian-app-task-role	>>> 	s3:PutObject to meridian-uploads/* only;  write logs. No Get/List/Delete on S3, no IAM read. 

meridian-ecs-exec-role	>>> 	Pull images from the two Meridian ECR repos and write container logs at launch. Holds no application-data permissions.

MeridianDeveloper	     >>>   Full access in the dev account; ViewOnly (read-only) in prod. Ships to prod through the pipeline, never by hand.

MeridianSecurityAuditor	>>>	SecurityAudit + ViewOnlyAccess to read IAM, CloudTrail and Config, with an explicit Deny on every mutating action. Read-only by construction.


Billing alerts were created at $5 and $10 with **aws budgets create-budget**; S3 data-event logging is enabled and a denied **PutObject** surfaces in CloudTrail well inside the two-minute target via aws **cloudtrail lookup-events** filtered on **AccessDenied**; and the test-repo credential leak was flagged by the secret scanner and “rotated” by moving CI/CD to OIDC, which removes the stored secret entirely rather than replacing it.

