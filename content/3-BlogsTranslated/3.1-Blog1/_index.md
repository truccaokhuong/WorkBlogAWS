---
title: "Blog 1 - Amazon Bedrock – Generative AI Service on AWS"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

Recently, I have been spending time learning about AI services on AWS, especially Amazon Bedrock. After reading AWS documentation and reviewing deployment examples, I found this to be a very useful service as it greatly simplifies the process of building AI applications.

The first thing that impressed me is that Amazon Bedrock does not require developers to set up or manage AI infrastructure themselves. Instead of having to prepare GPU servers, install frameworks, and deploy large language models (LLMs), AWS provides ready-to-use AI models from various providers on a single platform. Users simply send a prompt through the API to receive results from the AI model.

In my illustrated diagram, the processing flow of an AI application using Amazon Bedrock works as follows:

The user sends a request from a Website or Mobile App.
Amazon API Gateway receives the request and forwards it to AWS Lambda.
AWS Lambda handles business logic, validates input data, constructs an appropriate prompt, and sends it to Amazon Bedrock.
Amazon Bedrock selects the suitable AI model to process and generate a response.
If the application needs to retrieve data, Lambda can read documents from Amazon S3 or fetch data from Amazon DynamoDB before sending the prompt or after receiving results.
The final result is returned to the user through API Gateway.

One particularly interesting aspect is that Amazon Bedrock doesn't just support a single AI model — it integrates multiple Foundation Models from various providers such as Amazon Titan, Claude, Llama, Cohere, and Mistral AI. This allows developers to easily experiment with different models without making major architectural changes.

Additionally, Bedrock supports integration with Amazon Knowledge Bases to build applications using the RAG (Retrieval-Augmented Generation) pattern. Rather than relying solely on pre-trained knowledge, AI can retrieve additional documents from enterprise sources or Amazon S3 before generating responses. This leads to more accurate and up-to-date results, making it especially suitable for internal chatbots, document search assistants, or Q&A systems.

Another service that appears in the diagram is Amazon CloudWatch. This is not a data processing component but a monitoring service for the entire system. CloudWatch collects logs, metrics, and alerts from API Gateway, Lambda, Bedrock, S3, or DynamoDB to help administrators track performance, detect errors, and resolve issues more quickly.

Through this research, I've observed that AWS architecture is designed with component separation in mind. Each service fulfills a specific role, making the system easy to scale, maintain, and modify individual components without affecting the entire application. This is one of the reasons many enterprises choose AWS for deploying AI applications.

In the coming time, I will continue to research more deeply on topics such as:

Amazon Bedrock Agents.
Knowledge Bases and RAG patterns.
Prompt Engineering on AWS.
Integrating Bedrock with Lambda and API Gateway to build complete AI chatbots.
Comparing the effectiveness of Foundation Models such as Claude, Titan, and Llama in different practical scenarios.

I am still in the learning process, so this article mainly reflects what I have gathered and researched. If you have experience deploying Amazon Bedrock in real projects, I would greatly appreciate any feedback or sharing to help me learn more.
