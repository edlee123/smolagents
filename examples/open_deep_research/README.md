# Open Deep Research

Welcome to this open replication of [OpenAI's Deep Research](https://openai.com/index/introducing-deep-research/)! This agent attempts to replicate OpenAI's model and achieve similar performance on research tasks.

Read more about this implementation's goal and methods in our [blog post](https://huggingface.co/blog/open-deep-research).


This agent achieves **55% pass@1** on the GAIA validation set, compared to **67%** for the original Deep Research.

## Setup

To get started, follow the steps below:

### Clone the repository

```bash
git clone https://github.com/huggingface/smolagents.git
cd smolagents/examples/open_deep_research
```

### Install dependencies

    Run the following command to install the required dependencies from the `requirements.txt` file:

    ```bash
    pip install -r requirements.txt
    ```

### Install the development version of `smolagents`

    ```bash
    pip install -e ../../.[dev]
    ```

If you anticipate making many code changes you can avoid installing/reinstalling, by setting:
```export PYTHONPATH=<smolagents_path>/smolagents/src/```

### Set up environment variables

The agent uses the `GoogleSearchTool` for web search, which requires an environment variable with the corresponding API key, based on the selected provider:
- `SERPAPI_API_KEY` for SerpApi: [Sign up here to get a key](https://serpapi.com/users/sign_up)
- `SERPER_API_KEY` for Serper: [Sign up here to get a key](https://serper.dev/signup)

Depending on the model you want to use, you may need to set environment variables.
For example, to use the default `o1` model, you need to set the `OPENAI_API_KEY` environment variable.
[Sign up here to get a key](https://platform.openai.com/signup).

> [!WARNING]
> The use of the default `o1` model is restricted to tier-3 access: https://help.openai.com/en/articles/10362446-api-access-to-o1-and-o3-mini


## Usage

Run the run.py script, as in:

```bash
python run.py --model-id "o1" "Your question here!"
```

Use the `--model-id` parameter to specify the model you want to use.  For OpenAI models, you can use model IDs like "o1".

To use a different OpenAI-compatible API endpoint, also specify the `--api-base` parameter:

```bash
python run.py --model-id "YOUR_MODEL_NAME" --api-base "YOUR_API_BASE_URL" "Your question here!"
```

Replace `"YOUR_API_BASE_URL"` with the base URL of your API endpoint, and `"YOUR_MODEL_NAME"` with the name of the model you want to use with that endpoint.

### Using a different search provider

You can choose between the "serper" (default) and "serpapi" search providers using the `--search-provider` argument. Make sure to set the corresponding environment variable (`SERPER_API_KEY` or `SERPAPI_API_KEY`) accordingly.

```bash
python run.py --search-provider "serper" "Your question here!"  # Uses SERPER_API_KEY (default)
python run.py --search-provider "serpapi" "Your question here!" # Uses SERPAPI_API_KEY