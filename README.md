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
     - SpeechSynthesizer (SpeechConfig + AudioConfig): a proxy client for the Text to speech API.
     - use SpeechSynthesizer to call the underlying API functions
     - Process the response from the Azure AI Speech service:
       - AudioData
       - Properties
       - Reason ('SynthesizingAudioCompleted' | ...)
       - ResultId
 - Configure audio format and voices: **When synthesizing speech**, you can use a SpeechConfig object to customize the audio that is returned by the Azure AI Speech service.
   - Audio format:
     - Audio file type
     - Sample-rate
     - Bit-depth
     - To specify the required output format, use the **SetSpeechSynthesisOutputFormat** method of the **SpeechConfig** object
   - Voices:
     - Standard voices - synthetic voices created from audio samples.
     - Neural voices - more natural sounding voices created using deep neural networks.
     - To specify a voice for speech synthesis in the **SpeechConfig**, set its **SpeechSynthesisVoiceName** property to the voice you want to use
 - Use Speech Synthesis Markup Language:
   - Specify a speaking style, such as "excited" or "cheerful" when using a neural voice.
   - Insert pauses or silence.
   - Specify phonemes (phonetic pronunciations), for example to pronounce the text "SQL" as "sequel".
   - Adjust the prosody of the voice (affecting the pitch, timbre, and speaking rate).
   - Use common "say-as" rules, for example to specify that a given string should be expressed as a date, time, telephone number, or other form.
   - Insert recorded speech or audio, for example to include a standard recorded message or simulate background noise.
## Translate speech with the Azure AI Speech service
 - Translate speech to text:
   - SpeechTranslationConfig: encapsulate the information required to connect to your Azure AI Speech resource. Specifically, its location and key, also used to specify the speech recognition language (the language in which the input speech is spoken) and the target languages into which it should be translated.
   - AudioConfig(Optional): define the input source for the audio to be transcribed. By default, this is the default system microphone, but you can also specify an audio file.
   - TranslationRecognizer(SpeechTranslationConfig + AudioConfig): a proxy client for the Azure AI Speech translation API.
   - Use the methods of the TranslationRecognizer object to call the underlying API functions.
   - Process the response from Azure AI Speech. In the case of the RecognizeOnceAsync() method, the result is a SpeechRecognitionResult object that includes the following properties:
     - Duration
     - OffsetInTicks
     - Properties
     - Reason ('RecognizedSpeech'|'NoMatch'|'Cancelled')
     - ResultId
     - Text
     - Translations
 - Synthesize translations
   - Event-based synthesis: When you want to perform **1:1** translation (translating from one source language into a single target language), you can use event-based synthesis to capture the translation as an audio stream. Specify the desired voice for the translated speech in the TranslationConfig. Create an event handler for the TranslationRecognizer object's Synthesizing event. In the event handler, use the GetAudio() method of the Result parameter to retrieve the byte stream of translated audio.
   - Manual synthesis: essentially just the combination of two separate operations:
     - Use a TranslationRecognizer to translate spoken input into text transcriptions in one or more target languages.
     - Iterate through the Translations dictionary in the result of the translation operation, using a SpeechSynthesizer to synthesize an audio stream for each language.
## Build a question answering solution
 - Understand question answering: The Azure **AI Language** service includes a **question answering** capability, which enables you to define a **knowledge base** of question and answer pairs that can be queried using natural language input. The knowledge base can be published to a REST endpoint and consumed by client applications, commonly **bots**.
   - The knowledge base can be created from existing sources: FAQ website, Files containing structured text, Built-in chit chat question and answer pairs that encapsulate common conversational exchanges.
 - Compare question answering to Azure AI Language understanding: A question answering knowledge base is a form of language model, which raises the question of when to use question answering, and when to use the conversational language understanding capabilities of the Azure AI Language service. The two features are similar in that they both enable you to define a language model that can be queried using natural language expressions. The two services are in fact complementary. You can build comprehensive natural language solutions that combine conversational language understanding models and question answering knowledge bases.
   - Question answering: a static answer to a known question
   - conversational language understanding: Response indicates the most likely intent and referenced entities
 - Create a knowledge base:
   - Create an Azure AI Language resource in your Azure subscription( question answering feature, Create or select an Azure Cognitive Search resource to host the knowledge base index.).
   - In Azure AI Language Studio, select the Language resource and create a Custom question answering project (add data source, create knowledge base and edit Q&A pair).
 - Implement multi-turn conversation: sometimes you might need to ask follow-up questions to elicit more information from a user before presenting a definitive answer. This kind of interaction is referred to as a multi-turn conversation.
 - Test and publish a knowledge base: After you have defined a knowledge base, you can train its natural language model, and test it before publishing it for use in an application or bot.
 - Use a knowledge base: add a 'question' property in a request body
 - Improve question answering performance: After creating and testing a knowledge base, you can improve its performance with active learning and by defining synonyms.
   - Use active learning: Active learning can help you make continuous improvements so that it gets better at answering user questions correctly over time.
     - Implicit feedback: As incoming requests are processed, the service identifies user-provided questions that have multiple, similarly scored matches in the knowledge base. These are automatically clustered as alternate phrase suggestions for the possible answers that you can accept or reject in the Suggestions page for your knowledge base in Azure AI Language Studio.
     - Explicit feedback:
       - When developing a client application you can control the number of possible question matches returned for the user's input by specifying the **top** parameter. 
       - The response from the service includes a question object for each possible match, up to the **top** value specified in the request
       - You can implement logic in your client app to compare the score property values for the questions, and potentially present the questions to the user so they can positively identify the question closest to what they intended to ask.
       - With the correct question identified, your app can use the REST API to send feedback containing suggested alternative phrasing based on the user's original input.
       - The **qnaId** in the feedback corresponds to the **id** of the question the user identified as the correct match. The **userId** parameter is an identifier for the user and can be any value you choose, such as an email address or numeric identifier. The feedback will be presented in the active learning **Suggestions** page for your knowledge base in Azure AI Language Studio for you to accept or reject.
   - Define synonyms: Synonyms are useful when question submitted by users might include multiple different words to mean the same thing. To define synonyms, you must use the REST API to submit synonyms in the following JSON format.
 - Create a question answering bot: A bot is a conversational application that enables users to interact using natural language through one or more **channels**, such as email, web chat, voice messaging, or social media platform such as Microsoft Teams. To create a bot from your knowledge base, use Azure AI Language Studio to deploy the bot and then use the Create Bot button to create a bot in your Azure subscription. You can then edit and customize your bot in the Azure portal.
## Create a bot with the Bot Framework SDK
 - Introduce principles of bot design: Before embarking on the development of a bot, it's worth spending some time considering some principles for effective bot design.
   - Factors influencing a bot's success:
     - Is the bot discoverable? Discoverability can be achieved through integration with the proper channels. 
     - Is the bot intuitive and easy to use? The more difficult or frustrating a bot interaction is, the less use it will receive. Users will not return to a bad user experience.
     - Is the bot available on the devices and platforms that users care about? Knowing your customer-base is a good start to address this consideration. 
     - Can users solve their problems with minimal use and bot interaction? Although it may seem counter-intuitive, success doesn't equate to how long a user interacts with the bot. Users want answers to their issues or problems as quickly as possible. 
     - Does the bot solve the user issues better than alternative experiences? If a user can reach an answer with minimal effort through other means, they are less likely to use the bot.
   - Factors that do not guarantee success
     - Perhaps you want to ensure you have support for speech so that users don't have to type text for the interaction. Demonstrating factors such as these, may impress fellow developers, but are less likely to impress users. They could lead to user experience issues as well. The ability to support every language and dialect is not possible at this time. Speaker pronunciation and speed can greatly impact the accuracy. A user interacting with the bot in language that is not their native language can create issues in recognition. Other factors where speech enabled bots can be problematic are in noisy environments. Background noise will impact the accuracy of speech recognition and could create issues for the user in hearing the bot responses. Use voice only where it truly makes sense for bot user interaction.
     - Consider the concept of simplicity. The more complex your bot is, in terms of AI or machine learning features, the more open it may be to issues and problems. Consider adding advanced machine learning features to the bot if they are necessary to solve the problems the bot is designed to address.
     - Adding natural language features may not always make the bot experience great. A simple bot, that solves the user's problem without any conversational aspects, is still a successful bot.
   - Considerations for responsible AI
     - Articulate the purpose of your bot and take special care if your bot will support consequential use cases.
     - Be transparent about the fact that you use bots as part of your product or service.
     - Ensure a seamless hand-off to a human where the human-bot exchange leads to interactions that exceed the bot's competence.
     - Design your bot so that it respects relevant cultural norms and guards against misuse.
     - Ensure your bot is reliable.
     - Ensure your bot treats people fairly.
     - Ensure your bot respects user privacy.
     - Ensure your bot handles data securely.
     - Ensure your bot is accessible.
     - Accept responsibility for your bots operation and how it affects people.
 - Get started with the Bot Framework SDK:
   - Bot solutions on Microsoft Azure are supported by the following technologies:
     - Azure AI Bot Service. A cloud service that enables bot delivery through one or more channels, and integration with other services.
     - Bot Framework Service. A component of Azure AI Bot Service that provides a REST API for handling bot activities.
     - Bot Framework SDK. A set of tools and libraries for end-to-end bot development that abstracts the REST interface, enabling bot development in a range of programming languages.
   - Developing a Bot with the Bot Framework SDK: The Bot Framework SDK provides an extensive set of tools and libraries that software engineers can use to develop bots.
     - Bot templates
       - Empty Bot - a basic bot skeleton.
       - Echo Bot - a simple "hello world" sample in which the bot responds to messages by echoing the message text back to the user.
       - Core Bot - a more comprehensive bot that includes common bot functionality, such as integration with the Language Understanding service.
     - Bot application classes and logic
       - The template bots are based on the **Bot** class defined in the Bot Framework SDK, which is used to implement the logic in your bot that receives and interprets user input, and responds appropriately. Additionally, bots make use of an **Adapter** class that handles communication with the user's channel. Conversations in a bot are composed of **activities**, which represent events such as a user joining a conversation or a message being received. These activities occur within the context of a **turn**, a two-way exchange between the user and bot. The Bot Framework Service notifies your bot's adapter when an activity occurs in a channel by calling its **Process Activity** method, and the adapter creates a context for the turn and calls the bot's **Turn Handler** method to invoke the appropriate logic for the activity. 
     - Testing with the Bot Framework Emulator
       - Bots developed with the Bot Framework SDK are designed to run as cloud services in Azure, but while developing your bot, you'll need a way to test it before you deploy it into production. The Bot Framework Emulator is an application that enables you to run your bot local or remote web applications and connect to it from an interactive web chat interface that you can use to test your bot. Details of activity events are captured and shown in the testing interface, so you can monitor your bots behavior as you submit messages and review the responses.
 - Implement activity handlers and dialogs: The logic for processing the activity can be implemented in multiple ways. The Bot Framework SDK provides classes that can help you build bots that manage conversations using
   - Activity handlers: Event methods that you can override to handle different kinds of activities.
     - For simple bots with short, stateless interactions, you can use Activity Handlers to implement an event-driven conversation model in which the events are triggered by activities such as users joining the conversation or a message being received. When an activity occurs in a channel, the Bot Framework Service calls the bot adapter's **Process Activity** function, passing the activity details. The adapter creates a turn context for the activity and passes it to the bot's turn handler, which calls the individual, event-specific activity handler. The **ActivityHandler** base class includes event methods for the many kinds of common activity, including: Message received, Members left the conversation...
     - Turn context: An activity occurs within the context of a **turn**, which represents a single two-way exchange between the user and the bot. Activity handler methods include a parameter for the **turn context**, which you can use to access relevant information. For example, the activity handler for a message received activity includes the text of the message.
   - Dialogs: For more complex conversational flows where you need to store **state** between turns to enable a **multi-turn conversation**, you can implement **dialogs**. The Bot Framework SDK dialogs library provides multiple dialog classes that you can combine to implement the required conversational flow for your bot.
     - Component dialogs: A **component** dialog is a dialog that can contain other dialogs, defined in its **dialog set**. Often, the initial dialog in the component dialog is a **waterfall** dialog, which defines a sequential series of steps to guide the conversation. It's common for each step to be a **prompt** dialog so that conversational flow consists of gathering input data from the user sequentially. Each step must be completed before passing the output onto the next step
     - Adaptive dialogs: An **adaptive** dialog is another kind of container dialog in which the flow is more flexible, allowing for interruptions, cancellations, and context switches at any point in the conversation. In this style of conversation, the bot initiates a **root** dialog, which contains a flow of **actions** (which can include branches and loops), and **triggers** that can be initiated by actions or by a **recognizer**. The recognizer analyzes natural language input (usually using the Language Understanding service) and detects intents, which can be mapped to triggers that change the flow of the conversation - often by starting new child dialogs, which contain their own actions, triggers, and recognizers.
 - Deploy a bot
   - Create the Azure resources required to support your bot:
     - Register an Azure app: You can create the application registration by using the az ad app create Azure command-line interface (CLI) command, specifying a display name and password for your app identity. This command registers the app and returns its registration information, including a unique application ID that you will need in the following step.
     - Create a bot application service: Your bot requires a **Bot Channels Registration** resource, along with associated application service and application service plan. To create these resources, you can use the Azure resource deployment templates provided with the Bot Framework SDK template you used to create your bot. Just run the az deployment group create command, referencing the deployment template and specifying your bot application registration's ID (from the az ad app create command output) and the password you specified.
   - Prepare your bot for deployment: The specific steps you need to perform to prepare your bot depend on the programming language used to create it. For C# and JavaScript bots, you can use the az bot prepare-deploy command to ensure your bot is properly configured with the appropriate package dependencies and build files. For Python bots, you must include a requirements.txt file listing any package dependencies that must be installed in the deployment environment.
   - Deploy your bot as a web app: The final step is to package your bot application files in a zip archive, and use the az webapp deployment source config-zip command to deploy the bot code to the Azure resources you created previously. After deployment has completed, you can test and configure your bot in the Azure portal.
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


