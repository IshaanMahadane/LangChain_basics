# Restaurant Name & Menu Generator

This Streamlit app generates **restaurant names** and corresponding **menu items** based on the selected cuisine. It leverages OpenAI's GPT models via LangChain to provide creative and context-aware suggestions.

---

## 🚀 Features

- Select a cuisine from a sidebar dropdown (Indian, Chinese, Mexican, Italian, Arabic, American).  
- Automatically generate a fancy restaurant name.  
- Suggest a list of menu items relevant to the chosen cuisine.  
- Clean and interactive interface using **Streamlit**.  

---

## 🏗 Architecture

The app uses a modular architecture with two main components:

1. **Frontend (`frontend.py`)**
   - Built with Streamlit.
   - Handles user input (cuisine selection) and displays results (restaurant name + menu items).
   - Communicates with the backend helper module.

2. **Backend Helper (`langchain_helper.py`)**
   - Uses **LangChain** to orchestrate GPT-based chains.
   - **Chains** used:
     - `LLMChain` for generating restaurant name.
     - `LLMChain` for generating menu items.
     - `SequentialChain` to run the above chains in order.
   - GPT model accessed via `OpenAI` LLM class.

---

## 💻 Technology Stack

- **Frontend:** Streamlit  
- **Backend:** Python, LangChain  
- **LLM:** OpenAI GPT (via LangChain)  
- **Environment Management:** Conda or pip  
- **Secrets Management:** Streamlit secrets for OpenAI API key  

---

Installation Guide: Restaurant Name & Menu Generator
1. Clone the Repository
git clone https://github.com/<your-username>/langchain_basics.git
cd langchain_basics

2. Create a Virtual Environment (Optional but Recommended)
Using venv:
python -m venv venv
source venv/bin/activate   # On Linux/macOS
venv\Scripts\activate      # On Windows

Using conda:
conda create -n restaurant_gen python=3.11
conda activate restaurant_gen

3. Install Dependencies
pip install -r requirements.txt


Make sure the requirements.txt includes all packages:

streamlit==1.49.1
langchain==0.3.27
langchain-community==0.3.29
openai==1.108.1

4. Set Up OpenAI API Key

Create a file at .streamlit/secrets.toml in the repo folder.

Add your OpenAI API key:

openai_key = "sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"


⚠️ Make sure you do not commit this key to public repositories.

5. Run the App Locally
streamlit run frontend.py


The app should open in your default browser.

Use the sidebar to select a cuisine and generate a restaurant name and menu.

6. Optional: Deploy on Streamlit Cloud

Push your repository to GitHub.

Go to Streamlit Cloud.
Click “New App”, select your repo, branch, and set frontend.py as the main file.

Add your OpenAI API key in the Secrets section on Streamlit Cloud.

🔄 Workflow

User selects a cuisine.

frontend.py calls langchain_helper.generate_restaurant_name_and_items(cuisine).

langchain_helper runs a SequentialChain:

Step 1: GPT generates a restaurant name.

Step 2: GPT generates menu items based on the restaurant name.

Results are returned to the frontend and displayed.

⚠️ Notes

Make sure the OpenAI API key is valid and active.

The current implementation uses deprecated LangChain classes (LLMChain and OpenAI). Consider updating to langchain_openai for future compatibility.
