# 🧠 AI Code Style Analyzer (Experimental)

**Author:** D0up4       
**Last Updated:** 06/2025  
**Project Type:** Python Tool / Code Analysis / Developer Tools

---

## 📘 Description

This is a lightweight Python tool that performs a **heuristic analysis** on `.py` source files to estimate whether they may have been **AI-generated** (e.g., via ChatGPT, Copilot, etc.). It works by analyzing coding patterns such as:

- Comment density
- Naming conventions (e.g., `camelCase` vs `snake_case`)
- Use of generic function or variable names
- Presence of overly broad exception handling

🔍 **Note:** This tool is **not definitive**. It gives an educated guess based on observable patterns — helpful for fun, learning, or code review exploration.

---

## ⚙️ Features

- 📊 Analyzes comment-to-code ratio
- 📛 Flags use of common AI-style naming patterns
- 🎯 Calculates consistency of naming style
- 🧠 Produces an "AI-likeness" score (0–4)
- 💬 Human-friendly output with context
- 🐍 Pure Python — no external dependencies

---

## 🚀 Usage

### 1. Clone or Download the Script

```bash
git clone https://github.com/D0up4/ai-code-style-analyzer.git
cd ai-code-style-analyzer
