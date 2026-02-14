
# Text to SQL LLM Application with Google Gemini Pro

## Overview
This project is an **end-to-end Generative AI application** designed to convert natural language text into SQL queries and retrieve data from a SQL database. It leverages the **Google Gemini Pro** LLM to understand user intent and generate precise SQL commands, which are then executed against a local **SQLite** database.

The application features a user-friendly interface built with **Streamlit**, allowing users to ask questions about their data in plain English and receive real-time results from the database.

## Features
*   **Natural Language Processing**: Converts complex English questions into executable SQL queries.
*   **Gemini Pro Integration**: Uses Google's advanced LLM for high-accuracy query generation.
*   **Database Interaction**: Automatically hits an SQLite database to fetch and display records.
*   **Support for Complex Queries**: Handles operations such as `AVERAGE`, `GROUP BY`, and ranking (e.g., finding the second-highest marks).

## Tech Stack
*   **Language**: Python (3.9+).
*   **LLM**: Google Gemini Pro.
*   **Frontend**: Streamlit.
*   **Database**: SQLite 3.
*   **Libraries**: `google-generativeai`, `python-dotenv`.

## Project Structure
*   **`app.py`**: The main Streamlit application that handles the UI, LLM interaction, and database querying.
*   **`SQL.py`**: A helper script to create the initial SQLite database, define the table schema, and insert sample student records.
*   **`requirements.txt`**: Contains the necessary Python libraries for the project.
*   **`.env`**: Stores the sensitive **Google API Key**.

## Installation & Setup

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd <repository-folder>
```

### 2. Create a Virtual Environment
It is recommended to use **Python 3.9+** for compatibility with Google Gemini Pro.
```bash
conda create -p venv python=3.9 -y
conda activate venv/
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure API Key
Create a `.env` file in the root directory and add your Google API Key:
```env
GOOGLE_API_KEY="your_api_key_here"
```
*You can obtain your API key from [Google AI Studio (MakerSuite)](https://aistudio.google.com/app/apikey)*.

### 5. Initialize the Database
Run the script to create the `student.db` file and populate it with sample data:
```bash
python SQL.py
```
This script creates a `student` table with columns: `NAME`, `CLASS`, `SECTION`, and `MARKS`.

## Usage
To launch the application, run:
```bash
streamlit run app.py
```
Once the app is running in your browser, you can enter questions like:
*   *"Tell me all the students' names."*
*   *"Give me the average marks of all students class-wise."*
*   *"Provide the student name with the second-highest marks."*

## How it Works
1.  **Prompt Engineering**: A custom prompt instructs the LLM to behave as an expert SQL converter, ensuring the output is a clean SQL query without additional text or markdown formatting.
2.  **Query Generation**: The user's question and the prompt are sent to **Gemini Pro**, which returns a SQL query.
3.  **Data Retrieval**: The generated query is executed against the `student.db` SQLite database.
4.  **Display**: The retrieved records are displayed directly on the Streamlit dashboard.
