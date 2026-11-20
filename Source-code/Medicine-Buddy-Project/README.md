# Medicine Buddy

Medicine Buddy is an AI-powered medicine information platform designed to help users understand medicines, explore their ingredients, review relevant precautions, and ask medicine-related questions.

The application combines a SvelteKit frontend, FastAPI backend, PostgreSQL database, evidence retrieval, and conversational AI to provide accessible, source-grounded medicine information.

## Features

### 1. Medicine Search
- Search for medicines using their brand or generic name.
- Retrieve medicine information from the connected database.
- Display available medicine details and relevant source references.
- Support medicine identification using uploaded packaging images and OCR.
- Allow users to review and correct extracted text before searching.

### 2. Ingredient Information
- Identify ingredients associated with a medicine.
- Display information about their general uses and functions.
- Explain how ingredients generally work.
- Provide relevant information and supporting source references.

### 3. Medicine Analysis
- Analyse available medicine information and ingredient evidence.
- Compare user-provided health conditions and allergies against available evidence.
- Highlight relevant precautions and potential concerns.
- Present the evidence used for the analysis.

### 4. Conversational AI Assistant
- Ask questions about medicines and their ingredients.
- Receive conversational responses using retrieved information.
- Ask follow-up questions using conversation context.
- View relevant source references where available.
- Indicate when the available evidence is insufficient.

**Note:** Medicine Analysis and the Conversational AI Assistant are separate features designed for different purposes.

### 5. Evidence-Based Retrieval
- Retrieve relevant information from the connected medicine database and external sources.
- Use search and retrieval to identify supporting information.
- Present source references to help users verify information.
- Aim to avoid presenting unsupported information as established medical facts.

## Technology Stack

| Component | Technology |
|---|---|
| Frontend | SvelteKit |
| Frontend Styling | CSS |
| Backend | Python, FastAPI |
| Database | PostgreSQL (Neon) |
| AI Agent | LangChain `create_agent` |
| LLM Providers | Groq and Google Gemini |
| Web Search | Tavily |
| OCR | Tesseract.js |
| Deployment | Vercel |
| Version Control | Git and GitHub |

## System Architecture

Medicine Buddy follows a frontend-backend architecture.

1. **Frontend:** SvelteKit provides the user interface for medicine searches, image uploads, analysis, and conversational questions.
2. **Backend:** FastAPI handles API requests, medicine lookup, evidence retrieval, and AI-related operations.
3. **Database:** PostgreSQL stores structured medicine and ingredient information.
4. **Retrieval Layer:** Relevant information is retrieved from available database records and external sources.
5. **AI Agent:** LangChain connects the conversational assistant to its evidence-retrieval tools and configured language model providers.
6. **Response:** The backend returns retrieved information and generated responses to the frontend for display.

## Project Structure

```text
Medicine_Buddy/
|
|-- backend/
|   |-- app/
|   |   |-- main.py
|   |   |-- agent.py
|   |
|   |-- data/
|   |-- database.py
|   |-- requirements.txt
|   |-- check_backend.py
|   |-- clean_dataset.py
|   |-- test_agent.py
|
|-- src/
|   |-- lib/
|   |   |-- api.js
|   |
|   |-- routes/
|   |   |-- +page.svelte
|   |   |-- +layout.svelte
|   |
|   |-- app.css
|   |-- app.html
|
|-- index.py
|-- package.json
|-- package-lock.json
|-- svelte.config.js
|-- vite.config.js
|-- vercel.json
|-- .env.example
|-- .gitignore
|-- README.md
```

*The structure above shows the main project files. Only include files and folders that are actually present in the submitted project.*

## Installation and Setup

### Prerequisites

- Python 3.10 or newer
- Node.js and npm
- Git
- VS Code
- Internet connection

### 1. Clone the Repository

```bash
git clone https://github.com/sakshi-G07/Medicine_Buddy.git
cd Medicine_Buddy
```

### 2. Set Up the Backend

Navigate to the backend directory:

```powershell
cd backend
```

Create and activate a virtual environment:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install the Python dependencies:

```powershell
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a local `.env` file using the provided `.env.example` as a reference.

The application may require the following environment variables, depending on the configured backend:

```env
DATABASE_URL=your_database_connection_string
GROQ_API_KEY=your_groq_api_key
GEMINI_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
```

Add the actual values to your local environment configuration and Vercel project settings.

**Important:** Never commit API keys, database credentials, or private environment files to GitHub.

### 4. Start the Backend

Run the following command from the `backend` directory:

```powershell
py -m uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

The backend will normally be available at:

```text
http://127.0.0.1:8000
```

API health endpoint:

```text
http://127.0.0.1:8000/api/health
```

The exact endpoint depends on the routes configured in `main.py`.

### 5. Set Up the Frontend

Open a second terminal in the project root directory:

```powershell
npm install
```

Start the development server:

```powershell
npm run dev
```

Open the local URL displayed in the terminal, normally:

```text
http://localhost:5173
```

The frontend communicates with the backend through the configured API connection.

## Deployment

The application is deployed through Vercel using the project's existing deployment configuration.

To deploy:

1. Push the latest project changes to the connected GitHub repository.
2. Open the project in Vercel.
3. Configure the required environment variables in Vercel project settings.
4. Trigger a deployment.
5. Verify the deployed website and API health endpoint.
6. Test the available medicine search, analysis, and conversational features.

The deployment uses the existing project build configuration.

**Live Application:** https://medicine-buddy.vercel.app/

## Safety and Limitations

- Medicine Buddy is an educational medicine-information platform, not a clinically validated medical device.
- It does not diagnose diseases or prescribe medicines.
- It does not replace advice from a qualified doctor or pharmacist.
- Medicine identification results should be checked against the actual packaging.
- OCR can make mistakes, so extracted text must be reviewed.
- Ingredient and precaution information depends on the availability and completeness of sources.
- The absence of a warning in retrieved information does not mean a medicine is safe.
- AI-generated responses may be incomplete or incorrect. Important medical decisions should always be verified with a healthcare professional.

## Future Improvements

- Expand medicine and ingredient database coverage.
- Improve medicine identification from packaging images.
- Add more authoritative and region-specific medical references.
- Improve retrieval accuracy and source verification.
- Enhance conversational context handling.
- Add further validation and testing.

## Author

**Medicine Buddy**

An academic project developed as part of the MSc Artificial Intelligence programme.

**Repository:** https://github.com/sakshi-G07/Medicine_Buddy

