Azure Content Safety Sample Code

This repository contains a sample implementation of the Azure Content Safety API, which allows you to analyze and moderate text and image content for harmful or inappropriate material. The project demonstrates how to interact with the Azure Content Safety API to detect unsafe content based on various categories, such as hate speech, self-harm, sexual content, and violence.
Prerequisites

    An Azure account with access to the Azure Content Safety API.
    .NET 6 or later installed on your machine.
    A subscription key for the Azure Content Safety API.

Getting Started

Follow these steps to set up and run the sample project:
1. Set up the Azure Content Safety API

Before using the API, you need to create an Azure Content Safety resource in the Azure portal.

    Go to the Azure Portal.
    Search for Content Safety in the marketplace and create a new resource.
    After creating the resource, get the endpoint URL and subscription key.

2. Clone this repository

Clone this repository to your local machine:

git clone https://github.com/sandeeppaldotnet/Azure-AI-Content-Safety-Demo.git
cd azure-content-safety-sample

3. Configure the project

Open the project in your preferred IDE or text editor. In the Program.cs file, replace the placeholders for the endpoint and subscription key with the values obtained from your Azure Content Safety resource:

string endpoint = "your-endpoint-url"; // The endpoint URL for your Content Safety API resource
string subscriptionKey = "your-subscription-key"; // Your Content Safety API subscription key

4. Run the project

To run the project, open a terminal/command prompt, navigate to the project directory, and execute the following:

dotnet run

The application will prompt you to enter the content (text) that you want to analyze. Once entered, it will send the content to the Azure Content Safety API and display the moderation results.
5. Customize Reject Thresholds

The rejectThresholds dictionary in the Program.cs file allows you to set custom rejection thresholds for each category. Adjust these values to meet your moderation requirements.

Dictionary<Category, int> rejectThresholds = new Dictionary<Category, int> {
    { Category.Hate, 4 },
    { Category.SelfHarm, 4 },
    { Category.Sexual, 4 },
    { Category.Violence, 4 }
};

6. View the Detection Results

The program will display the detection results, including the action (Accept or Reject) for each category, based on the severity score of the content.
Project Structure

    ContentSafetySampleCode: Contains the main logic for interacting with the Azure Content Safety API, handling both text and image analysis.
    Program.cs: The entry point of the application, which drives the content detection and decision-making process.
    DetectionResult and related classes: Used to model the data sent to and received from the API.
    Enums: Definitions for media types (Text, Image), content categories (Hate, SelfHarm, Sexual, Violence), and actions (Accept, Reject).

Key Classes and Methods

    ContentSafety: This is the main class that interacts with the Azure Content Safety API. It provides methods to:
        Build request URLs and payloads (BuildUrl, BuildRequestBody).
        Send content for detection (Detect).
        Deserialize the API response (DeserializeDetectionResult).
        Make a decision based on the results (MakeDecision).

    DetectionResult: The base class for API responses, containing a list of category analyses and severity scores.

    Decision: Represents the action recommended by the system based on the detected content's severity.

Error Handling

If an error occurs during the content detection process, a custom exception DetectionException is thrown. This provides details about the error code and message, which you can use for debugging.
Example:

Error: 400
{
    "error": {
        "code": "InvalidContent",
        "message": "The content provided is invalid for analysis."
    }
}
