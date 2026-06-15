# RestaurantAssistAI: LLM-Powered Restaurant Recommendation Chatbot

![Python](https://img.shields.io/badge/Python-3.x-blue)
![OpenAI](https://img.shields.io/badge/OpenAI-LLM-green)
![LangChain](https://img.shields.io/badge/LangChain-Orchestration-orange)
![Generative AI](https://img.shields.io/badge/Generative%20AI-Application-purple)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

**Built using OpenAI API, LangChain, and geopy to deliver personalized restaurant recommendations through natural language conversations.**

## Project Overview

RestaurantAssistAI is an end-to-end Generative AI application that helps users discover restaurants through natural language conversations.

Instead of relying on static filters and dropdown selections, users can express their preferences conversationally, including:

- Cuisine preferences
- Budget constraints
- Location preferences
- Ambience requirements
- Dietary restrictions
- Parking requirements
- Occasion-specific needs

The system uses OpenAI APIs and LangChain to understand user requirements, retrieve relevant restaurant candidates, and generate personalized recommendations with detailed reasoning.

---

## Business Problem

Finding the right restaurant can be challenging due to the large number of available options and the variety of user preferences.

Traditional recommendation systems often depend on predefined filters and structured inputs, limiting flexibility and personalization.

The objective of this project is to build a conversational AI assistant that:

- Understands user intent through natural language.
- Extracts relevant dining preferences.
- Filters restaurants from a large restaurant dataset.
- Provides personalized recommendations.
- Explains the reasoning behind recommendations.

The solution is designed to create a more engaging and human-like restaurant discovery experience.

---

## Dataset Description

The restaurant dataset was sourced from publicly available Zomato restaurant data for Bengaluru.

### Dataset Characteristics

| Attribute | Value |
|------------|------------|
| Total Records | ~51,000 |
| Unique Restaurants | ~6,500 |
| Number of Features | 17 |
| Data Source | Kaggle |
| Location | Bengaluru, India |

The dataset contains:

- Restaurant details
- Ratings
- Cost information
- Cuisine information
- User reviews
- Location data

Due to OpenAI API cost constraints, the complete end-to-end chatbot workflow was tested on a representative subset of approximately 1,000 restaurant records.

---

## Project Objectives

1. Build a conversational restaurant recommendation assistant.
2. Extract restaurant attributes from unstructured user reviews.
3. Understand user requirements through natural language conversations.
4. Filter restaurants based on multiple user preferences.
5. Handle location mismatches intelligently.
6. Generate personalized recommendations with reasoning.
7. Provide a human-like recommendation experience.

---

## System Architecture

```text
User
 │
 ▼
RestaurantAssistAI Chatbot
 │
 ▼
Requirement & Intent Extraction (OpenAI)
 │
 ▼
Restaurant Filtering (LangChain + Pandas)
 │
 ├── Restaurant Dataset
 │
 └── Geopy Nearby Location Search
 │
 ▼
Top 5 Candidate Restaurants
 │
 ▼
Recommendation Generator (OpenAI)
 │
 ▼
Personalized Recommendation
```

---

## Application Workflow

```text
User Starts Conversation
            │
            ▼
Welcome Message
            │
            ▼
Collect Requirements
            │
            ├── Cuisine
            ├── Budget
            ├── Location
            ├── Ambience
            └── Preferences
            │
            ▼
Intent Confirmation
            │
            ▼
Requirement Extraction
            │
            ▼
Restaurant Search
            │
            ▼
Top 5 Restaurants
            │
            ▼
Best Recommendation
            │
            ▼
Persuasive Explanation
            │
            ▼
Conversation End
```

---

## Recommendation Pipeline

```text
Restaurant Reviews
          │
          ▼
OpenAI Feature Extraction
          │
          ▼
Structured Restaurant Dataset
          │
          ├── Cuisine
          ├── Ambience
          ├── Parking
          ├── Suggested Dishes
          ├── Cost
          └── Ratings
          │
          ▼
User Query
          │
          ▼
LangChain + OpenAI
          │
          ▼
Natural Language Filtering
          │
          ▼
Top 5 Restaurants
          │
          ▼
OpenAI Recommendation Engine
          │
          ▼
Final Recommendation
```

---

## LLM Components

| Component | Technology |
|------------|------------|
| Review Feature Extraction | OpenAI API |
| User Requirement Understanding | OpenAI API |
| Intent Confirmation | OpenAI API |
| Restaurant Filtering | LangChain + OpenAI |
| Recommendation Generation | OpenAI API |
| Nearby Location Resolution | geopy |

## System Design Stages

### Stage 1: Data Sourcing and Preparation

The restaurant dataset undergoes preprocessing and cleaning before being used by the recommendation engine.

A key design decision was to use OpenAI APIs to extract structured restaurant attributes from unstructured user reviews.

Examples of extracted attributes include:

- Ambience
- Parking Availability
- Recommended Dishes
- Family Friendliness
- Dining Experience Indicators

This transformation converts raw review text into structured restaurant features.

---

### Stage 2: User Requirement and Intent Confirmation

The chatbot gathers information through natural conversations.

Typical requirements include:

- Preferred cuisine
- Dining budget
- Location
- Ambience preferences
- Dietary restrictions

OpenAI APIs are used to validate and confirm user intent before restaurant retrieval begins.

---

### Stage 3: Restaurant Retrieval and Filtering

LangChain and OpenAI are used to interpret natural language requirements and retrieve matching restaurants from a Pandas dataframe.

If the user enters a location that does not exist in the restaurant database:

- geopy is used to identify nearby locations.
- Restaurants from nearby areas within approximately 3 km are considered.

This significantly improves user experience and recommendation coverage.

---

### Stage 4: Recommendation Generation

The top restaurant candidates are analyzed using OpenAI APIs.

The recommendation engine:

- Selects the most relevant restaurant.
- Generates supporting reasoning.
- Produces a persuasive recommendation narrative.

This creates a recommendation experience that feels more like interacting with a human expert.

---

## Key Design Decisions

### Precomputing Restaurant Features

Instead of extracting review information during runtime, restaurant attributes were extracted in advance.

Benefits:

- Faster response times
- Simpler filtering logic
- Reduced runtime token consumption

---

### Natural Language Filtering

Users are not restricted to predefined options.

Example:

**Assistant**

> Are you looking for Indian, Italian, Chinese, Continental, or Desserts?

**User**

> Ice Cream

The system intelligently maps this requirement to dessert-oriented restaurants.

---

### Location Fallback Strategy

One common challenge was handling locations not present in the dataset.

The solution uses geopy to identify nearby supported areas, ensuring that recommendations remain relevant even when exact matches are unavailable.

---

## Challenges Faced

- Cleaning inconsistent public restaurant data.
- Extracting meaningful restaurant attributes from large review datasets.
- Managing OpenAI API costs during large-scale feature extraction.
- Handling varying output formats across system stages.
- Filtering dataframe records using natural language requirements.
- Managing unsupported user-entered locations.
- Designing prompts that consistently produce structured outputs.

---

## Sample Conversation

A complete conversation example can be found here:

📄 **[View Sample Conversation](reports/sample_conversation.md)**

---

## Technologies Used

- Python
- OpenAI API
- LangChain
- Pandas
- NumPy
- geopy
- Jupyter Notebook

---

## Business Applications

Potential real-world applications include:

- Restaurant Discovery Platforms
- Food Delivery Applications
- Travel Recommendation Systems
- Hospitality Recommendation Engines
- Conversational Commerce
- AI Concierge Services

---

## Limitations

- Recommendations are limited to restaurants present in the dataset.
- Feature extraction was performed on a subset of records due to API cost considerations.
- Real-time restaurant availability is not considered.
- User preference learning is not yet implemented.

---

## Future Enhancements

1. Integrate vector databases for semantic restaurant retrieval.
2. Add user preference memory and personalization.
3. Integrate restaurant booking APIs.
4. Support real-time restaurant availability.
5. Implement Retrieval-Augmented Generation (RAG).
6. Add feedback-driven recommendation refinement.
7. Deploy as a Streamlit or FastAPI application.

---

## Repository Structure

```text
restaurant-recommender-ai/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── restaurant_sample.csv
│
├── notebooks/
│   └── RestaurantAssistAI.ipynb
│
├── reports/
│   ├── sample_conversation.md
│   └── figures/
│
└── src/
```

---

## How to Run

### Clone Repository

```bash
git clone https://github.com/rajani2024/restaurant-recommender-ai.git
```

### Navigate to Project Directory

```bash
cd restaurant-recommender-ai
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Configure Environment Variables

Create a `.env` file:

```env
OPENAI_API_KEY=your_api_key_here
```

### Launch Notebook

```bash
jupyter notebook notebooks/RestaurantAssistAI.ipynb
```

---

## Author

This project was completed as part of an advanced Generative AI learning journey focused on:

- Large Language Models (LLMs)
- Conversational AI
- Prompt Engineering
- LangChain Applications
- Recommendation Systems
- AI Application Development

The project demonstrates how OpenAI APIs and LangChain can be combined to build practical, user-facing AI applications that transform natural language requirements into personalized recommendations.