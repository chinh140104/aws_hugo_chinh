---
title: "Event 3"
date: "2025-11-16"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Workshop Reflection Report: "AWS Cloud Mastery Series #2: DevOps on AWS"

### Purpose of the Event
- Provide a comprehensive understanding of DevOps culture, principles, and practices on the AWS platform.
- Guide participants in building complete CI/CD pipelines from source control to automated deployment.
- Introduce key Infrastructure as Code (IaC) tools on AWS and their practical applications.
- Equip participants with knowledge about containerization, observability, and best practices for stable system operations.

### Main Speakers / Instructors (Based on Program)
- **Mr. Đỗ Huy Thắng** – DevOps Lead, VNG (Core session on DevOps culture & practices)
- **Ms. Nguyễn Thị Thu Hà** – Sr. DevOps Engineer, AWS (Technical sessions on CI/CD & IaC)
- **Mr. Phạm Tuấn Anh** – Solutions Architect, AWS (Container & Observability sessions)

### Highlights & Key Learnings

#### 1. DevOps Culture & Principles
- **DevOps Mindset**: Not just tools, but a **collaborative culture** between Development and Operations to optimize the entire software delivery process.
- **Performance Measurement**: DORA metrics (Deployment Frequency, Lead Time, MTTR, Change Failure Rate) are **critical indicators** for assessing DevOps effectiveness.
- **Shift-Left Testing & Security**: Integrate testing and security early in the pipeline to **detect issues faster** and reduce remediation costs.

#### 2. CI/CD Pipeline on AWS: From Code to Production
- **AWS Developer Tools Suite**: Comprehensive toolset (CodeCommit, CodeBuild, CodeDeploy, CodePipeline) enabling **full automation** of the release process.
- **Deployment Strategies**: Deep understanding of **Blue/Green** (zero-downtime), **Canary** (risk reduction), and **Rolling Updates** for appropriate selection.
- **Practical Demo**: Building a complete pipeline from code commit, automated testing, to deployment on EC2/ECS, providing clear visualization of the workflow.

#### 3. Infrastructure as Code (IaC): Managing Infrastructure as Source Code
- **AWS CloudFormation**: Powerful "declarative" IaC tool using YAML/JSON templates to define and manage AWS resources.
- **AWS CDK (Cloud Development Kit)**: "Imperative" approach using familiar programming languages (Python, TypeScript) to define infrastructure, **enhancing reusability and maintainability**.
- **Drift Detection**: Mechanism to identify differences between code-defined configuration and actual infrastructure, ensuring **consistency and compliance**.

#### 4. Container Services & Microservices Architecture
- **Containerization with Docker**: Packaging applications into **lightweight, independent, and portable** containers, the foundation of microservices architecture.
- **Amazon ECS vs Amazon EKS**: Detailed comparison of AWS's top container orchestration services to **choose the right tool** for specific needs (fully-managed vs self-managed Kubernetes).
- **AWS App Runner**: "Serverless" solution simplifying container deployment, **minimizing infrastructure management** overhead.

#### 5. System Monitoring & Observability
- **Amazon CloudWatch**: Central hub for collecting metrics, logs, setting alarms, and dashboards to **monitor system health** in real-time.
- **AWS X-Ray**: Performance analysis and debugging tool for distributed applications by **tracing requests across services**.
- **Best Practices**: Setting meaningful alerts, SLO-focused dashboards, and incident response processes (on-call, postmortems).

### Key Takeaways

#### Mindset & Culture
- **DevOps is a journey, not a destination**: Requires continuous improvement based on data and feedback.
- **Automation is core**: Automate everything possible to **reduce manual errors** and free up time for creative work.
- **Failure is an option**: Build resilient systems and learn from incidents through blameless postmortems.

#### Technical & Tools
- **CI/CD is more than "running a pipeline"**: It's about creating a **reliable workflow** to deliver value to users quickly and safely.
- **IaC transforms infrastructure management**: Brings **consistency, version control, and environment reproducibility**.
- **Observability > Monitoring**: Not just alerting when things break, but **understanding root causes** through logs, metrics, and traces.

#### Career Skills
- **Need broad knowledge**: A DevOps Engineer requires understanding from networking, security, coding to system operations.
- **Problem-solving skills**: The ability to debug complex systems is invaluable.

### Personal Action Plan After the Workshop
1.  **Set up a personal CI/CD pipeline**: Use AWS CodeCommit & CodePipeline to automate deployment of a static web application or small API to AWS.
2.  **Get familiar with AWS CDK**: Choose a language (Python) and write CDK code to deploy basic AWS resources (VPC, EC2, S3).
3.  **Practice with Docker & ECS**: Containerize a simple application into a Docker image, push to Amazon ECR, and attempt deployment on ECS Fargate.
4.  **Build basic CloudWatch Dashboard**: For my demo application, set up simple metrics and alarms.

### Personal Experience at the Event

A full day from 8:30 AM to 5:00 PM focused on DevOps delivered an extremely valuable and practical wealth of knowledge. Compared to the AI/ML session, this workshop delved deeper into **operational processes and techniques** that developers like myself typically have less direct exposure to.

**The CI/CD pipeline and IaC demos were particularly impressive.** Witnessing how a single code commit triggered an entire automated sequence: build, test, security scan, then deployment with Blue/Green strategy, truly showcased the power of automation. It's not just fast but **significantly reduces risk**.

I also particularly enjoyed the sessions on **DevOps culture and case studies**. Hearing Mr. Thắng from VNG share how they applied DevOps to reduce MTTR from hours to minutes, or stories about startups failing due to neglecting monitoring, provided "priceless" lessons beyond textbooks.

The workshop concluded with the feeling of being **equipped with a more complete "mental toolkit."** I realized that to become a proficient software engineer, beyond writing good code, one must understand the entire software lifecycle—from idea and code to operations and learning from incidents.

#### Some photos from the event
![anh3 event](/images/4-Event/event-image3.png)
![anh4 event](/images/4-Event/event-image4.png)
