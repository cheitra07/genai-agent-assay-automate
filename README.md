# genai-agent-assay-automate
clinical experient automation using aws bedrock nova

Scientist UI (Web / API)
        |
API Gateway
        |
Lambda (Agent Controller)
        |
Amazon Bedrock (Nova Agent)
        |
-------------------------------------------------
|   Tools invoked by Agent                      |
|                                               |
| 1. RAG Search (Embeddings + S3)                |
| 2. Protocol Parser                             |
| 3. Plate Setup Planner                         |
| 4. Reagent Validator                           |
| 5. Deviation Detector                          |
-------------------------------------------------
        |
Step Functions (Workflow + Approvals)
        |
DynamoDB (Audit Logs, Versions)
        |
SNS / Email (Scientist Approval)

| Capability    | AWS Service                                         |
| ------------- | --------------------------------------------------- |
| LLM Agent     | **Amazon Bedrock – Nova**                           |
| Embeddings    | **Bedrock Embeddings (Titan / Nova)**               |
| Vector Store  | **S3 + OpenSearch Serverless** *(or FAISS locally)* |
| Orchestration | **AWS Step Functions**                              |
| Compute       | **AWS Lambda (Python)**                             |
| API           | **API Gateway**                                     |
| Storage       | **S3 (Protocols, SOPs, Guidelines)**                |
| Audit Logs    | **DynamoDB**                                        |
| Approval      | **SNS / SES**                                       |
| IAM           | Fine-grained access                                 |
| Monitoring    | CloudWatch                                          |
genai-assay-agent/
│
├── README.md
├── architecture/
│   └── architecture-diagram.png
│
├── data/
│   └── sample_protocols/
│
├── lambdas/
│   ├── parse_protocol/
│   │   └── app.py
│   ├── plate_planner/
│   ├── reagent_validator/
│   ├── deviation_detector/
│   └── audit_logger/
│
├── agent/
│   └── nova_agent_config.json
│
├── step_functions/
│   └── assay_workflow.json
│
├── infra/
│   ├── iam.yaml
│   ├── s3.yaml
│   ├── lambda.yaml
│   └── step_functions.yaml
│
├── notebooks/
│   └── rag_testing.ipynb
│
└── .github/
    └── workflows/
        └── deploy.yml
