# Hackathon-Finals
SME BUSINESS ADVISOR IN A BOX - NEXA

import streamlit as st
import pandas as pd
import google.generativeai as genai

st.set_page_config(page_title="UFIX AI", layout="wide")

st.title("🚀 UFIX AI — SME Business Advisor")

# KPI CARDS
col1, col2, col3, col4 = st.columns(4)

col1.metric("Registered SMEs", "4,85,000", "+10%")
col2.metric("Avg Growth", "16%")
col3.metric("Loan Access", "62%")
col4.metric("Risk Level", "Low")

st.divider()

data = {
    "Sector": ["Manufacturing", "Services", "Retail", "Tech"],
    "SMEs": [1200, 2100, 900, 650],
    "Growth": [12,18,9,25]
}

df = pd.DataFrame(data)

colA, colB = st.columns(2)

with colA:
    st.subheader("SME Distribution")
    st.bar_chart(df.set_index("Sector")["SMEs"])

with colB:
    st.subheader("Growth Trend")
    st.line_chart(df.set_index("Sector")["Growth"])

st.divider()

st.header("🤖 AI SME Consultant")

industry = st.text_input("Industry")
size = st.selectbox("Business Size", ["Micro","Small","Medium"])
goal = st.text_area("Business Goal")

api_key = st.text_input("Gemini API Key", type="password")

if st.button("Generate Advice"):

    if api_key:
        genai.configure(api_key=api_key)
        model = genai.GenerativeModel("gemini-pro")

        prompt = f"""
        You are an SME consultant.

        Industry: {industry}
        Size: {size}
        Goal: {goal}

        Provide:
        SWOT Analysis
        Pricing Strategy
        Growth Ideas
        Government Scheme Suggestions
        """

        response = model.generate_content(prompt)

        st.success("AI Recommendation")
        st.write(response.text)

        # NEXA: SME Business Advisor in a Box (UFIX AI)
        

## 📌 PROJECT OVERVIEW

[cite_start]Small and Medium Enterprise (SME) owners and operators frequently face a major pain point: they cannot afford expensive professional consultants for market research, pricing, or strategic planning[cite: 51, 52]. [cite_start]NEXA, operating through the UFIX AI platform, is an innovative AI-powered chatbot that acts as a virtual business advisor[cite: 55, 69, 75]. 

[cite_start]By inputting specific business details such as industry, size, and goals, the tool instantly generates tailored, actionable business strategies[cite: 56, 57]. [cite_start]This solution democratises high-tier consulting for millions of SMEs by delivering strategic outcomes in seconds at zero marginal cost, drastically reducing the time and money required to generate a strategy report[cite: 53, 61, 62].


## ✨ KEY FEATURE

* [cite_start]**Interactive Analytics Dashboard**: Displays high-level summary metrics and KPIs such as Registered SMEs, Average Growth, Loan Access percentage, and Risk Levels[cite: 46, 77, 80, 88, 90].
* [cite_start]**Visual Data Insights**: Provides bar charts illustrating SME distribution by sector and line charts tracking growth trends[cite: 83, 87].
* [cite_start]**AI SME Consultant**: A core chatbot interface that takes in user queries regarding their industry, business size, and goals[cite: 28, 92].
* [cite_start]**Instant Strategy Generation**: Harnesses NLP and ML algorithms to generate a comprehensive SWOT analysis, pricing strategies, and specific growth ideas[cite: 37, 42, 44, 45, 57].
* [cite_start]**Government Scheme Suggestions**: Identifies and recommends relevant initiatives, such as MSME Udyam, MUDRA loans, and digital transformation grants[cite: 127, 128].



## 🏗️ARCHITECTURE AND WORKFLOW

1. [cite_start]**File/Data Input**: The user provides their industry data, financials, size, goals, and specific queries[cite: 28].
2. [cite_start]**Data Validation & Processing**: The system harmonizes the input data to prepare it for the AI model[cite: 24, 31].
3. [cite_start]**AI Chatbot Core**: The inputs are processed through the AI's internal Pricing Suggester and SWOT Analyzer[cite: 33, 34, 35].
4. [cite_start]**Insights Generation**: The system evaluates the data to generate specific business insights[cite: 38, 39].
5. [cite_start]**Dashboard Display**: The finalized pricing forecasts, SWOT visuals, and growth strategies are displayed on the UFIX AI dashboard[cite: 40, 43, 44, 45].

## 🛠️ Technology Stack
* [cite_start]**UI/Frontend**: Streamlit and Lovable[cite: 21, 67].
* [cite_start]**Ideation, Logic & Agent Design**: Google Gemini[cite: 18, 20, 64, 66].
* [cite_start]**Knowledge Base**: Google Sheets[cite: 19, 65].
* [cite_start]**Data Foundation**: Grounded in datasets like the World Bank Enterprise Surveys and the MSME Data Portal[cite: 12, 58].

## 🚀INSTALLATION AND SETUP 

To run this application locally, you will need Python installed. Follow these steps:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/nexa-ufix-ai.git](https://github.com/yourusername/nexa-ufix-ai.git)
   cd nexa-ufix-ai
Install the required dependencies:
The project requires Streamlit, Pandas, and the Google Generative AI SDK.

Bash
pip install streamlit pandas google-generativeai
Run the Streamlit application:

Bash
streamlit run app.py
(Note: Ensure your code file is named app.py, or replace app.py with your specific python file name).

#API Key Setup:
You will need a Gemini API Key to power the AI Consultant. You can securely enter this key directly into the application's UI sidebar/input field when running it.

#DATASET

World Bank Enterprise Surveys 

MSME Data Portal 
