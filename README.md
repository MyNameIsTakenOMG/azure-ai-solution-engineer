# azure-ai-solution-engineer
## Contents of table
 - [Prepare to develop AI solutions on Azure](#prepare-to-develop-ai-solutions-on-azure)
 - [Create and consume Azure AI Services](#create-and-consume-azure-ai-services)
 - [Secure Azure AI Services](#secure-azure-ai-services)
 - [Monitor Azure AI Services](#monitor-azure-ai-services)
 - [Deploy Azure AI services in containers](#deploy-azure-ai-services-in-containers)
 - [Extract insights from text with the Azure AI Language service](#extract-insights-from-text-with-the-azure-ai-language-service)  
 - [Translate text with Azure AI Translator service](#translate-text-with-azure-ai-translator-service)
 - [Create speech enabled apps with Azure AI services](#create-speech-enabled-apps-with-azure-ai-services)
 - [Translate speech with the Azure AI Speech service](#translate-speech-with-the-azure-ai-speech-service)
 - [Build a question answering solution](#build-a-question-answering-solution)
 - [Create a bot with the Bot Framework SDK](#create-a-bot-with-the-bot-framework-sdk)
 - [Create a Bot with the Bot Framework Composer](#create-a-bot-with-the-bot-framework-composer)
 - [Analyze images](#analyze-images)
 - [Analyze video](#analyze-video)
 - [Classify images](#classify-images)
 - [Detect objects in images](#detect-objects-in-images)
 - [Detect analyze and recognize faces](#detect-analyze-and-recognize-faces)
 - [Read Text in images and documents with the Azure AI Vision Service](#read-text-in-images-and-documents-with-the-azure-ai-vision-service)
 - [Extract data from forms with Azure Document Intelligence](#extract-data-from-forms-with-azure-document-intelligence)
 - [Create an Azure AI Search solution](#create-an-azure-ai-search-solution)
 - [Create a custom skill for Azure AI Search](#create-a-custom-skill-for-azure-ai-search)
 - [Create a knowledge store with Azure AI Search](#create-a-knowledge-store-with-azure-ai-search)
 - [Enrich a search index using Language Studio](#enrich-a-search-index-using-language-studio)
 - [Implement advanced search features in Azure Cognitive Search](#implement-advanced-search-features-in-azure-cognitive-search)    
 - [Build an Azure Machine Learning custom skill for Azure Cognitive Search](#build-an-azure-machine-learning-custom-skill-for-azure-cognitive-search)
 - [Search data outside the Azure platform in Azure Cognitive Search using Azure Data Factory](#search-data-outside-the-azure-platform-in-azure-cognitive-search-using-azure-data-factory)
 - [Maintain an Azure Cognitive Search solution](#maintain-an-azure-cognitive-search-solution)


## Prepare to develop AI solutions on Azure
## Create and consume Azure AI Services
## Secure Azure AI Services
## Monitor Azure AI Services
## Deploy Azure AI services in containers
 - Containers enable you to host Azure AI Services either on-premises or on Azure.
 - A container is encapsulated in a container image that defines the software and configuration it must support. 
 - Understand containers: A container comprises an application or service and the runtime components needed to run it, while abstracting the underlying operating system and hardware.
   - Containers are portable across hosts
   - A single container host can support multiple isolated containers
   - Container deployment: A Docker* server, An Azure Container Instance (ACI), An Azure Kubernetes Service (AKS) cluster.
 - Use Azure AI Services containers
   - The container image for the specific Azure AI Services API you want to use is downloaded and deployed to a container host,
   - Client applications submit data to the endpoint provided by the containerized service, and retrieve results just as they would from an Azure AI Services cloud resource in Azure.
   - Periodically, usage metrics for the containerized service are sent to an Azure AI Services resource in Azure in order to calculate billing for the service.
   - **note:** Even when using a container, you must provision an Azure AI Services resource in Azure for billing purposes.(possible senitive data don't go to Azure, but container needs to connect to azure for billing purpose)
   - Azure AI Services container images: Each container provides a subset of Azure AI Services functionality.
   - Azure AI Services container configuration: ApiKey(Key from your deployed Azure AI Service; used for billing.), Billing(	Endpoint URI from your deployed Azure AI Service; used for billing.), Eula(Value of accept to state you accept the license for the container.)
   - Consuming Azure AI Services from a Container: adjust client apps such as endpoint, no need for subscription key, custom authentication solution, network security, etc
## Extract insights from text with the Azure AI Language service
## Translate text with Azure AI Translator service
## Create speech-enabled apps with Azure AI services
## Translate speech with the Azure AI Speech service
## Build a question answering solution
## Create a bot with the Bot Framework SDK
## Create a Bot with the Bot Framework Composer
## Analyze images
## Analyze video
## Classify images
## Detect objects in images
## Detect, analyze, and recognize faces
## Read Text in images and documents with the Azure AI Vision Service
## Extract data from forms with Azure Document Intelligence
## Create an Azure AI Search solution
## Create a custom skill for Azure AI Search
## Create a knowledge store with Azure AI Search
## Enrich a search index using Language Studio
## Implement advanced search features in Azure Cognitive Search
## Build an Azure Machine Learning custom skill for Azure Cognitive Search
## Search data outside the Azure platform in Azure Cognitive Search using Azure Data Factory
## Maintain an Azure Cognitive Search solution
## Get started with Azure OpenAI Service
## Build natural language solutions with Azure OpenAI Service
## Apply prompt engineering with Azure OpenAI Service


