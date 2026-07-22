---
title: "Amazon S3 Storage Classes and Selection Criteria"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Amazon Simple Storage Service (Amazon S3) is a highly scalable object storage service offering virtually unlimited capacity and data durability of up to **99.999999999% (11 nines)**. Rather than providing a single storage model, Amazon S3 offers multiple storage classes for different access frequencies, retrieval speeds, availability requirements, retention periods, and cost targets.

Choosing the appropriate storage class helps a system meet its data access requirements while optimizing its overall operating cost.

![Overview of Amazon S3 storage classes](/images/blog1/amazon-s3-storage-classes.png)

### Storage Class Overview

| Storage class | Key characteristics | Suitable use cases |
| --- | --- | --- |
| **S3 Standard** | Millisecond access, high availability, data stored across multiple AZs. Higher storage cost. | Websites, web/mobile apps, images, videos, frequently accessed docs. |
| **S3 Intelligent-Tiering** | Auto-moves objects between tiers per usage. Monitoring fee applies. | Enterprise data, project docs, content with changing access patterns. |
| **S3 Standard-IA** | Lower storage cost, fast retrieval, retrieval charges apply. Multi-AZ. | Backups, archives, standby data, docs accessed few times/year. |
| **S3 One Zone-IA** | Similar to Standard-IA but single AZ. Lower cost, lower resilience. | Re-creatable data, temp files, secondary backups. |
| **S3 Glacier Instant Retrieval** | Long-lived archive, millisecond retrieval. | Medical records, legal data, archived images, long-term media. |
| **S3 Glacier Flexible Retrieval** | Retrieval from minutes to hours. Balances cost and accessibility. | Periodic backups, business records, historical docs, audit data. |
| **S3 Glacier Deep Archive** | Lowest-cost class. Retrieval takes several hours. | Legal records, multi-year retention, regulatory archives. |

### Selection Criteria

**1. Access frequency** – Frequently used data suits **S3 Standard**. Unpredictable patterns benefit from **S3 Intelligent-Tiering**. Rarely accessed data fits **Standard-IA** or Glacier classes.

**2. Required retrieval time** – Immediate access needs millisecond-latency classes (Standard, Intelligent-Tiering, Glacier Instant Retrieval). Minutes-to-hours retrieval allows Glacier Flexible Retrieval or Deep Archive for greater savings.

**3. Total storage and retrieval cost** – Lower storage cost often means higher retrieval charges. Evaluate reads, retrieval volume, and object lifecycle together.

**4. Availability requirements** – Critical data should use multi-AZ classes (S3 Standard, Standard-IA). One Zone-IA only for re-creatable or risk-tolerant data.

**5. Retention period** – Short-lived data fits S3 Standard or Intelligent-Tiering. Multi-year retention suits Glacier Flexible Retrieval or Deep Archive.

### Conclusion

No single S3 storage class is optimal for every type of data. The right choice balances access frequency, recovery speed, availability, retention period, and total cost. S3 Lifecycle policies can transition objects from frequently accessed storage to colder tiers over time.
