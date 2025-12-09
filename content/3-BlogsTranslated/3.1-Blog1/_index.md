---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# How Uniphore Achieved 30% Cost Savings by Modernizing Windows Servers on AWS

**By Sornavel Perumal and Ismail Baig on June 19, 2025 in categories: [Amazon EC2](https://aws.amazon.com/blogs/storage/category/compute/amazon-ec2/), [Amazon Elastic File System (EFS)](https://aws.amazon.com/blogs/storage/category/storage/amazon-elastic-file-system-efs/), [Amazon Elastic Kubernetes Service](https://aws.amazon.com/blogs/storage/category/compute/amazon-kubernetes-service/), [Amazon Simple Storage Service (S3)](https://aws.amazon.com/blogs/storage/category/storage/amazon-simple-storage-services-s3/), [AWS Backup](https://aws.amazon.com/blogs/storage/category/storage/aws-backup/), [Customer](https://aws.amazon.com/blogs/storage/category/post-types/customer-solutions/)**

Uniphore is the first built-for-scale, AI-native company that brings AI to every part of the enterprise experience. Uniphore's enterprise-grade multimodal AI and data platform unifies all elements of voice, video, text, and data using Generative AI, Knowledge AI, Emotion AI, and workflow automation together as a trusted copilot. Uniphore operates one of its core enterprise applications on legacy Windows Server infrastructure, which faced scalability and performance challenges as the business grew. Increasing maintenance costs and security concerns related to end-of-support operating systems meant Uniphore needed to modernize their infrastructure while ensuring business continuity.

[Uniphore](https://www.uniphore.com/) successfully utilized Amazon Web Services (AWS) services to modernize their Windows workloads through containerization and cloud-native solutions. By using [Amazon Elastic Kubernetes Service (Amazon EKS)](https://aws.amazon.com/eks/) for containerization and [Amazon Elastic Compute Cloud (Amazon EC2)](https://aws.amazon.com/ec2/) for compute resources, combined with [Amazon Elastic File System (Amazon EFS)](https://aws.amazon.com/efs/) and [Amazon S3](https://aws.amazon.com/S3/) for storage, Uniphore achieved 30% cost savings while significantly improving their operational capabilities. They migrated from Windows on-premises infrastructure to Linux on AWS to optimize call center analytics workloads. They found that their core business requirements for training and fine-tuning large language models (LLMs) performed significantly better on Linux-based systems, allowing them to build a unified, high-performance ecosystem specifically designed for AI/ML operations.

In this article, we explore how Uniphore approached their modernization journey and share practical insights for organizations considering similar transformations. We present a practical approach to modernizing legacy Windows workloads through containerization, efficient data migration, and cloud-native services. Whether you're planning a similar transformation or evaluating modernization options, this real-world example shows how to overcome common migration challenges while achieving tangible business benefits like improved scalability, enhanced security, and reduced operational costs.

## **Business Challenges**

Uniphore's U-Assist platform was initially hosted on-premises on 50 physical Windows Server 2008 R2 servers. As the business rapidly expanded, these servers began experiencing significant load. Frequent storage capacity shortages led to application cache failures and operational disruptions. Data exceeding 60 TB coupled with aging hardware reaching its limits caused maintenance costs to rise while system performance declined.

These applications were not designed for scalability and lacked vendor support, making it increasingly difficult to meet growing business demands. Security was another significant concern, as the end-of-support status of Windows Server 2008 R2 meant no more security patches or compliance support. These challenges, combined with significant operational costs from frequent manual interventions, made it clear that modernization was necessary.

## **Deployed Solution**

### Uniphore implemented a comprehensive modernization strategy using AWS services across three main areas:

#### **1. Application Modernization**

The team modernized the application stack by rewriting Java-based services to become operating system-agnostic (OS-agnostic) and implementing containerization with Docker. This included refactoring Windows-specific dependencies, such as file system paths, while separating configuration for container compatibility. The containerized application was then deployed to Amazon EKS using Kubernetes, achieving true application portability and fault tolerance across cloud environments through auto-scaling, self-healing, and rolling updates.

#### **2. Custom Data Migration Solution**

Uniphore developed a custom migration solution using Type 2 hypervisor technology. This innovative approach enabled hosting the [AWS DataSync](https://aws.amazon.com/datasync/) agent and seamless integration with Windows-based storage. Using high-speed dedicated internet connections, data was efficiently transferred to Amazon EFS, ensuring improved reliability and availability.

#### **3. Cloud Infrastructure Setup**

The modern infrastructure uses Amazon EC2 and Amazon EKS for compute and container orchestration, with [Amazon Virtual Private Cloud (Amazon VPC)](https://aws.amazon.com/vpc/) providing secure network isolation. Storage needs are met through Amazon EFS and Amazon S3, while DataSync is used to transfer data from legacy servers to Amazon EFS, as illustrated in Figure 1.

Applications running on Amazon EKS process data retrieved from EFS, and the output is stored in Amazon S3. Processed data is backed up using [AWS Backup](https://aws.amazon.com/backup/).


![Uniphore Data Migration Architecture](/images/Blog1_image1.png)

*Figure 1: Uniphore's Data Migration Architecture with DataSync and AWS Services*

## **Technical Implementation**

To ensure a seamless and uninterrupted transition from legacy infrastructure to a modern cloud-native environment, Uniphore executed the migration in three structured phases. Each phase focused on minimizing risk, ensuring data integrity, and maintaining business continuity.

#### **Phase 1: Hypervisor and DataSync Agent Deployment**

The team began by setting up a Type 2 hypervisor (e.g., VMware Workstation or Hyper-V) on existing hardware to host the DataSync agent. This setup enabled secure connectivity between on-premises Windows Server hosts and the AWS environment.

Key actions in this phase included:

- Provisioning and configuring the hypervisor to run the DataSync agent in an isolated, stable environment.
- Optimizing the network layer with high-speed dedicated internet and VPN tunnels to maximize bandwidth and reduce latency.
- Validating connectivity between on-premises storage and Amazon EFS targets to ensure readiness for data transfer.

#### **Phase 2: Secure Data Migration and Validation**

With infrastructure ready, the team began migrating over 60 TB of structured and unstructured data. DataSync was used to orchestrate data transfers reliably with close monitoring.

To ensure data integrity and completeness:

- Transfers were performed incrementally, with checksum validation at both ends.
- Transfer tasks were monitored in real-time through [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) and DataSync metrics.
- Transfer performance was fine-tuned multiple times to optimize throughput, especially for large files and deep directory structures.
- A separate test environment on AWS was used to validate migrated data and application behavior before final cutover.

#### **Phase 3: Production Cutover and Application Deployment**

The final phase involved transitioning to production workloads hosted on AWS. The legacy Windows-based application stack was containerized using Docker and deployed to Amazon EKS, enabling flexible platform scaling and operation independent of the underlying operating system.

Key steps in this phase:

- The EKS cluster was configured with auto-scaling node groups using Amazon EC2, optimizing cost and performance.
- Amazon VPC was established with custom routing, Security Groups, and NACLs to ensure secure traffic flow between internal (east-west) and external (north-south) services.
- Application configuration and secrets were managed using [AWS Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) and AWS Secrets Manager.
- A/B testing and gradual traffic switching ensured zero-downtime deployment.
- Legacy systems were only decommissioned after thorough validation in the cloud environment.

## **Best Practices**

The following best practices were implemented:

- Infrastructure as Code (IaC) with Terraform: Infrastructure was provisioned with Terraform, enabling version-controlled, repeatable, and auditable deployments.
- CI/CD pipelines: GitLab pipelines were established for continuous integration and deployment (CI/CD), ensuring fast and secure updates to containerized services.
- Observability: [DATADOG](https://aws.amazon.com/codedeploy/product-integrations/datadog/) and CloudWatch were integrated for monitoring and alerting across the entire stack, including compute, storage, and network.
- Backup and Disaster Recovery: AWS Backup policies were applied to Amazon EFS and Amazon EC2 snapshots, with cross-[Region](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) replication for critical workloads.

## **Key Benefits**

The following six key benefits were achieved with this solution:

#### **1. Scalability and Performance**

Before modernization, Uniphore's physical servers had fixed resources, often leading to performance bottlenecks during peak periods.

After migration:

- Auto Scaling with Amazon EC2 and Amazon EKS enabled infrastructure to automatically scale up or down based on actual workload demand.
- This flexible scaling ensured high availability and stable performance, even during high-load periods or batch processing.
- Application latency was significantly reduced through optimized container orchestration and right-sized compute provisioning.

#### **2. Flexibility and Portability**

Legacy applications were previously tied to a specific Windows OS version (2008 R2), making upgrades or migration difficult.

After refactoring and containerization:

- Applications became OS-agnostic and independent of specific environments.
- Containerized services can now run on any Kubernetes-compatible platform, such as Amazon EKS, self-managed clusters, or even other cloud providers, ensuring vendor neutrality and mobility.
- Developers gained flexibility to test and deploy in isolated environments without dependency conflicts.

#### **3. Enhanced Security and Compliance**

Operating unsupported systems like Windows Server 2008 R2 posed serious security and compliance risks, such as:

- Lack of security patches.
- Incompatibility with modern compliance frameworks like SOC 2, HIPAA, or ISO 27001.

After migration:

- Use of Amazon VPC, [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/) roles, Security Groups, and Kubernetes RBAC improved access control and network segmentation.
- All workloads run on actively supported operating system versions and are protected by native AWS security tools like [Amazon Inspector](https://aws.amazon.com/inspector/), [AWS Config](https://aws.amazon.com/config/), and [AWS GuardDuty](https://aws.amazon.com/guardduty/).
- AWS Backup and multi-Availability Zone (AZ) architecture provide built-in disaster recovery and business continuity.

#### **4. Efficient Data Management**

Data growth velocity had exceeded on-premises infrastructure capabilities, leading to storage capacity issues and backup failures.

- Amazon EFS provides a fully managed NFS file system that automatically scales with data growth.
- Amazon S3 is used to store processed data, benefiting from high durability and lifecycle policies to move older data to cost-effective storage tiers like S3 Glacier.
- DataSync enabled fast and secure transfer of over 60 TB of data while ensuring integrity with checksum and retry mechanisms.

#### **5. Reduced Operational Costs**

Managing on-premises infrastructure incurred high operational costs, from manual patching and monitoring to capacity planning.

After migration:

- The team no longer worries about hardware maintenance, OS upgrades, or backup scripting.
- IaC with Terraform and automated CI/CD pipelines enabled more consistent, reliable infrastructure management and deployment.
- The engineering team can now focus on product innovation instead of infrastructure troubleshooting.

#### **6. Significant Cost Savings**

One of the most impactful outcomes of this initiative was a 30% reduction in total operational costs.

Cost savings were achieved through:

- Decommissioning legacy data center resources.
- Optimizing instance usage with EC2 Auto Scaling and Spot Instances.
- Right-sizing storage and compute resources.
- Containerization reducing resource costs, allowing multiple applications to run efficiently on fewer nodes.
- Ability to scale down unused resources during off-peak hours directly reducing monthly cloud bills.

## **Conclusion**

This article illustrates how enterprises can successfully modernize legacy Windows Server workloads using AWS services, through Uniphore's journey—from physical servers to containerized, cloud-native architecture.

Through careful planning and implementation of containerization, custom data migration solutions, and modern cloud infrastructure, organizations can achieve significant operational and cost benefits while maintaining business continuity.

Key takeaways from this modernization journey include:

- The importance of a phased migration approach to reduce risk and ensure data integrity.
- How containerization can transform legacy Windows applications into flexible, scalable workloads.
- Effective data migration strategies using AWS DataSync and custom solutions.
- Best practices for deploying security, monitoring, and disaster recovery in the cloud environment.

## **Learn More**

To begin your own modernization journey, please see the following resources:

- [https://aws.amazon.com/enterprise/modernization/](https://aws.amazon.com/enterprise/modernization/)
- [https://www.youtube.com/watch?v=iL5FJ_1vKik](https://www.youtube.com/watch?v=iL5FJ_1vKik)
- [https://www.youtube.com/watch?v=4rquMWa3qp0](https://www.youtube.com/watch?v=4rquMWa3qp0)

**TAGS:** [Amazon EKS](https://aws.amazon.com/blogs/storage/tag/amazon-eks/), [Amazon Elastic Compute Cloud (Amazon EC2)](https://aws.amazon.com/blogs/storage/tag/amazon-elastic-compute-cloud-amazon-ec2/), [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/blogs/storage/tag/amazon-simple-storage-service-amazon-s3/), [AWS Cloud Storage](https://aws.amazon.com/blogs/storage/tag/aws-cloud-storage/), [AWS DataSync](https://aws.amazon.com/blogs/storage/tag/aws-datasync/)

### **Sornavel Perumal**

![Sornavel Perumal](/images/Blog1_image2.png)

**Sornavel Perumal** is a Senior Technical Account Manager at AWS with over 20 years of experience. He helps customers build scalable and cost-optimized solutions with AWS. He is passionate about Analytics, Machine Learning, and GenAI, and always enjoys learning new things every day.

### **Ismail Baig**

![Ismail Baig](/images/Blog1_image3.png)

**Ismail Baig** is the Manager of DevOps and Cloud at Uniphore and an AWS Certified Solutions Architect professional. With over 12 years of experience, he specializes in solving complex infrastructure challenges for next-generation startups in Analytics, AI, ML, Big Data, and Digital Solutions.