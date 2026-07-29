# Lessons Learned

- A private EC2 instance can be managed securely using AWS Systems Manager.
- CloudFront requires a Default Root Object (`index.html`) when serving static sites.
- Security Groups should restrict backend access to only the Application Load Balancer.
- Lifecycle policies are an easy way to reduce long-term S3 storage costs.
- Separating frontend and backend simplifies scaling and improves security.
