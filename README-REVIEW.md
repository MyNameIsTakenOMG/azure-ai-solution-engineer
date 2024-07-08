# AI-SOLUTION-REVIEW

## table of contents
 - [Get started with Azure AI Services](#get-started-with-azure-ai-services)
 - [Create computer vision solutions with Azure AI Vision](#create-computer-vision-solutions-with-azure-ai-vision)
 - [Develop natural language processing solutions with Azure AI Services](#develop-natural-language-processing-solutions-with-azure-ai-services)
 - [Implement knowledge mining with Azure AI Search](#implement-knowledge-mining-with-azure-ai-search)
 - [Develop solutions with Azure AI Document Intelligence](#develop-solutions-with-azure-ai-document-intelligence)
 - [Develop Generative AI solutions with Azure OpenAI Service](#develop-generative-ai-solutions-with-azure-openai-service)

## Get started with Azure AI Services

 - Prepare to develop AI solutions on Azure
   - Define artificial intelligence: AI as software that exhibits one or more human-like capabilities: `visual perception`,`text analysis and conversation`,`speech`,`decision making`
   - Understand AI-related terms:
     - **data science**: Data science is a discipline that focuses on the processing and analysis of data; applying statistical techniques to uncover and visualize relationships and patterns in the data, and defining experimental `models` that help explore those patterns.
     - **machine learning**: Machine learning is a subset of data science that deals with the training and validation of `predictive models`. Typically, a data scientist prepares the data and then uses it to train a model based on an algorithm that exploits the relationships between the `features` in the data to predict values for unknown `labels`.
     - **artificial intelligence**: Artificial intelligence usually (but not always) builds on machine learning to create software that emulates one or more characteristics of human intelligence.
   - Understand considerations for AI Engineers:
     - **model training and inferencing**: Many AI systems rely on predictive models that must be `trained` using sample data. The training process analyzes the data and determines relationships between the `features` in the data and the `label`. After the model has been trained, you can submit new data that includes known `feature` values and have the model predict the most likely `label`. Using the model to make predictions is referred to as `inferencing`. Many services and frameworks require the process of training a model using exsiting data before using ti to inference new values.
     - **probability and confidence scores**: A well-trained machine learning model can be accurate, but no predictive model is infallible. In most cases, predictions have an associated confidence score that reflects the probability on which the prediction is being made. Software developers should make use of confidence score values to evaluate predictions and apply appropriate thresholds to optimize application reliability and mitigate the risk of predictions that may be made based on marginal probabilities.
     - **responsible ai and ethics**: It's important for software engineers to consider the impact of their software on users, and society in general; including ethical considerations about its use. The human-like nature of AI solutions is a significant benefit in making applications user-friendly, but it can also lead users to place a great deal of trust in the application's ability to make correct decisions. The potential for harm to individuals or groups through incorrect predictions or misuse of AI capabilities is a major concern, and software engineers building AI-enabled solutions should apply due consideration to mitigate risks and ensure fairness, reliability, and adequate protection from harm or discrimination.
   - Understand considerations for responsible AI:
     - **fairness**: AI systems should treat all people fairly. (no bias based on gender, ethnicity or etc)
     - **reliability and safety**: AI systems should perform relibly and safely. Unreliability in these kinds of system can result in substantial risk to human life. As with any software, AI-based software application development must be subjected to rigorous testing and deployment management processes to ensure that they work as expected before release.
     - **privacy and security**: AI systems should be secure and respect privacy. Personal details must be kept private.
     - **inclusiveness**: AI systems should empower everyone and engage people regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.
     - **transparency**: AI systems should be understandable. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.
     - **accountability**: People should be accountable for AI systems. Although many AI systems seem to operate autonomously, ultimately it's the responsibility of the developers who trained and validated the models they use, and defined the logic that bases decisions on model predictions to ensure that the overall system meets responsibility requirements.
   - Understand capabilities of Azure Machine Learning: a cloud-based platform for running experiments at scale to train predictive models from data, and publish the trained models as services. Features:
     - **Automated machine learning**
     - **Azure Machine Learning designer**
     - **Data and compute management**
     - **Pipelines**
   - Understand capabilities of Azure AI Services:
     - **natural language processing**: text analysis, QnA, translation, speech...
     - **knowledge mining and document intelligence**: ai search, document intelligence, custom document intelligence, custom skills...
     - **computer vision**: image analysis, face, video analysis, OCR...
     - **decision support**: content moderation...
     - **generative ai**: azure openai, dall-e image generation
   - Understand capabilities of Azure OpenAI Service: Generative AI models depend on large language models (LLMs) based on the transformer architecture that evolved from years of machine learning progress. Generative AI models are often queried with natural language prompts, and return an impressively accurate response when prompted correctly. `Azure OpenAI Service` is an Azure AI service for deploying, utilizing, and fine-tuning models developed by OpenAI. 
   - Understand capabilities of Azure AI Search: Azure AI Search is an Applied AI Service that enables you to ingest and index data from various sources, and search the index to find, filter, and sort information extracted from the source data. In addition to basic text-based indexing, Azure AI Search enables you to define an `enrichment pipeline` that uses AI skills to enhance the index with insights derived from the source data. Not only does this AI enrichment produce a more useful search experience, the insights extracted by your enrichment pipeline can be persisted in a knowledge store for further analysis or integration into a data pipeline for a business intelligence solution.
 - Create and consume Azure AI services: Azure AI services includes a wide range of individual services across multiple categories: `language`,`speech`,`vision`,`decision`. Different services can work together as a solution for certain scenario, such as `Azure AI document intelligence`,`Azure AI immersive reader`,`Azure cognitive search`,`Azure openai`
   - Create Azure AI services resources in an Azure subscription
     - multi-service resource and single-service resource(separated endpoints)
     - Training and prediction resources: some services offer separate resources for model training and prediction.
   - Identify endpoints, keys, and locations required to consume an Azure AI services resource.
     - `endpoint`: http address through which the service can be accessed.
     - `subscription key`: a valid key that must be provided when accessing endpoints
     - `resource location`: when provisioning a resource in Azure, this resource is assigned to a location, whhich determines the Azure data certer.
   - Use a REST API and an SDK to consume Azure AI services.
 - Secure Azure AI services
   - Consider authentication for Azure AI services
     - `regenerate subscription keys` (two keys for each ai service)
     - `protect keys with azure key vault`: Azure key vault can securely store secrets(passwords or keys). Access to key vault is granted to `security principals` which are authenticated user identities using `Microsoft Entra ID`. A security principal can be assigned to an application to define a `managed identity` for the application.
     - `token-based authentication`: When using the REST interface, some AI services support (or even require) token-based authentication. In these cases, the subscription key is presented in an initial request to obtain an authentication token, which has a valid period of 10 minutes. Subsequent requests must present the token to validate that the caller has been authenticated. (when using sdk, obtaining and presenting tokens are handled by sdk)
     - `Microsoft Entra ID authentication`: can be used to grant access to specific `service principals` or `managed identities` for apps and services.
       - `authenticate using service principals`
         - create a custom subdomain
         - assign a role to a service principal for you app
       - `authenticate using managed identities`
         - `system-assigned managed identity`: one-to-one, deleted when service deleted
         - `user-assigned managed identity`: reusable identity
   - Manage network security for Azure AI services: by default, azure ai services are accessible from all networks. But we can go to `networking/firewalls and virtual networks` to enable network restrictions.
 - Monitor Azure AI services
   - Monitor Azure AI services costs: using `azure pricing calculator` to create a new `estimate` and select an azure ai service you want to use (can choose multiple services). To view costs for the ai services, go to subscription --> cost analysis tab and view only costs for certain service by adding filters.
   - Create alerts and view metrics for Azure AI services
     - create alerts: create `alert rules` to configure notifications and alerts for your resources based on events or metric thresholds. `scope`: the resource to monitor; `condition`: on which the alert is triggered(`signal type`: `activity log` or `metric`); `optional actions`: sending emails or running azure logic aap to address the issue; `alert rule details`: such as the name of the alert rule and resource group where it should be defined.
     - view metrics: can add multiple metrics to a chart and choose appropriate aggregations and chart types.
     - add metrics to a dashboard
   - Manage Azure AI services diagnostic logging
     - create resources for diagnostic log storage: you can use Azure Event Hub as a destination so that then forward the data to a custom telemetry solution or 3rd party solution. But in most cases, you can use `Azure log analytics`, or `Azure storage`. **note**: create these resources before configuring diagnostic logging for your services
     - Configure diagnostic settings: go to `Diagnotic settings`, and specify the `name`, `catogories` of log event data to be captured, `details` of the destinations to store the data.
     - View log data in Azure Log Analytics
 - Deploy Azure AI services in containers
   - Create containers for reuse: pull container images from a registry and deploy it to a container host.
   - Deploy to a container and secure a container: download a contain image for specific azure ai service api and deploy it to ACI, or AKS or a local docker server. the usage metrics will be sent to azure ai services resource to calculate the billing.
     - configuration: `apikey`, `billing`,`eula`
     - containers:
       - language containers
       - speech containers
       - vision containers
   - Consume Azure AI services from a container: no need to provide subcription key, but has to implement your own authentication solution and network security restrictions.

## Create computer vision solutions with Azure AI Vision

## Develop natural language processing solutions with Azure AI Services

## Implement knowledge mining with Azure AI Search

## Develop solutions with Azure AI Document Intelligence

## Develop Generative AI solutions with Azure OpenAI Service
