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
```

### 2. Creating a Processing Node (`process_values`)

We define a Python function that will act as our single node, named `"processor"`. This function takes the current `state` as input, performs some logic, and returns a dictionary with the updated state values.

Specifically, it:
1.  Calculates the sum of the numbers in `state['values']`.
2.  Creates a simple greeting message.
3.  Returns a dictionary containing the new `sum` and `greeting`.

### 3. Building the Graph

We use LangGraph's `StateGraph` class to build the workflow:
1.  **Instantiate the Graph**: We create an instance of `StateGraph`, passing our `AgentState` as the state definition.
2.  **Add a Node**: We add our `process_values` function as a node named `"processor"`.
3.  **Set Entry and Exit Points**: Since this is a single-node graph, we set the entry point (`set_entry_point`) and the finish point (`set_finish_point`) to our `"processor"` node.


### 4. Compiling and Running the Application

1.  **Compile**: The `StateGraph` is compiled into an executable `app` using the `.compile()` method.
2.  **Invoke**: We call the compiled `app.invoke()` with an initial state (a dictionary containing the list of `values`).
3.  **Print Results**: The final state, after the graph has finished running, is printed to the console.

---

## 🚀 Usage

To run this demonstration, follow these steps:

1.  **Prerequisites**: Ensure you have Python 3.8+ installed.

2.  **Installation**: Install the required libraries.
    ```bash
    pip install langgraph langchain_core
    ```

3.  **Execution**: Open the notebook and run all the cells.

---

## 📊 Expected Output

When you invoke the application with the sample data `{'values': [10, 20, 5]}`, the final state printed will be:

```
{'values': [10, 20, 5], 'sum': 35, 'greeting': 'Hello from the processor!'}
```
