# 🚀 DeepSeek-R1 Cloud Chat Engine

An industry-grade, cloud-optimized web application that runs a distilled DeepSeek-R1 reasoning model. Built using Hugging Face Transformers and Gradio, this architecture implements background multi-threading and real-time regex sanitization to deliver low-latency, token-by-token text streaming with an interactive, animated user interface.

---

## ✨ Core Features

* **Asynchronous Token Streaming:** Spawns background worker threads using Python's `threading` library alongside `TextIteratorStreamer` to generate responses word-by-word without freezing the user interface.
* **Real-Time Thought Filtering:** DeepSeek-R1 outputs internal monologues within `<think>` tags. This engine dynamically intercepts and strips out these reasoning tokens on-the-fly, displaying a clean `🤖 Thinking...` status animation until the final response is ready.
* **Session Context Memory:** Automatically retains conversation history within individual sessions by managing structural context arrays, passing past dialogue loops back to the model with correct role designations (`user` vs. `assistant`).
* **Stricter Guard Persona:** Features an advanced system prompt configuration that keeps the reasoning engine grounded, preventing the model from overanalyzing simple inputs (like "Hi") or looping over its own persona.
* **Zero-Local Cloud Footprint:** Built to deploy and execute entirely on cloud infrastructure using a free Google Colab T4 GPU instance.

---

## 🛠️ Tech Stack

* **LLM Core:** [DeepSeek-R1-Distill-Qwen-1.5B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B)
* **UI Frontend:** Gradio (`gr.ChatInterface` & `gr.Chatbot`)
* **Inference Engine:** Hugging Face `transformers` & `accelerate`
* **Deep Learning Runtime:** PyTorch (`torch`)
* **Concurrency:** Python Native `threading.Thread`



