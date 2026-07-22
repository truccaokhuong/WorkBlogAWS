---
title: "Amazon Bedrock – Generative AI on AWS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

**Amazon Bedrock** is a fully managed service for building generative AI applications on AWS. Instead of provisioning GPU servers, installing frameworks, and deploying large language models, developers can access **foundation models (FMs)** through APIs. This approach shortens development time and allows teams to focus on application-specific business logic.

Bedrock provides access to model families from multiple providers, including Amazon Titan, Anthropic Claude, Meta Llama, Cohere, and Mistral AI. Applications can evaluate and select a suitable model for each use case without rebuilding the entire AI infrastructure.

![AI application architecture using Amazon Bedrock on AWS](/images/blog3/amazon-bedrock-ai-architecture.png)

### Main Components

| Component | Role |
| --- | --- |
| **Web/Mobile App** | Provides the interface through which users submit requests and receive results. |
| **Amazon API Gateway** | Accepts application requests, forwards them to the processing layer, and returns responses. |
| **AWS Lambda** | Validates input, applies business logic, constructs prompts, and invokes the selected model through Amazon Bedrock. |
| **Amazon Bedrock** | Provides APIs for accessing foundation models and generating content from prompts. |
| **Amazon S3** | Stores documents or unstructured data needed by the application. |
| **Amazon DynamoDB** | Stores application data, session state, or interaction history when required. |
| **Knowledge Bases for Amazon Bedrock** | Retrieves relevant information from data sources to add context for the model. |
| **Amazon CloudWatch** | Collects logs and metrics and supports alerting, performance monitoring, and troubleshooting. |

### Application Request Flow

A generative AI request moves through the system as follows:

1. The user enters a question or instruction in a website or mobile application.
2. Amazon API Gateway receives the request and forwards it to AWS Lambda.
3. Lambda validates the input, executes business logic, and constructs the prompt.
4. If additional context is required, Lambda or the Bedrock workflow retrieves documents from Amazon S3, data from DynamoDB, or relevant knowledge through a Knowledge Base.
5. Lambda invokes the foundation model selected by the application through Amazon Bedrock.
6. The model processes the prompt and returns its output to Lambda.
7. Lambda may format, validate, or store the output before responding.
8. API Gateway sends the final answer back to the user interface.

### Choosing a Foundation Model

Amazon Bedrock does not restrict an application to one model. Developers can compare foundation models according to response quality and reasoning capability, supported languages and content types, request latency, context-window size, usage cost, and task requirements such as question answering, summarization, content generation, or coding.

### Knowledge Bases and RAG

**Retrieval-Augmented Generation (RAG)** combines a foundation model's generation capability with information retrieved from private data sources. Knowledge Bases for Amazon Bedrock supports this workflow, enabling AI applications to use organizational documents rather than relying only on knowledge already available to the model.

### Monitoring with Amazon CloudWatch

Amazon CloudWatch provides observability for the system. Logs, metrics, and alerts from API Gateway, Lambda, and related components help administrators monitor traffic, latency, and errors, detect failed requests or unusual activity, and investigate causes and resolve incidents more quickly.

### Conclusion

Amazon Bedrock significantly reduces the infrastructure that teams must manage when developing generative AI applications. Combined with API Gateway, Lambda, S3, DynamoDB, Knowledge Bases, and CloudWatch, it can serve as the center of a modular AI architecture that is maintainable and scalable.
