---
layout: doc
title: Backup and Recovery Management
date: 2019-09-08 8:14:30 +0600
tags: [Manage]
toc: true
---
# Overview
-	Automatic back-ups performed according to your predefined policies and configurations, resulting in more efficiency, improved security posture, and reduced capacity costs (through optimization of data storage).
-	Ability to protect and track resources – and their copies – across your clouds, through a single, easy-to-use tool, making it easy to maintain compliance and apply governance.
-	Ability to see, in real-time, when resources were backed up – and see immediately how much data is unprotected – through a single Compliance Dashboard.  Get notifications of all key events and issues.
-	Automatic discovery of resources and auto-assignment of them to backup policies. You can also automate pre- and post-activities with webhooks.
-	Automated control of retention policies and removal of obsolete back-ups, enabling you to save on capacity costs.

# Client Stories
- As a client CTO, I want to ensure all production workload are backedup regularly to provide the required RTO and RPO
- As a client CISO, I want to get a periodic reporting on the backup status and policy
- As a client CTO, I want a backup and recovery solution that supports the production business case
- As a client CTO, I want to restore workload during the time of cyber attack or other disaster

# Owning service team
IBM Hybrid Cloud Management’s Platform Engineering Services organization

# Prerequisites
-	No formal prerequisite, but it’s highly recommended that the service Design overall cloud platform should have been delivered prior to the delivery of this service

# Included services
- Backup only - PES Fundamental
- Backup and recovery design
- Resiliency testing
- backup and restore
- backup monitoring
- backup policy management






*See detailed [estimator tool](https://ibm.ent.box.com/file/934857700859?s=zz0w274ddi7kqa6kkhutkkgmtk6us2dl) for more guidance.*
# Pricing considerations:
-	MRC charge shown is for first year only
-	The cost drivers above reflect implementation of backup only; any recoveries from backups incur separate costs
-	The cost drivers above reflect the usage of IBM’s recommended tooling; any customer-specific tooling would incur additional charges
-	Pricing does not include the cost of storage for backups; that cost comes from the customer’s cloud provider



# Fulfillment process
1.	Determine scope of backups:
    -	VMs
    -	VM images
    -	Storage accounts/buckets
    -	Container images
    -	Databases
2.	Implement backup tooling, including Compliance Dashboard
3.	Implement backup schedule
4.	Implement backup policies
5.	Conduct resiliency testing
6.	Make any necessary adjustments based upon testing
7.	Perform ongoing monitoring of all backups within scope


# Indicative fulfillment time
-	Design of backup and recovery solution is approximately 2-4 weeks, depending upon complexity of customer’s total cloud estate
-	Implementation of solution likewise ranges from 2-4 weeks
-	Management of solution is ongoing


# Related services
-	Design overall cloud platform
-	Design cloud storage
-	Secure template development



# SOW Content

The IBM proposed solution utilizes AWS Backup to provide a comprehensive and cost-effective data protection and recovery solution. The solution will automate the backup and retention of SMT data across AWS services in the cloud, and will also allow for backup monitoring, providing necessary audit information.
Our solution includes a holistic backup and restore system that leverages replication and low-cost Cloud Object Storage. With this solution, a full data archive will exist within the production AWS Multi Zone Region (MZR) which is replicated to the DR MZR for quick recovery.
IBM’s solution provides a backup and archive service that complies, while in alignment with the best practices of cloud native modern infrastructure, as represented in the Table 1 below:

| Backup Rotation Time             | 	Requirement                                                                   |
|----------------------------------|--------------------------------------------------------------------------------|
 | Daily Differential / Incremental | 	Taken at least once over a seven (7) day period                               |
| Weekly Full	                     | Taken once every seven (7) days                                                |
 | Monthly Full                     | 	Taken on the first week or first full backup of the following month           |
| Yearly Full                      | 	Taken on the first week of the new calendar year,at the end of the work week  |


Based on the requirements, different data types would require different rotation types. The data types, along with the retention periods are described in Table 2: 


| System Tiers     | Backup                           | Retention  | 	Backup                                       | 	Retention                    |
|------------------|----------------------------------|------------|-----------------------------------------------|-------------------------------|
| Non-Production	  | Initial Full Daily Incremental	  | 35 Days    | 	Two (2) Full per week Archive logs:3x daily  | 	DB: 30 days Logs: 35 days    |
| Production	      | Initial Full Daily Incremental   | 	35 Days   | 	Two (2) Full per week Archive logs:3x daily  | 	DB: 30 days Logs: 35 days    |

# Delivery Phase
- Manage
