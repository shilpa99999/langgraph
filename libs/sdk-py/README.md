# LangGraph Python SDK

This repository contains the Python SDK for interacting with the LangGraph Platform REST API.

## Quick Start

To get started with the Python SDK, [install the package](https://pypi.org/project/langgraph-sdk/)

```bash
pip install -U langgraph-sdk
```

You will need a running LangGraph API server. If you're running a server locally using `langgraph-cli`, SDK will automatically point at `http://localhost:8123`, otherwise
you would need to specify the server URL when creating a client.

```python
from langgraph_sdk import get_client

# If you're using a remote server, initialize the client with `get_client(url=REMOTE_URL)`
client = get_client()

# List all assistants
assistants = await client.assistants.search()

# We auto-create an assistant for each graph you register in config.
agent = assistants[0]

# Start a new thread
thread = await client.threads.create()

# Start a streaming run
input = {"messages": [{"role": "human", "content": "what's the weather in la"}]}
async for chunk in client.runs.stream(thread['thread_id'], agent['assistant_id'], input=input):
    print(chunk)
```

## About the Maintainer

This project is currently maintained by Shilpa Kuppili, a Software Engineer with 7+ years of experience developing scalable, enterprise-grade applications. Shilpa is proficient in Python, Java, and cloud platforms like AWS, and is dedicated to delivering high-impact solutions.

-   **GitHub**: Shilpa Kuppili
-   **LinkedIn**: [Shilpa Kuppili](https://linkedin.com/in/shilpa-kuppili-a80ba2126)
-   **Email**: shilpakp333@gmail.com