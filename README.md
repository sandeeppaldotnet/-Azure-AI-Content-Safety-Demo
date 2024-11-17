# -Azure-AI-Content-Safety-Demo
Azure-AI-Content-Safety-Demo

This is a demonstration project for Azure AI Content Safety using C#. The goal of this demo is to show how to integrate Azure's AI capabilities for content moderation and safety into a C# application.
Overview

The Azure AI Content Safety Demo project helps developers integrate Azure AI's content moderation APIs into their C# applications to detect and filter potentially harmful or inappropriate content in text, images, and videos. The demo utilizes Azure Cognitive Services to perform content analysis and classification.
Features

    Text moderation: Analyze text content for potential risks, including profanity, personal information, and harmful language.
    Image moderation: Detect inappropriate content in images using the Azure Content Moderator API.
    Video moderation: Evaluate videos for explicit content using Azure’s Video Indexer.
    Real-time results: Get immediate feedback and suggestions for handling detected unsafe content.
    Customizable thresholds: Adjust moderation sensitivity to meet your specific needs.

Prerequisites

Before you run the demo, make sure you have the following:

    Microsoft Azure account:
        You will need an Azure account with access to the Cognitive Services APIs, including the Content Moderator API.
        Create a Cognitive Services resource in the Azure portal.

    .NET SDK:
        Install .NET SDK (version 6.0 or later).

    API Keys:
        Once you have created the Cognitive Services resource, you'll need the API keys from the Azure portal to authenticate your requests.

    Visual Studio (optional):
        If you're using Visual Studio, you can open the solution directly and build the project.

Setup Instructions

    Clone the repository:

git clone https://github.com/yourusername/Azure-AI-Content-Safety-Demo.git

Navigate into the project directory:

cd Azure-AI-Content-Safety-Demo

Install the required NuGet packages:

dotnet restore

Configure the API keys:

    Open the appsettings.json file in the project and add your Azure Content Moderator API key and endpoint URL:

    {
      "AzureContentModerator": {
        "Endpoint": "your-azure-endpoint",
        "ApiKey": "your-api-key"
      }
    }

Running the Demo

To run the application, use the following command:

dotnet run

This will launch the application, and you can interact with it via the console or UI (depending on your project setup). The app will process the sample content or allow you to input your own content for moderation.
Example

    To check text content for inappropriate language:

var textToAnalyze = "This is some sample text.";
var moderationResult = await contentModeratorClient.ModerateTextAsync(textToAnalyze);
Console.WriteLine(moderationResult);

    To analyze an image for inappropriate content:

var imageUrl = "https://example.com/image.jpg";
var imageAnalysisResult = await contentModeratorClient.ModerateImageAsync(imageUrl);
Console.WriteLine(imageAnalysisResult);

Features in Action

This project showcases several key features of Azure’s AI-powered content safety tools, including:

    Text Moderation: Detects offensive language and personal information.
    Image Moderation: Flags images with explicit content or disturbing imagery.
    Video Moderation: Analyzes video files for harmful or offensive material.
