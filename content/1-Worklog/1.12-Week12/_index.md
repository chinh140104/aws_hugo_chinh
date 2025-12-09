---
title: "Week 12 Worklog"
date: "2025-11-28"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Week 12 Objectives:

* Review and evaluate system performance after deployment on AWS.
* Optimize source code, Lambda functions, and DynamoDB database.
* Review basic authentication/authorization flows to avoid issues (no deep security work).
* Finalize the project summary report and prepare presentation materials.


### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                         | Start Date | End Date | Reference Materials |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | -------- | ------------------- |
| 2   | - Analyze CloudWatch logs <br> - Use X-Ray to identify bottlenecks and runtime errors                                                  | 24/11/2025 | 24/11/2025 |  |
| 3   | - Check backend performance (API response time / Cold Start) <br> - Perform light load testing to evaluate scalability                  | 25/11/2025 | 25/11/2025 |  |
| 4   | - Optimize .NET code: reduce package size, improve Lambda handlers <br> - Review DynamoDB queries and optimize GSI if necessary        | 26/11/2025 | 26/11/2025 |  |
| 5   | - Review basic authentication/authorization (no deep dive, only ensure stable functionality) <br> - Finalize architecture diagram & data flow description | 27/11/2025 | 27/11/2025 |  |
| 6   | - Consolidate worklogs from Week 10–12 into the final report <br> - Write evaluation, conclusion, strengths/weaknesses of the architecture <br> - Prepare presentation slides | 28/11/2025 | 28/11/2025 |  |


### Week 12 Achievements:

* Overview:
  * This week, I focused on reviewing the entire system deployed on AWS, evaluating real performance, and optimizing key components. After that, I completed the documentation and final project report.

* Theoretical knowledge acquired:
  * How to query and analyze runtime logs in CloudWatch.
  * Trace request flows with X-Ray to detect bottlenecks.
  * Performance optimization for Lambda (cold start, initialization improvements).
  * DynamoDB optimization using GSI/LSI and analyzing query access patterns.
  * Summary of Serverless architecture and evaluation of pros/cons.

* Practical work / Deliverables:
  * Analyzed runtime errors and performance metrics via CloudWatch & X-Ray.
  * Checked API response time and proposed cold-start improvements (if necessary).
  * Reduced Lambda package size and improved execution performance.
  * Optimized DynamoDB data model to reduce query latency.
  * Finalized AWS architecture diagram.
  * Completed the project summary report, including final evaluation and presentation slides.
