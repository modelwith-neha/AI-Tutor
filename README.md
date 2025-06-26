# AI-Tutor
Hackathon project - To create a Data Science AI tutor with GPU acceleration knowledge as well. Created a semi-socratic, game based tutor which has flashcards , game mode and point system to interest you.
🧠 M^6 AI Tutor: Data Science & GPU Acceleration Assistant

Overview

M^6 AI Tutor is an interactive, gamified tutor system designed for students and professionals exploring Data Science and GPU Acceleration. It uses:
	•	RAG (Retrieval-Augmented Generation) with a FAISS vector index
	•	LLM fallback (Falcon-7B-Instruct) for poor RAG results
	•	Interactive game modes: flashcards, quizzes, and coding puzzles

⸻

Features

🔍 Tutor Mode
	•	Ask any Data Science or GPU-related question
	•	Smart response via RAG over curated URLs (cuDF, RAPIDS, CUDA, pandas, sklearn, etc.)
	•	Fallback to LLM (Falcon-7B-Instruct) if RAG yields poor results
	•	Automatic polishing of RAG answers
	•	Related question suggestions and GPU benchmark graphs (plotly)

🎮 Game Mode
	•	Flashcards to review core concepts (e.g., CUDA, cuDF)
	•	Quizzes with multiple-choice questions to earn points
	•	Coding Puzzle: Convert CPU (pandas) code to GPU (cuDF) and simulate speedup

⸻

How it Works

1. RAG Pipeline
	•	URLs are scraped using BeautifulSoup
	•	Text is chunked, embedded with SentenceTransformers
	•	Indexed via FAISS
	•	User queries retrieve top-K chunks for context

2. Fallback with Falcon-7B
	•	If no good RAG content is found, a helpful prompt is passed to Falcon-7B
	•	LLM answers are optionally followed with a documentation link

3. Plotting Benchmarks
	•	When queries involve GPU/benchmarking, a dynamic CPU vs GPU plot is shown

⸻

Installation

pip install gradio torch transformers sentence-transformers faiss-cpu beautifulsoup4 requests plotly

Use faiss-gpu if you want GPU acceleration for indexing.

⸻

File Structure

📁 DataSci-GPU-Tutor/
├── tutor_app.py              # Full Python app (this script)
├── chunks.pkl                # Cached scraped chunks
├── faiss.index               # FAISS vector index
├── custom_urls.txt           # List of RAG URLs


⸻

Run the App

python tutor_app.py

It will launch a Gradio web app with two tabs:
	•	Tutor Mode: Ask questions
	•	Game Mode: Flashcards | Quiz | Coding Puzzle

⸻

Future Enhancements
	•	Chat-style UI
	•	User auth + progress tracking
	•	More advanced quizzes with explanations
	•	Upload your own notes for RAG

⸻

Credits
	•	Falcon-7B-Instruct by TII UAE
	•	SentenceTransformers: all-MiniLM-L6-v2
	•	Gradio UI
	•	Plotly for charts
	•	FAISS for fast similarity search
