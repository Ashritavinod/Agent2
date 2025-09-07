# Simple LangGraph Workflow Demo 📝

This notebook provides a basic, hands-on demonstration of how to create a simple workflow using **LangGraph**. It showcases the fundamental concepts of defining a state, creating a processing node, and compiling the graph into an executable application.

---

## 📜 Overview

The goal of this project is to illustrate the simplest possible LangGraph structure: a graph with a single node. This node takes a list of numbers as input, calculates their sum, adds a greeting message, and returns the updated state.

This example is perfect for understanding the core components of LangGraph:

* **State Management**: How to define and pass data through the graph.
* **Nodes**: The fundamental units of computation.
* **Graph Construction**: The process of assembling nodes into a coherent workflow.

---

## ⚙️ How It Works

The workflow is straightforward and consists of the following steps:

### 1. Defining the State (`AgentState`)

First, we define a state object using Python's `TypedDict`. This `AgentState` dictionary holds all the data that will be passed between nodes in our graph. For this demo, it contains:
* `values`: A list of numbers to be processed.
* `sum`: The calculated sum of the numbers (optional, added by the node).
* `greeting`: A message string (optional, added by the node).

```python
from typing import List, TypedDict

class AgentState(TypedDict):
    values: List[int]
    sum: int
    greeting: str
