# AppWorld Experiments

This repository provides the full setup and instructions for running AppWorld experiments and reproducing the reported metrics, including offline and online adaptation with ACE.

> **⚠️ Important:**  
> Do **NOT** install this repository using `pip install appworld`.  
> This version includes custom modifications and must be installed **from source**.

## 1. Environment Setup

Follow these steps exactly. Skipping steps may cause missing-file errors or silent failures.

### 1.1 Install Git LFS
```bash
git lfs install
```

### 1.2 Clone the repository
```bash
git clone https://github.com/Alex-q-z/ace-appworld.git ace-appworld
cd ace-appworld
```

### 1.3 Install AppWorld from source
```bash
pip install -e .
appworld install --repo
```

### 1.4 Install appworld_experiments from source
```bash
cd experiments
pip install -e .
cd ..
```

### 1.5 Fetch data
```bash
appworld download data
```

### 1.6 Install jsonnet (required for configs)
```bash
pip install jsonnet
```

## 2. Configure Experiment Paths

Replace ```PATH``` with the absolute path to your working directory (e.g. ```/home/user/projects```).
```bash
export APPWORLD_EXPERIMENT_PROMPTS_PATH=PATH/ace-appworld/experiments/prompts
export APPWORLD_EXPERIMENT_CONFIGS_PATH=PATH/ace-appworld/experiments/configs
export APPWORLD_EXPERIMENT_CODE_PATH=PATH/ace-appworld/experiments/code
```

## 3. Configure API Keys

You may provide a Together API key, a SambaNova API key, or an OpenAI API key, depending on which model or client is being used for inference.
```bash
export TOGETHER_API_KEY=YOUR_API_KEY_HERE
export SAMBANOVA_API_KEY=YOUR_API_KEY_HERE
export OPENAI_API_KEY=YOUR_API_KEY_HERE
```

## 4. Run Experiments

Example: run the AppWorld + ACE (online adaptation) experiment on the test-normal split
```bash
appworld run ACE_online_no_GT
```

## 5. Evaluate Results

After the run completes, compute aggregated metrics:
```bash
appworld evaluate ACE_online_no_GT test_normal
```

Here is an example of a generated evaluation report:
| type         | task_goal_completion | scenario_goal_completion |
|--------------|----------------------|---------------------------|
| aggregate    | 64.9                 | 51.8                      |
| difficulty_1 | 86.0                 | 79.0                      |
| difficulty_2 | 77.1                 | 68.8                      |
| difficulty_3 | 36.5                 | 14.3                      |