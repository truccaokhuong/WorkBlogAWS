---
title: "Blog 3 - Survey of Amazon S3 Storage Classes and Selection Criteria"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

Amazon S3 (Simple Storage Service) is one of the most popular data storage services of Amazon Web Services (AWS), designed with virtually unlimited storage capacity, data durability of up to 99.999999999% (11 nines), and flexible scalability. Rather than offering a single storage form, Amazon S3 is divided into multiple Storage Classes to meet different needs regarding access frequency, performance, retention duration, and cost.

Choosing the right storage class not only ensures usage efficiency but also significantly optimizes operational costs. Each Storage Class is designed for a specific data group, from frequently accessed data to long-term archival data for backup or record-keeping purposes.

## Overview of Amazon S3 Storage Classes

Amazon S3 currently offers various storage classes, with the most common including:

- S3 Standard
- S3 Intelligent-Tiering
- S3 Standard-Infrequent Access (Standard-IA)
- S3 One Zone-Infrequent Access (One Zone-IA)
- S3 Glacier Instant Retrieval
- S3 Glacier Flexible Retrieval
- S3 Glacier Deep Archive

These storage classes are categorized by data access frequency, from "Hot Data" that is frequently used to "Cold Data" that is only retrieved in special circumstances.

## S3 Standard

S3 Standard is the default storage class of Amazon S3 and is suitable for frequently accessed data. This is the choice for applications requiring high performance, low latency, and high availability.

Use cases include: static websites, web applications, mobile applications, storage of continuously accessed images, videos, or documents.

The advantages of S3 Standard include millisecond access time, high availability, and data stored across multiple Availability Zones to enhance fault tolerance. However, the storage cost of this class is higher compared to other classes.

## S3 Intelligent-Tiering

S3 Intelligent-Tiering is designed for data with unpredictable or unstable access patterns. The standout feature of this storage class is the ability to automatically move data between storage tiers based on usage levels without user intervention.

If data is frequently accessed, the system maintains it at the high-performance tier. When data becomes less frequently used, Amazon S3 automatically moves it to a lower-cost tier to save budget.

This storage class is suitable for enterprise data lakes, project documents, and digital content with varying access frequency over time. Although there is an additional object monitoring fee, Intelligent-Tiering significantly reduces storage costs for systems with large data volumes.

## S3 Standard-Infrequent Access (Standard-IA)

Standard-IA is designed for data that is infrequently accessed but still requires fast retrieval when needed. Compared to S3 Standard, Standard-IA storage costs are lower; however, users pay an additional fee each time data is retrieved.

Use cases include: data backup, archival records, backup data, and documents accessed only a few times per year. This storage class still ensures data durability equivalent to S3 Standard and data is stored across multiple Availability Zones.

## S3 One Zone-Infrequent Access

One Zone-IA has similar characteristics to Standard-IA but data is stored in only a single Availability Zone. Since there is no data replication mechanism across multiple Availability Zones, storage costs are lower. However, if the Availability Zone experiences a severe failure, data may become unrecoverable.

One Zone-IA is suitable for reproducible data, temporary files, secondary backup data, and content that does not require high availability. This is a reasonable choice when businesses want cost savings and can accept higher risk levels.

## S3 Glacier Instant Retrieval

Glacier Instant Retrieval is for long-term archive data that still needs immediate retrieval when needed. Unlike traditional Glacier classes, retrieval time for Glacier Instant Retrieval is measured in milliseconds, while storage costs are lower than S3 Standard-IA.

This storage class is commonly used for medical records, archived images, multimedia content, and legal data requiring long-term retention.

## S3 Glacier Flexible Retrieval

Glacier Flexible Retrieval targets long-term archive data that does not require frequent access. Users can choose from various retrieval time options, from minutes to hours, depending on needs and desired cost levels.

Common applications include: enterprise record storage, periodic data backup, historical document storage, and audit data. This is a storage class that balances cost and retrieval capability.

## S3 Glacier Deep Archive

Glacier Deep Archive is the lowest-cost storage class in Amazon S3, designed for data that needs to be retained for very long periods and is almost never accessed. Retrieval time can extend to several hours, so this storage class is not suitable for frequently used data.

Use cases include: legal record storage, multi-year data archives, regulatory compliance documents for businesses or government agencies, and long-term backup. This is the appropriate solution when the primary goal is to minimize storage costs.

## Selection Criteria for Choosing the Right Storage Class

Choosing a Storage Class should not be based on cost alone but should consider multiple factors simultaneously.

### Data Access Frequency

This is the most important factor. Frequently accessed data should use S3 Standard or Intelligent-Tiering. For data accessed only a few times per month or per year, Standard-IA or Glacier are more suitable choices.

### Required Data Retrieval Time

If the application requires immediate retrieval, choose classes with millisecond response times such as Standard, Intelligent-Tiering, or Glacier Instant Retrieval. For data that can wait minutes or hours, Glacier Flexible Retrieval or Glacier Deep Archive will significantly save costs.

### Storage Costs and Retrieval Costs

Typically, the lower the storage cost, the higher the retrieval cost. Therefore, consider the trade-off between the number of data accesses and the total cost throughout the data lifecycle.

### Availability Requirements

If data is critical and requires high availability, prioritize storage classes deployed across multiple Availability Zones such as Standard or Standard-IA. In cases where data is reproducible or not critical, One Zone-IA will help reduce costs.

### Data Retention Duration

Short-term data is usually suitable for Standard or Intelligent-Tiering. Conversely, data that needs to be retained for many years but rarely accessed should use Glacier Flexible Retrieval or Glacier Deep Archive to optimize the budget.

The fact that Amazon S3 offers multiple storage classes shows that AWS does not aim for a one-size-fits-all solution but allows users to choose the approach appropriate for each specific need. Understanding the characteristics of each Storage Class helps build a more effective storage strategy, both ensuring data access capability when needed and optimizing system operational costs on the AWS platform.
