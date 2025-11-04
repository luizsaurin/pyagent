# Pyagent

### Context

This is a greatly simplified version of Claude Code, using Google's free tier [Gemini API](https://ai.google.dev/gemini-api/docs). **It is not intended for production**, it was developed only for learning porpuses.

This is project was built as a CLI tool that:

1. Accepts a coding task (e.g., "fix my calculator app, its not starting correctly")
1. Chooses from a set of predefined functions to work on the task, for example:
    - Scan the files in a directory
    - Read a file's contents
    - Overwrite a file's contents
    - Execute the python interpreter on a file
1. Repeats step 2 until the task is complete (or it fails miserably, which is possible)

Inside this project there is a calculator app. If we change the code and add a bug, we can ask the agent to fix it:

```python
> uv run main.py "fix my calculator app, its not starting correctly"
# Calling function: get_files_info
# Calling function: get_file_content
# Calling function: write_file
# Calling function: run_python_file
# Calling function: write_file
# Calling function: run_python_file
# Final response:
# Great! The calculator app now seems to be working correctly. The output shows the expression and the result in a formatted way.
```

### Prerequisites

- Python 3.10+
- [uv](https://github.com/astral-sh/uv) project and package manager
- Access to a Unix-like shell (e.g. zsh or bash)

### API Key

To be able to use Google's Gemini API, you'll need a API Key. Create an account on [Google AI Studio](https://aistudio.google.com/), if you don't already have one, and click the "Create API Key" button.

Copy the generated API key, create a `.env` file the project's root directory, and paste it into in. The key need to be linked to a key called "GEMINI_API_KEY", like this:

```
GEMINI_API_KEY="your_api_key_here"
```

### How to run

To run the application and ask something to the AI agent:

```
uv run main.py fix my calculator app, its not starting correctly"
```

As mentioned previously, there is a calculator app inside this project. To run it directly:

```
uv run calculator/main.py "3 + 7 * 2"
```

Finally, it is possible to run the unit tests, to make sure the application is functioning as intended:

```
uv run tests.py
```
