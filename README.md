# VIRTUAL-CARE-ASSISTANT: Revolutionizing Healthcare with AI

![Virtual Care Assistant](https://github.com/abdulghaffaransari/Virtual-Care-Assistant/blob/main/Results/Pic1.png)

## Overview

The **VIRTUAL-CARE-ASSISTANT** is an **LLM-powered medical chatbot** that leverages the latest advancements in **LangChain**, **Pinecone**, and **OpenAI's GPT-3.5-turbo-instruct** model. This innovative project is designed to redefine the way users access and interact with medical knowledge. Built to provide precise and concise answers, the assistant empowers users with insights directly sourced from trusted medical resources like the **Gale Encyclopedia of Medicine**.

This project showcases the seamless integration of cutting-edge technologies to deliver a **scalable, efficient, and user-friendly virtual assistant** capable of answering complex health-related queries.

---

## Key Features

1. **LLM Integration**: Powered by **OpenAI's GPT-3.5-turbo-instruct**, delivering high-quality, context-aware responses.
2. **LangChain Framework**: Enables efficient document parsing, text splitting, and retrieval augmentation.
3. **Pinecone Vector Database**: Ensures ultra-fast semantic search for relevant document chunks.
4. **Comprehensive Knowledge Base**: Extracts reliable information from the **Gale Encyclopedia of Medicine**.
5. **Modern Chat Interface**: Features a sleek, responsive UI for seamless user interaction.
6. **Embeddings from HuggingFace**: Utilizes `sentence-transformers/all-MiniLM-L6-v2` for high-dimensional semantic text representation.

---

## How It Works

### 1. **Data Processing**
   - **PDF Parsing**: Using LangChain's `PyPDFLoader`, the **Gale Encyclopedia of Medicine** is ingested and converted into text.
   - **Text Splitting**: The content is split into 500-character chunks with a 20-character overlap using LangChain's `RecursiveCharacterTextSplitter`.

### 2. **Semantic Search**
   - **HuggingFace Embeddings**: Text chunks are embedded into 384-dimensional vectors for semantic understanding.
   - **Pinecone Indexing**: Embeddings are stored in **Pinecone**, enabling fast and accurate similarity search.

### 3. **Question Answering**
   - **Retrieval-Augmented Generation (RAG)**: Relevant document chunks are retrieved from Pinecone and passed to **OpenAI's GPT-3.5-turbo-instruct** for response generation.
   - **System Prompt Engineering**: A carefully crafted prompt ensures concise, medically accurate answers.

### 4. **Chatbot Interface**
   - Users interact via a **Flask-powered web interface**, styled with Bootstrap and CSS for an intuitive experience.
   - Real-time responses are displayed in a dynamic chat format.

---

## The GPT-3.5-Turbo-Instruct Model

At the core of this project is **OpenAI's GPT-3.5-turbo-instruct**. Unlike conversational models like GPT-3.5-turbo, this variant is optimized for **instruction-following tasks**, ensuring:
- **Accurate and Focused Responses**: Adapts to structured prompts and retrieves context-aware answers.
- **Cost-Effective Performance**: Offers advanced capabilities at a significantly lower cost compared to GPT-4.

### How We Use GPT-3.5-Turbo-Instruct:
1. The system prompt defines the assistant's behavior:
   ```python
   system_prompt = (
       "You are an assistant for question-answering tasks. "
       "Use the following pieces of retrieved context to answer "
       "the question. If you don't know the answer, say that you "
       "don't know. Use three sentences maximum and keep the "
       "answer concise."
       "\n\n"
       "{context}"
   )
   ```
2. Retrieved chunks from Pinecone are provided as context.
3. The model generates answers based on the prompt and context, delivering concise and informative responses.

---

## Project Structure

```plaintext
VIRTUAL-CARE-ASSISTANT/
│
├── app.py                        # Flask web application
├── store_index.py                # Script for embedding and indexing
├── requirements.txt              # Project dependencies
├── setup.py                      # Project setup
├── templates/
│   └── chat.html                 # Chat interface
├── static/
│   └── style.css                 # Chat interface styling
├── src/
│   ├── helper.py                 # PDF processing and embeddings
│   ├── prompt.py                 # System prompt definition
│   └── __init__.py               # Package initialization
├── Data/                         # Medical encyclopedia PDF files
├── research/
│   └── trials.ipynb              # Experimentation notebook
├── Results/                      # Screenshots and output examples
│   └── Pic1.png                  # Chatbot example screenshot
└── .env                          # Environment variables
```

---

## Setting Up the Project

Follow these steps to set up the **VIRTUAL-CARE-ASSISTANT**:

### 1. Clone the Repository
```bash
git clone https://github.com/abdulghaffaransari/Virtual-Care-Assistant.git
cd Virtual-Care-Assistant
```

### 2. Install Dependencies
Install the required Python packages:
```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables
Create a `.env` file and add your API keys:
```plaintext
PINECONE_API_KEY=your_pinecone_api_key
OPENAI_API_KEY=your_openai_api_key
```

### 4. Initialize the Knowledge Base
Run the script to process the medical PDF, generate embeddings, and store them in Pinecone:
```bash
python store_index.py
```

### 5. Start the Application
Run the Flask application and access it in your browser:
```bash
python app.py
```
Visit `http://localhost:8080` to interact with the chatbot.

---

## Example Interaction

### User Query:
*"What are the symptoms of diabetes?"*

### System Workflow:
1. The query is processed by the Flask app.
2. Relevant text chunks are retrieved from Pinecone using similarity search.
3. The context is passed to OpenAI's GPT-3.5-turbo-instruct model, which generates the response.

### Chatbot Response:
*"The primary symptoms of diabetes include increased thirst, frequent urination, and unexplained weight loss. Consult a healthcare professional for proper diagnosis and treatment."*

---

## Technologies Used

1. **OpenAI GPT-3.5-Turbo-Instruct**: Powers the assistant with accurate and context-driven responses.
2. **LangChain**: Facilitates text parsing, splitting, and chain creation for retrieval-augmented generation.
3. **Pinecone**: Provides a high-performance vector database for semantic search.
4. **HuggingFace**: Offers robust embedding models for semantic text representation.
5. **Flask**: Serves the web application for user interaction.

---

## Knowledge Source: Gale Encyclopedia of Medicine

The **Gale Encyclopedia of Medicine** (Second Edition) serves as the foundation of the assistant's knowledge base. This trusted resource provides detailed, authoritative information on medical conditions, treatments, and terminology.

---

## Future Enhancements

- **Voice Interaction**: Integrate voice-based queries and responses.
- **User Customization**: Tailor suggestions based on user preferences and history.
- **Multilingual Support**: Enable chatbot interaction in multiple languages.
- **Mobile App**: Extend functionality to Android and iOS platforms.

---

## Author

**Abdul Ghaffar Ansari**  
Email: [abdulghaffaransari9@gmail.com](mailto:abdulghaffaransari9@gmail.com) 

---

## License

This project is licensed under the MIT License. See `LICENSE` for more details.

---

## Contribute

We welcome contributions to improve the **VIRTUAL-CARE-ASSISTANT**. Fork the repository, create a feature branch, and submit a pull request with your changes!