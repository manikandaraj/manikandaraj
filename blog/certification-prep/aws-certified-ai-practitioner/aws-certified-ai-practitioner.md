+++
title = "AWS Certification - AWS Certified AI Practitioner"
description = "Study Guide for AWS Certified AI Practitioner. 🚀"
summary = "Study Guide for AWS Certified AI Practitioner. 🚀"
date = '2025-09-30-T17:35:40-04:00'
lastmod = '2025-09-30T17:35:40-04:00'
keywords = []
tags = ['aws', 'certification', 'learning', 'guide']
categories = []
draft = false 
[params]
    author = 'Manikandaraj Srinivasan'
+++

# AWS Certified AI Practitioner (AIF-C01) - Complete Exam Prep

## EXAM QUICK FACTS
- **50 scored questions** + 15 unscored (65 total)
- **Passing score**: 700/1000
- **No penalty for guessing** - answer everything
- **Compensatory scoring** - don't need to pass each section, just overall

## EXAM DOMAINS & WEIGHTINGS

| Domain | Weight | Focus |
|--------|--------|-------|
| 1. Fundamentals of AI and ML | 20% | Basic concepts, use cases, ML lifecycle |
| 2. Fundamentals of Generative AI | 24% | GenAI concepts, capabilities, limitations |
| 3. Applications of Foundation Models | 28% | RAG, prompt engineering, fine-tuning |
| 4. Guidelines for Responsible AI | 14% | Bias, fairness, transparency |
| 5. Security, Compliance, Governance | 14% | IAM, encryption, compliance standards |

---

# PART 1: AWS SERVICES REFERENCE

## MACHINE LEARNING SERVICES (Core Focus)

### **Amazon Bedrock** ⭐ CRITICAL
**What it does**: Fully managed service for foundation models (FMs) via API
**Use cases**: 
- Build GenAI apps without managing infrastructure
- Access multiple FMs (Claude, Llama, Titan, etc.)
- RAG implementations
- Agents for multi-step tasks

**Key features**:
- Guardrails for content filtering
- Knowledge Bases for RAG
- Model customization (fine-tuning)
- Agents for orchestration

**When to use**: Any GenAI application, chatbots, content generation, summarization
**Pricing**: Token-based, pay per use

---

### **Amazon SageMaker** ⭐ CRITICAL
**What it does**: End-to-end ML platform for building, training, and deploying custom models
**Use cases**: Custom ML model development, training at scale, model deployment

**Key Components**:
- **SageMaker Studio**: IDE for ML
- **Data Wrangler**: Data preparation and feature engineering
- **Feature Store**: Centralized feature repository
- **Model Monitor**: Track model performance and drift
- **Clarify**: Detect bias in data and models
- **JumpStart**: Pre-trained models and solutions
- **Model Cards**: Documentation for model transparency

**When to use**: Need custom models, not just pre-trained APIs
**Advantages**: Full control, scalability, integrated tools
**Disadvantages**: Requires ML knowledge, more complex than managed AI services

---

### **Amazon Comprehend**
**What it does**: NLP service for text analysis
**Use cases**: Sentiment analysis, entity recognition, key phrase extraction, language detection, topic modeling
**When to use**: Analyzing customer feedback, document classification, content moderation
**No training needed**: Pre-trained models ready to use

---

### **Amazon Lex**
**What it does**: Build conversational interfaces (chatbots, voice bots)
**Use cases**: Customer service chatbots, IVR systems, virtual assistants
**Key feature**: Same technology as Alexa
**When to use**: Need conversational AI with intent recognition

---

### **Amazon Polly**
**What it does**: Text-to-speech service
**Use cases**: Voice assistants, accessibility features, content narration
**Key feature**: Multiple voices and languages, SSML support

---

### **Amazon Transcribe**
**What it does**: Speech-to-text service
**Use cases**: Transcribing meetings, subtitles, call center analytics
**Key features**: Real-time or batch, speaker identification, custom vocabulary

---

### **Amazon Translate**
**What it does**: Neural machine translation
**Use cases**: Multilingual websites, document translation, real-time translation
**Key feature**: Supports 75+ languages

---

### **Amazon Rekognition**
**What it does**: Computer vision service
**Use cases**:
- Image/video analysis
- Facial recognition
- Object/scene detection
- Content moderation
- Celebrity recognition
- Text in images (OCR)

**When to use**: Any image/video analysis task
**Privacy note**: Facial recognition has compliance considerations

---

### **Amazon Textract**
**What it does**: OCR + document analysis with understanding
**Use cases**: Extract text and data from scanned documents, forms, tables
**Difference from Rekognition**: Understands document structure, not just text

---

### **Amazon Personalize**
**What it does**: Recommendation engine service
**Use cases**: Product recommendations, personalized content, targeted marketing
**When to use**: Need Netflix-style recommendations

---

### **Amazon Fraud Detector**
**What it does**: Fraud detection using ML
**Use cases**: Online payment fraud, fake accounts, loyalty program abuse
**Key feature**: Pre-built fraud detection models

---

### **Amazon Kendra**
**What it does**: Intelligent search service powered by ML
**Use cases**: Enterprise search, knowledge management, document search
**Key feature**: Natural language queries, ranking by relevance

---

### **Amazon Augmented AI (A2I)**
**What it does**: Human review workflows for ML predictions
**Use cases**: Low-confidence predictions, content moderation, sensitive decisions
**When to use**: Need human-in-the-loop validation

---

### **Amazon Q**
**What it does**: GenAI-powered business assistant
**Use cases**: Answer business questions, code generation, summarization
**When to use**: Enterprise knowledge assistant, developer productivity

---

### **PartyRock**
**What it does**: Amazon Bedrock Playground - no-code app builder
**Use cases**: Rapid prototyping of GenAI apps, learning, experimentation
**When to use**: Testing ideas without coding

---

## STORAGE & DATABASE (For AI/ML)

### **Amazon S3**
**Role in AI/ML**: Primary data lake for training data, model storage, outputs
**Key features**: Scalable, durable, versioning, lifecycle policies
**Use with**: SageMaker, Bedrock, all ML services

---

### **Amazon S3 Glacier**
**Role in AI/ML**: Long-term archival of historical training data
**When to use**: Compliance, historical datasets not actively used

---

### **Vector Databases** ⭐ CRITICAL FOR RAG

#### **Amazon OpenSearch Service**
**Use case**: Vector search, RAG implementations, semantic search
**Key feature**: Built-in vector engine

#### **Amazon Aurora (PostgreSQL)**
**Use case**: Relational database with pgvector extension for embeddings
**When to use**: Need both traditional DB and vector search

#### **Amazon Neptune**
**Use case**: Graph database, can store embeddings
**When to use**: Relationship-based data with vector search

#### **Amazon DocumentDB**
**Use case**: MongoDB-compatible, can store embeddings
**When to use**: Document store with vector capabilities

#### **Amazon RDS for PostgreSQL**
**Use case**: Relational DB with pgvector for embeddings
**When to use**: Standard relational needs + vector search

---

## ANALYTICS SERVICES

### **AWS Glue**
**Role in AI/ML**: ETL service for data preparation
**Use cases**: Data cleaning, transformation, cataloging before ML

### **AWS Glue DataBrew**
**What it does**: Visual data preparation tool
**When to use**: Non-coders need to prep data

### **AWS Lake Formation**
**What it does**: Build and manage data lakes
**Role in AI/ML**: Centralized data governance for ML training data

### **Amazon EMR**
**What it does**: Big data processing (Hadoop, Spark)
**Role in AI/ML**: Large-scale data processing before ML

### **Amazon Redshift**
**What it does**: Data warehouse
**Role in AI/ML**: Analytics on structured data, feature engineering

### **Amazon QuickSight**
**What it does**: BI and visualization
**Role in AI/ML**: ML insights integration, visualize predictions

---

## SECURITY, IDENTITY & COMPLIANCE

### **AWS IAM**
**Role in AI/ML**: Access control for all AWS services
**Key concepts**: 
- Roles for services (SageMaker execution role)
- Policies for permissions
- Least privilege principle

---

### **AWS KMS**
**What it does**: Encryption key management
**Role in AI/ML**: Encrypt training data, models, outputs
**Key feature**: Encryption at rest and in transit

---

### **Amazon Macie**
**What it does**: Discover and protect sensitive data in S3
**Role in AI/ML**: Ensure training data doesn't contain PII/PHI
**When to use**: Data governance, compliance

---

### **AWS PrivateLink**
**What it does**: Private connectivity between VPCs and services
**Role in AI/ML**: Keep ML traffic off public internet
**When to use**: Security-sensitive AI applications

---

### **AWS Artifact**
**What it does**: Access compliance reports and agreements
**Role in AI/ML**: Prove compliance for AI systems
**Use case**: SOC, ISO, PCI reports

---

### **AWS Audit Manager**
**What it does**: Automate audit evidence collection
**Role in AI/ML**: Continuous compliance monitoring for AI systems

---

### **Amazon Inspector**
**What it does**: Automated security assessments
**Role in AI/ML**: Scan EC2/containers running ML workloads

---

### **AWS Secrets Manager**
**What it does**: Manage secrets (API keys, credentials)
**Role in AI/ML**: Store API keys for AI services, database credentials

---

## MANAGEMENT & GOVERNANCE

### **AWS CloudTrail**
**What it does**: Audit logs for all AWS API calls
**Role in AI/ML**: Track who accessed models, data, predictions
**Compliance**: Required for audit trails

---

### **Amazon CloudWatch**
**What it does**: Monitoring and logging
**Role in AI/ML**: 
- Monitor model endpoints
- Track inference latency
- Set alarms on metrics
- Log analysis

---

### **AWS Config**
**What it does**: Track resource configuration changes
**Role in AI/ML**: Compliance, governance over AI resources

---

### **AWS Trusted Advisor**
**What it does**: Best practice recommendations
**Role in AI/ML**: Cost optimization, security checks for ML resources

---

## COMPUTE & CONTAINERS

### **Amazon EC2**
**Role in AI/ML**: 
- Training infrastructure (GPU instances)
- Custom ML pipelines
- Self-managed deployments

**GPU Instances**: P4, P3, G5 for ML training/inference

---

### **Amazon ECS / EKS**
**Role in AI/ML**: 
- Deploy containerized ML models
- Microservices architecture for AI apps
- Orchestration at scale

---

## NETWORKING

### **Amazon VPC**
**Role in AI/ML**: Network isolation for ML workloads
**When to use**: Security-sensitive AI applications

---

### **Amazon CloudFront**
**Role in AI/ML**: 
- Distribute ML inference results globally
- Cache AI-generated content
- Low-latency delivery

---

## COST MANAGEMENT

### **AWS Budgets**
**Role in AI/ML**: Set budget alerts for ML training costs
**Critical**: ML training can be expensive

---

### **AWS Cost Explorer**
**What it does**: Analyze spending patterns
**Role in AI/ML**: Identify cost optimization opportunities for ML

---

# KEY AI/ML CONCEPTS

## Learning Types

### **Supervised Learning**
- **What**: Labeled training data (input → known output)
- **Use cases**: Classification, regression
- **Examples**: Spam detection, price prediction, image classification

### **Unsupervised Learning**
- **What**: Unlabeled data, find patterns
- **Use cases**: Clustering, anomaly detection
- **Examples**: Customer segmentation, outlier detection

### **Reinforcement Learning**
- **What**: Learn through trial and error, rewards/penalties
- **Use cases**: Game AI, robotics, optimization
- **Examples**: AlphaGo, autonomous vehicles

---

## ML Techniques

### **Classification**
- Predict discrete categories (spam/not spam, cat/dog)
- Metrics: Accuracy, Precision, Recall, F1 Score

### **Regression**
- Predict continuous values (price, temperature)
- Metrics: MSE, RMSE, R²

### **Clustering**
- Group similar items without labels
- Examples: K-means, hierarchical clustering

---

## Inference Types

### **Batch Inference**
- Process large datasets at once
- Not real-time
- Cost-effective for bulk predictions
- **Use case**: Daily report generation, bulk scoring

### **Real-time Inference**
- On-demand predictions
- Low latency
- More expensive
- **Use case**: Chatbots, fraud detection, recommendations

---

## Data Types

### **Structured**
- Tabular data (rows/columns)
- Examples: CSV, databases

### **Unstructured**
- No predefined format
- Examples: Text, images, video, audio

### **Time-series**
- Sequential data with timestamps
- Examples: Stock prices, sensor data

---

## Model Metrics

### **Accuracy**
- (Correct predictions) / (Total predictions)
- Simple but can be misleading with imbalanced data

### **Precision**
- Of predicted positives, how many are correct?
- High precision = few false positives

### **Recall (Sensitivity)**
- Of actual positives, how many did we find?
- High recall = few false negatives

### **F1 Score**
- Harmonic mean of precision and recall
- Balanced metric

### **AUC (Area Under ROC Curve)**
- Measures classifier performance
- 1.0 = perfect, 0.5 = random

---

## ML Pipeline Stages

1. **Data Collection**: Gather training data
2. **EDA (Exploratory Data Analysis)**: Understand data patterns
3. **Data Pre-processing**: Clean, normalize, handle missing values
4. **Feature Engineering**: Create meaningful features
5. **Model Training**: Train algorithm on data
6. **Hyperparameter Tuning**: Optimize model parameters
7. **Evaluation**: Test performance on validation set
8. **Deployment**: Put model in production
9. **Monitoring**: Track performance, detect drift
10. **Re-training**: Update model with new data

---

# GENERATIVE AI CONCEPTS ⭐ CRITICAL

## Foundation Model Basics

### **Tokens**
- Basic units of text (words, subwords, characters)
- **Why important**: Pricing and context limits based on tokens
- ~750 words = 1000 tokens (rough estimate)

### **Embeddings**
- Numerical representations of text/images
- Capture semantic meaning
- **Use in RAG**: Convert documents to vectors for search

### **Vectors**
- Lists of numbers representing embeddings
- Stored in vector databases
- Compared using distance metrics (cosine similarity)

### **Chunking**
- Breaking documents into smaller pieces
- **Why**: Manage context window limits
- **Best practice**: Overlap chunks for context

---

## Model Types

### **Large Language Models (LLMs)**
- Text generation, understanding
- Examples: Claude, GPT, Llama
- **Transformer-based**: Attention mechanism

### **Multi-modal Models**
- Handle multiple types of input/output (text, image, audio)
- Examples: Claude 3.5 (text + images), DALL-E

### **Diffusion Models**
- Generate images from noise iteratively
- Examples: Stable Diffusion, Midjourney

---

## Inference Parameters

### **Temperature** ⭐ CRITICAL
- **Range**: 0 to 1+
- **Low (0-0.3)**: Deterministic, focused, repetitive
- **Medium (0.5-0.7)**: Balanced creativity
- **High (0.8-1.0)**: Creative, random, diverse
- **Use low for**: Factual tasks, code, data extraction
- **Use high for**: Creative writing, brainstorming

### **Top-p (Nucleus Sampling)**
- Alternative to temperature
- Consider only tokens in top p probability mass
- **Example**: Top-p=0.9 means consider tokens that make up 90% probability

### **Max Tokens**
- Limit output length
- Controls cost and response size

---

## Retrieval Augmented Generation (RAG) ⭐ CRITICAL

### **What is RAG?**
Technique to ground LLM responses in external knowledge

### **How it works**:
1. User asks question
2. Convert question to embedding
3. Search vector database for relevant documents
4. Retrieve top-k most similar chunks
5. Include chunks in prompt context
6. LLM generates answer based on retrieved info

### **Benefits**:
- Up-to-date information (beyond training data)
- Reduces hallucinations
- Citations/sources
- No model retraining needed
- Domain-specific knowledge

### **Use cases**:
- Enterprise knowledge bases
- Customer support with product docs
- Legal/medical document Q&A

### **AWS Implementation**:
- **Amazon Bedrock Knowledge Bases**: Fully managed RAG
- Vector databases: OpenSearch, Aurora, RDS PostgreSQL

---

## Prompt Engineering ⭐ CRITICAL

### **Techniques**:

#### **Zero-shot**
- No examples, just instruction
- "Translate this to French: Hello"

#### **Single-shot / One-shot**
- One example provided
- "Translate to French. Example: Hello → Bonjour. Now: Goodbye"

#### **Few-shot**
- Multiple examples (2-10)
- Helps model understand pattern

#### **Chain-of-thought**
- Ask model to show reasoning steps
- "Let's think step by step"
- Better for complex problems

#### **Prompt Templates**
- Reusable structures
- Fill in variables
- Consistent formatting

### **Best Practices**:
- Be specific and clear
- Provide context
- Use delimiters (""", ```, etc.)
- Specify output format
- Include examples
- Use negative prompts (what NOT to do)
- Iterate and refine

### **Risks**:
- **Prompt injection**: Malicious instructions in user input
- **Jailbreaking**: Bypass safety guardrails
- **Poisoning**: Training data contamination
- **Hijacking**: Override original instructions

---

## Model Customization Approaches

### **Pre-training**
- Train from scratch
- **Cost**: Extremely expensive
- **Time**: Weeks to months
- **When**: Building foundational model
- **AWS**: Not typical for practitioners

### **Fine-tuning** ⭐
- Continue training on domain-specific data
- **Cost**: Moderate to high
- **Time**: Hours to days
- **When**: Need specialized model behavior
- **Methods**:
  - Full fine-tuning (all parameters)
  - PEFT (Parameter-Efficient Fine-Tuning)
  - RLHF (Reinforcement Learning from Human Feedback)
- **AWS**: Amazon Bedrock custom models, SageMaker

### **In-context Learning**
- Provide examples in the prompt
- **Cost**: Low (just inference)
- **Time**: Immediate
- **When**: Quick adaptation, few examples available
- **Example**: Few-shot prompting

### **RAG**
- Add external knowledge via retrieval
- **Cost**: Low to moderate
- **Time**: Hours to set up
- **When**: Need current info, many documents
- **AWS**: Bedrock Knowledge Bases

### **Cost Ranking** (low to high):
1. In-context learning
2. RAG
3. Fine-tuning
4. Pre-training

---

## Foundation Model Lifecycle

1. **Data Selection**: Choose training corpus
2. **Model Selection**: Pick base architecture
3. **Pre-training**: Train on massive datasets
4. **Fine-tuning**: Adapt to specific tasks
5. **Evaluation**: Test performance
6. **Deployment**: Serve via API
7. **Feedback**: Gather user feedback, iterate

---

## GenAI Advantages vs Disadvantages

### **Advantages**:
- Adaptability (handle varied tasks)
- Responsive (understand context)
- Simplicity (no model training needed)
- Rapid development
- Natural language interface

### **Disadvantages** ⭐ CRITICAL:
- **Hallucinations**: Generate false information confidently
- **Nondeterminism**: Same input → different outputs
- **Inaccuracy**: Not 100% reliable
- **Interpretability**: Hard to explain decisions
- **Cost**: Can be expensive at scale
- **Latency**: Slower than traditional models
- **Bias**: Reflect training data biases

---

# RESPONSIBLE AI ⭐ CRITICAL DOMAIN

## Key Principles

### **Fairness**
- Equal treatment across groups
- No discrimination

### **Bias**
- Systematic errors favoring certain groups
- **Types**: Selection bias, measurement bias, historical bias

### **Inclusivity**
- Consider diverse perspectives
- Represent all users

### **Robustness**
- Reliable under various conditions
- Handle edge cases

### **Safety**
- Prevent harm
- Content filtering

### **Veracity**
- Truthfulness
- Minimize hallucinations

### **Transparency**
- Explainable decisions
- Model documentation

---

## Detecting & Mitigating Bias

### **Detection Tools**:
- **SageMaker Clarify**: Detect bias in data and models
- **Model Monitor**: Track prediction drift
- **A2I**: Human review for fairness

### **Dataset Best Practices**:
- Balanced representation
- Diverse data sources
- Labeled by diverse annotators
- Regular audits
- Remove sensitive attributes where appropriate

### **Bias Effects**:
- **Overfitting**: Model too specific to training data
- **Underfitting**: Model too simple, misses patterns
- Demographic disparities in accuracy

---

## Transparency & Explainability

### **SageMaker Model Cards** ⭐
- Document model details
- Intended use
- Performance metrics
- Limitations
- Ethical considerations
- Training data info

### **Explainable AI**:
- Human-centered design
- Interpretable predictions
- Feature importance
- Decision trees (inherently explainable)

### **Tradeoffs**:
- More complex models → higher accuracy, less interpretability
- Simpler models → more interpretable, lower accuracy
- Balance based on use case risk

---

## Guardrails for Amazon Bedrock ⭐

### **What they do**:
- Filter harmful content
- Block topics
- Redact PII
- Enforce content policies

### **Use cases**:
- Prevent toxic outputs
- Compliance requirements
- Brand safety
- Child safety

---

## Legal & Ethical Risks

### **Intellectual Property**:
- Training on copyrighted data
- Generated content ownership
- Fair use questions

### **Bias Risks**:
- Discriminatory outputs
- Legal liability
- Loss of customer trust

### **Hallucinations**:
- Misinformation
- User harm
- Reputational damage

### **End User Risks**:
- Privacy violations
- Sensitive data exposure
- Malicious use

---

## Environmental Considerations

### **Sustainability**:
- Model training carbon footprint
- Energy-efficient model selection
- Right-sized infrastructure
- Consider smaller models when possible

---

# SECURITY, COMPLIANCE & GOVERNANCE

## Security Fundamentals

### **Shared Responsibility Model** ⭐
- **AWS responsibility**: Security OF the cloud
  - Physical infrastructure
  - Hardware
  - Managed service security
- **Customer responsibility**: Security IN the cloud
  - IAM configuration
  - Data encryption
  - Application security
  - Network configuration

---

## IAM Best Practices

### **Principle of Least Privilege**:
- Grant minimum permissions needed
- Use roles, not root account

### **Key Concepts**:
- **Roles**: For services (SageMaker execution role)
- **Policies**: Define permissions
- **Users**: Individual access
- **Groups**: Collections of users

### **For AI/ML**:
- SageMaker execution role needs S3, CloudWatch access
- Bedrock invocation permissions
- Separate dev/prod permissions

---

## Encryption

### **At Rest**:
- S3: Server-side encryption (SSE-S3, SSE-KMS)
- RDS/DynamoDB: Transparent encryption
- EBS volumes: Encrypted by default option

### **In Transit**:
- HTTPS/TLS for API calls
- VPC endpoints for private connectivity

### **Key Management (KMS)**:
- Customer managed keys (CMK)
- Automatic key rotation
- Audit with CloudTrail

---

## Data Governance

### **Data Lineage**:
- Track data origins and transformations
- SageMaker Model Cards
- AWS Lake Formation

### **Data Cataloging**:
- AWS Glue Data Catalog
- Metadata management
- Schema discovery

### **Data Lifecycle**:
- Retention policies
- Archival (S3 → Glacier)
- Deletion procedures

### **Residency**:
- Data stays in selected region
- Compliance requirements
- GDPR, data sovereignty

---

## Monitoring & Logging

### **CloudTrail** ⭐:
- Who did what, when
- API call history
- Compliance audits

### **CloudWatch**:
- Performance metrics
- Custom metrics
- Alarms and notifications

### **SageMaker Model Monitor**:
- Data quality
- Model quality
- Bias drift
- Feature attribution drift

---

## Compliance Standards ⭐

### **ISO**:
- ISO 27001: Information security
- ISO 27017: Cloud security
- ISO 27018: Cloud privacy

### **SOC**:
- SOC 1: Financial reporting controls
- SOC 2: Security, availability, confidentiality
- SOC 3: Public SOC 2 report

### **Other**:
- **HIPAA**: Healthcare data
- **PCI DSS**: Payment card data
- **GDPR**: European data protection
- **FedRAMP**: US government cloud
- **Algorithm accountability laws**: AI-specific regulations

---

## Governance Frameworks

### **Review Process**:
- Regular policy reviews
- Risk assessments
- Audit schedules
- Stakeholder sign-offs

### **Generative AI Security Scoping Matrix**:
- Risk assessment framework
- Security controls mapping

### **Team Training**:
- AI ethics training
- Security awareness
- Compliance requirements
- Incident response

---

## Threat Protection

### **Application Security**:
- Input validation
- Prompt injection prevention
- Rate limiting
- Authentication

### **Vulnerability Management**:
- Amazon Inspector (EC2, containers)
- Patch management
- Security scanning

### **Infrastructure Protection**:
- VPC isolation
- Security groups
- NACLs
- AWS WAF (web application firewall)

---

# QUICK REFERENCE: SERVICE COMPARISON

## When to Use What

### **Need GenAI Application?**
→ **Amazon Bedrock** (managed FMs)

### **Need Custom ML Model?**
→ **Amazon SageMaker** (full ML platform)

### **Need Pre-trained AI API?**
- Text analysis → **Comprehend**
- Image/video → **Rekognition**
- Speech-to-text → **Transcribe**
- Text-to-speech → **Polly**
- Translation → **Translate**
- Chatbot → **Lex**
- Document extraction → **Textract**
- Search → **Kendra**
- Recommendations → **Personalize**
- Fraud detection → **Fraud Detector**

### **Need Vector Database for RAG?**
- Best for scale → **OpenSearch Service**
- Already using PostgreSQL → **Aurora/RDS PostgreSQL**
- Graph relationships → **Neptune**
- MongoDB compatible → **DocumentDB**

---

# EXAM STRATEGIES

## Question Type Tips

### **Multiple Choice (1 correct)**:
1. Eliminate obviously wrong answers
2. Look for AWS-specific services
3. Choose managed service over self-managed

### **Multiple Response (2+ correct)**:
1. Each option is independent
2. Typical: 3 correct out of 5-6 options
3. Use elimination process

### **Ordering**:
1. Think ML pipeline stages
2. Data comes before training
3. Training before deployment

### **Case Study**:
1. Read scenario carefully once
2. Each question stands alone
3. Track important details

---

## Common Distractors

### **Watch for**:
- Out-of-scope services
- Services from wrong category
- Overly complex solutions
- Manual processes vs automation
- Non-existent AWS features

### **AWS Prefers**:
- Managed over self-managed
- Serverless over EC2
- Native integrations
- Automation over manual
- Scalable architectures

---

## Domain Focus Strategy

Prioritize study time based on weights:
1. **Applications of Foundation Models (28%)** - RAG, prompting, fine-tuning
2. **Fundamentals of Generative AI (24%)** - LLMs, concepts, Bedrock
3. **Fundamentals of AI and ML (20%)** - Basic ML, SageMaker, use cases
4. **Security & Governance (14%)** - IAM, encryption, compliance
5. **Responsible AI (14%)** - Bias, fairness, transparency

---

# CRITICAL EXAM CONCEPTS

## Must-Know Services (Appear Most)
1. Amazon Bedrock
2. Amazon SageMaker
3. RAG Architecture
4. IAM
5. S3
6. Vector Databases
7. Comprehend/Rekognition/Transcribe
8. SageMaker Clarify/Model Monitor

## Must-Know Concepts
1. Supervised vs Unsupervised Learning
2. RAG (how it works, when to use)
3. Prompt engineering techniques
4. Temperature parameter
5. Fine-tuning vs RAG vs Pre-training costs
6. Bias detection and mitigation
7. Shared responsibility model
8. Data encryption (at rest and in transit)
9. ML pipeline stages
10. Hallucinations and mitigation

---

**STATUS**: Part 1 Complete. Ready for questions/answers for Part 2.
