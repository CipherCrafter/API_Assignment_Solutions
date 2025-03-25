# API Autocomplete Extraction

This repository contains a solution to extract **all possible names** from an **undocumented autocomplete API** running at `http://35.200.185.69:8000`. The approach involves systematically querying the API, handling constraints, and optimizing the extraction process.

---

## 📌 Problem Statement

The goal is to discover how the API works and extract all available names through its autocomplete system. Given the unknown constraints, this requires:

- Exploring the API's behavior.
- Handling rate limits or restrictions.
- Efficiently querying the API for maximum name coverage.
- Documenting findings and optimization strategies.

---

## 🚀 Solution Approach

### 1️⃣ API Exploration
- The API provides an **autocomplete endpoint** at:  
`/v1/autocomplete?query=<string>`
- It returns **suggested names** based on the provided `query` prefix.
- Sending different prefixes results in **different sets of names**.
- There is no explicit endpoint to list **all** names, so an iterative discovery approach is required.

### 2️⃣ Query Strategy
To extract names efficiently, the program:
1. **Starts with Single-Character Queries** (`a`, `b`, `c`, …, `z`, `0`, `1`, …, `9`).
2. **Expands Using Prefixes**: If a prefix returns valid names, explore further (`aa`, `ab`, `ac`, ...).
3. **Optimizes with Heuristics**:
 - Stops expanding queries when no new names are found.
 - Avoids redundant or unproductive queries.
4. **Handles API Limitations**:
 - Implements **rate limit handling** (delays between requests).
 - Uses **multi-threading** to optimize query execution.

### 3️⃣ Handling Rate Limits & Constraints
- **Adaptive Request Timing**: Introduced delays to prevent throttling.
- **Parallel Requests**: Used multiprocessing/threading where possible.
- **Efficient Query Expansion**: Avoids unnecessary requests by tracking visited prefixes.

---

## 📊 Results

| Version | API Requests Made | Names Extracted |
|---------|-----------------|----------------|
| **V1**  | 12,947          | 18,632        |
| **V2**  | 3,122           | 13,730        |
| **V3**  | 8,516           | 12,517        |

- **Version 1** retrieved the most names but required more requests.
- **Version 2** was the most efficient in terms of requests.
- **Version 3** had more complexity, requiring additional logic for extraction.

---

## 📂 Repository Structure

📁 API_Assignment_Solutions │── 📜 api-assignment-V1.ipynb # Code for Version 1 │── 📜 api-assignment-V2.ipynb # Code for Version 2 │── 📜 api-assignment-V3.ipynb # Code for Version 3 │── 📜 version1_extracted_names.txt # Names extracted from V1 │── 📜 version2_extracted_names.txt # Names extracted from V2 │── 📜 version3_extracted_names.txt # Names extracted from V3 │── 📜 README.md # Documentation
