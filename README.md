# LLM OS
## Personal Workspace Fork

This repository contains an initial implementation of the LLM OS proposed by [Karpathy](https://twitter.com/karpathy/status/1723140519554105733).
He talks about it [in this tweet](https://twitter.com/karpathy/status/1723140519554105733), [this tweet](https://twitter.com/karpathy/status/1707437820045062561) and [this video](https://youtu.be/zjkBMFhNj_g?t=2535).

## The LLM OS philosophy
![llm-os](https://github.com/martintmv-git/llm_os/assets/101264514/6a6e1ce0-68ac-4041-83f2-b35e742a76ad)

- LLMs are the kernel process of an emerging operating system.
- This process (LLM) will solve problems by coordinating other resources (like memory or computation tools).
- The LLM OS Vision:
  - [X] It can read/generate text
  - [X] It has more knowledge than any single human about all subjects
  - [X] It can browse the internet
  - [X] It can use existing software infra (calculator, python, mouse/keyboard)
  - [ ] It can see and generate images and video
  - [ ] It can hear and speak, and generate music
  - [ ] It can think for a long time using a system 2
  - [ ] It can “self-improve” in domains
  - [ ] It can be customized and fine-tuned for specific tasks
  - [X] It can communicate with other LLMs

[x] indicates functionality that is implemented in the LLM OS app

## Running the LLM OS:

> Note: Fork and clone this repository if needed

### 1. Create a virtual environment

```shell
mkdir llm_os_env
cd llm_os_env
conda create --prefix ./env python=3.11    # choose python version
conda activate ./env
```

### 2. Install libraries

```shell
pip install -r requirements.txt
```

### 3. Export credentials

- Out initial implementation uses GPT-4o, so export your OpenAI API Key

```shell
export OPENAI_API_KEY=***
```

- To use Exa for research, export your EXA_API_KEY (get it from [here](https://dashboard.exa.ai/api-keys))

```shell
export EXA_API_KEY=xxx
```

### 4. Run PgVector

We use PgVector to provide long-term memory and knowledge to the LLM OS.
Please install [docker desktop](https://docs.docker.com/desktop/install/mac-install/) and run PgVector using either the helper script or the `docker run` command.

- Run using a helper script

```shell
./pgvector/run_pgvector.sh
```

- OR run using the docker run command

```shell
docker run -d \
  -e POSTGRES_DB=ai \
  -e POSTGRES_USER=ai \
  -e POSTGRES_PASSWORD=ai \
  -e PGDATA=/var/lib/postgresql/data/pgdata \
  -v pgvolume:/var/lib/postgresql/data \
  -p 5532:5432 \
  --name pgvector \
  phidata/pgvector:16
```

### 5. Run the LLM OS App

```shell
streamlit run app.py
```

- Open [localhost:8501](http://localhost:8501) to view your LLM OS.

<hr>

#### Original repository 👉🏻 https://git.new/llm-os
