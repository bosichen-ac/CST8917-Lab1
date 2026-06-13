# CST8917 Lab 1: Create and Deploy Your First Azure Function

- Student Name: Bosi Chen
- Student ID: 041040774
- Course: CST8917 Serverless Applications

---

## Demo Video

[Video Demo](https://youtu.be/feOiuJxYIvA)

---

## Overview

This project is an Azure Function application built with Python. It provides a text analysis API that calculates various statistics from user-provided text and stores analysis results in Azure Cosmos DB.

## Features

- Analyze text through an HTTP endpoint
- Calculate:
  - Word count
  - Character count
  - Character count without spaces
  - Sentence count
  - Paragraph count
  - Average word length
  - Longest word
  - Estimated reading time
- Store analysis results in Azure Cosmos DB
- Retrieve previous analysis records through a history endpoint

## Technologies
- Visual Studio Code
- Python 3.12.11
- Azure Functions
- Azure Functions Core Tools
- Azure Cosmos DB

## Installation Guide

### Prerequisites

- Python 3.12
- Visual Studio Code
  - Azure Functions Extension
  - Azurite Extension
- Azure Account

### Clone GitHub Repo

```
git clone https://github.com/bosichen-ac/CST8917-Lab1.git
cd CST8917-Lab1
```

### Create a Virtual Environment in VS Code

Open Command Palette and select `Python: Create Environment`. Select Python 3.12 and create `.venv` using the `requirements.txt` in the repo.

### Create Cosmos DB 

Create an Azure Cosmos DB account.

Create a database named `TextAnalyzer` and a container named `Results` using `/id` as the partition key.

### Environment Variables

Create a `local.settings.json` file in the project root using the `local.settings.json.example` file.

Replace `<your-cosmos-db-connection-string>` with your Azure Cosmos DB connection string.

### Run the Application

Start Azurite using the VS Code Command Palette: `Azurite: Start`.

Start the Azure Function in the Run and Debug tab or by pressing `F5`.

The application will be available at: http://localhost:7071

### API Endpoints

#### TextAnalyzer

TextAnalyzer can be used to analyze text and store the result in Cosmos DB.

```
GET http://localhost:7071/api/TextAnalyzer?text=Hello world
```
or
```
POST http://localhost:7071/api/TextAnalyzer

{
  "text": "Hello world"
}
```

#### GetAnalysisHistory

Retrieve previously stored analysis results.
```
/api/GetAnalysisHistory
```
Optional limit parameter:
```
/api/GetAnalysisHistory?limit=5
```