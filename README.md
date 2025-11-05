# OCR to Structured Markdown Table Using Llama Vision and Streamlit

This project provides a modern way to extract text from images including both printed text and handwritten notes and convert it into a clean Markdown table. Instead of relying on traditional OCR methods that often miss handwritten or uneven text, this system uses Groq-powered Llama vision models to understand the content more intelligently and reconstruct it in a structured format.

The process works by splitting the uploaded image into overlapping horizontal slices. Each slice is passed through the Llama vision model to ensure that even partial text, unevenly placed handwriting, and mixed formatting are captured accurately. Once all slices are processed, a second language model reviews the combined text, removes duplicates caused by overlapping sections, resolves inconsistent readings, and then produces a polished table that represents the contents of the original document as clearly as possible.

The entire workflow runs through a simple Streamlit interface, making the experience interactive and easy to use even for non-technical users.

## How the Application Works

Once you upload an image, the app quietly handles a few important steps in the background:

The image is resized for clarity.
It is then sliced into multiple overlapping horizontal strips to avoid losing information that stretches across boundaries.
Each strip is processed individually using a Llama vision model hosted via Groq’s API.
All extracted text segments are gathered and handed to a second LLM that cleans, merges, and formats the final output.
The formatted table appears on screen, ready to review or download.

This design helps ensure accuracy while improving the reliability of text recognition, especially when handling handwritten notes, scans of notebook pages, receipts, and messy or mixed-format images.

## Technology Behind the System

The core functionality relies on:

Groq Llama Vision models for OCR interpretation
A second Llama language model for deduplication and formatting
Streamlit for the user interface
Pillow for image preprocessing
LangChain to orchestrate model calls
dotenv to securely load API keys

In simple terms, this application blends vision AI and language AI to produce structured information from unstructured images.

## How to Run the Application

To run this project on your machine, follow these steps:

Make sure you have Python installed (version 3.9 or later works best).
Clone this project or copy the source code into a working folder.
Install the required Python packages by running:
pip install streamlit python-dotenv Pillow langchain-groq

Create a .env file in the project directory and add your Groq API key:
GROQ_API_KEY=your_key_here

Start the application from your terminal:
streamlit run your_script_name.py

Once Streamlit launches in your browser, simply upload an image and wait for the processing to complete. The final Markdown-formatted table will appear automatically, and you can download it if you wish.

No GPU or special hardware is required, since all model inference is done through the Groq API.
