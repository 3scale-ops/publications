## General

- Use infrastructure as code
- Ensure every single resource is tagged
- Disable AWS services like GuardDuty or AWS Config if you are not using them
- Remove unused resources (that's obvious, but they tend to accumulate, and then no one knows if they are in use)
- Apply retention/lifecycle policies to S3 buckets for AWS services (CloudTrail, AWS Config, Billing Exports)

## AWS Billing

- Use alerts for billing thresholds (so you get notified and are aware of accumulated monthly costs)
- Review the cost explorer frequently to detect variations in usage patterns
- Use cost budgets, to learn about how are you expending and to easily detect cost increases (or savings)

## Elastic Cloud Compute

- Purchase saving plans for the base capacity of the platform
- Size instances properly to the sustained workload (track usage, downsize if possible)
- Use burstable instances when possible (for staging)
- Use spot instances when possible (for development)
- Avoid EBS overprovisioning (volumes are expandable after creation)
- Track EBS usage evolution (it shouldn't grow over time)
- Avoid creating resources via wizards, use infra as code

## Openshift / Kubernetes

- Ensure ephemeral resources are eventually deleted (like Tekton PVCs, target groups, temporary load balancers...)
- Take into account intra-cluster traffic on multi-az clusters
- Configure pod resources and limits

## RDS / ElastiCache

- Purchase instance reservation for the base capacity of the platform
- Size instances properly to the sustained workload (track usage, downsize if possible)
- Use burstable instances for non-production environments
- Disable high availability for development environments (is reasonable to use it in staging to test failover scenarios)

## S3 Storage optimization

- Use storage classes appropriately
- Be aware of each class's minimal billable duration
- Configure bucket-wide object retention policies, especially for backup buckets
- Configure bucket-wide object lifecycle policies
- Be aware of non-current object versions usage
- Use the S3 storage lens feature to learn about current usage
- Clean and archive unused buckets
