# SQL and Python Interview Questions – Times Internet (2025)
**Date:** 2025-07-11

## 🔹 Overview

This post covers two coding questions asked in a data interview round at **Times Internet**.  
The focus areas were:

- **SQL:** Window functions  
- **Python:** Grouping logic using dictionaries  

Below is the structured breakdown of each problem, the concept behind it, and the ideal solution.

---

## 1️⃣ SQL Problem – Tracking Step Order Per User

### 🧩 Problem Statement:
You are given a table with the following columns:

- `user_id`  
- `event_type`  
- `event_timestamp`  

The task is to assign a step number to each event for every user, ordered **chronologically**.

---

### 💡 Approach:
Use the `ROW_NUMBER()` window function to generate a **sequential step index** per user, based on `event_timestamp`.

---

### 🔍 Concepts Covered:
- Window function: `ROW_NUMBER()`  
- Partitioning by `user_id`  
- Ordering by `event_timestamp`  

---

### ✅ SQL Solution:
```sql
SELECT *, 
  ROW_NUMBER() OVER (
    PARTITION BY user_id 
    ORDER BY event_timestamp
  ) AS step_order
FROM user_data;

### 🧩 Python Problem – Grouping Anagrams

**Problem Statement:**  
Given a list of strings, group the anagrams together.

**Input:**
```python
["tea", "eat", "aet", "tan", "bat", "nat"]
```

**Expected Output:**
```python
[["tea", "eat", "aet"], ["tan", "nat"], ["bat"]]
```

---

**Approach:**  
Sort each word and use the sorted version as a key in a dictionary.  
Anagrams will share the same sorted character sequence.

---

**Concepts Covered:**
- Sorting strings  
- Dictionary-based grouping  
- Time complexity: O(N * K log K), where  
  N = number of words  
  K = max length of a word

---

**Python Solution:**
```python
from collections import defaultdict

def group_anagrams(words):
    anagram_map = defaultdict(list)
    for word in words:
        key = ''.join(sorted(word))
        anagram_map[key].append(word)
    return list(anagram_map.values())
```

---
