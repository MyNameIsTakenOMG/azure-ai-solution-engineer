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
 - Language detection: determining the language in which text is written.
   - keywords: **request: document(limit:5120 chars, 1000 items), item(countryHint, id, text). response: {language_name, language_code, confidence_score} -- multilingual content: predominant language , ambiguity: unknown & NaN**
 - Key phrase extraction: identifying important words and phrases in the text that indicate the main points.
   - limit: 5120 chars per document
 - Sentiment analysis: quantifying how positive or negative the text is. (scenarios: reviews)
   - keywords: **positive, negative, and neutral**
   - If all sentences are neutral, the overall sentiment is neutral.
   - If sentence classifications include only positive and neutral, the overall sentiment is positive.
   - If the sentence classifications include only negative and neutral, the overall sentiment is negative.
   - If the sentence classifications include positive and negative, the overall sentiment is mixed.
 - Named entity recognition - detecting references to entities, including people, locations, DateTime, organizations, addresses, email, URLs, and more.
 - Entity linking: identifying specific entities by providing reference links to Wikipedia articles.
## Translate text with Azure AI Translator service
 - Understand language detection, translation, and transliteration(translate it to a different language, you may want to transliterate it to a different script in order to get accurate pronounciation)
 - Specify translation options:
   - Word alignment: to understand the relationship between the characters in the source text and the corresponding characters in the translation. 
   - Sentence length: Sometimes it might be useful to know the length of a translation, for example to determine how best to display it in a user interface. You can get this information by setting the includeSentenceLength parameter to true.
   - Profanity filtering: Sometimes text contains profanities, which you might want to obscure or omit altogether in a translation. You can handle profanities by specifying the profanityAction parameter
     - NoAction
     - Deleted
     - Marked: Profanities are indicated using the technique indicated in the profanityMarker parameter (if supplied). The default value for this parameter is Asterisk, which replaces characters in profanities with "*". As an alternative, you can specify a profanityMarker value of Tag, which causes profanities to be enclosed in XML tags.
 - Define custom translations: While the default translation model used by Azure AI Translator is effective for general translation, you may need to develop a translation solution for businesses or industries in that have specific vocabularies of terms that require custom translation.
   - **note:** Your custom model is assigned a unique category Id (highlighted in the screenshot), which you can specify in translate calls to your Azure AI Translator resource by using the category parameter, causing translation to be performed by your custom model instead of the default model.
   - call custom translator API:
     - request parameters: `api-version`, `to`, `category`(your category ID)
     - request headers: `Ocp-Apim-Subscription-Key`, `Content-Type`
## Create speech-enabled apps with Azure AI services
 - Azure AI Speech provides APIs that you can use to build speech-enabled applications
   - Speech to text: An API that enables **speech recognition** in which your application can accept spoken input.
   - Text to speech: An API that enables **speech synthesis** in which your application can provide spoken output.
   - Speech Translation: An API that you can use to translate spoken input into multiple languages.
   - Speaker Recognition: An API that enables your application to recognize individual speakers based on their voice.
   - Intent Recognition: An API that uses conversational language understanding to determine the semantic meaning of spoken input.
 - Use the Azure AI Speech to text API:The Azure AI Speech service supports speech recognition through two REST APIs:
   - The Speech to text API, which is the primary way to perform speech recognition.
   - The Speech to text Short Audio API, which is optimized for short streams of audio (up to 60 seconds).
   - Using the Azure AI Speech SDK (consistent pattern):
     - SpeechConfig (encapsulate the information required to connect to your Azure AI Speech resource.)
     - AudioConfig (optional, define the input source for the audio to be transcribed. microphone or audio file)
     - SpeechRecognizer (SpeechConfig + AudioConfig): a proxy client for the Speech to text API.
     - use SpeechRecognizer to call the underlying API functions
     - Process the response from the Azure AI Speech service:
       - Duration
       - OffsetInTicks
       - Properties ('CancellationReason')
       - Reason ('RecognizedSpeech' | 'NoMatch' | 'Canceled')
       - ResultId
       - Text (the transcript)
 - Use the text to speech API:
   - The Text to speech API, which is the primary way to perform speech synthesis.
   - The Batch synthesis API, which is designed to support batch operations that convert large volumes of text to audio - for example to generate an audio-book from the source text.
   - Using the Azure AI Speech SDK (pattern):
     - SpeechConfig
     - AudioConfig (define the output device for the speech to be synthesized)
     - SpeechSynthesizer (SpeechConfig + AudioConfig) : a proxy client for the Text to speech API.
     - use SpeechSynthesizer to call the underlying API functions
     - Process the response from the Azure AI Speech service:
       - AudioData
       - Properties
       - Reason ('SynthesizingAudioCompleted' | ...)
       - ResultId
 - Configure audio format and voices: When synthesizing speech, you can use a SpeechConfig object to customize the audio that is returned by the Azure AI Speech service.
   - Audio format:
     - Audio file type
     - Sample-rate
     - Bit-depth
   - Voices:
     - Standard voices - synthetic voices created from audio samples.
     - Neural voices - more natural sounding voices created using deep neural networks.
 - Use Speech Synthesis Markup Language:
   - Specify a speaking style, such as "excited" or "cheerful" when using a neural voice.
   - Insert pauses or silence.
   - Specify phonemes (phonetic pronunciations), for example to pronounce the text "SQL" as "sequel".
   - Adjust the prosody of the voice (affecting the pitch, timbre, and speaking rate).
   - Use common "say-as" rules, for example to specify that a given string should be expressed as a date, time, telephone number, or other form.
   - Insert recorded speech or audio, for example to include a standard recorded message or simulate background noise.
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


