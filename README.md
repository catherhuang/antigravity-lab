## GEP x Google Cloud Agent Platform Workshop (July 17, 2026)

# Antigravity + Agent Platform: From Development to Production

Welcome to the ** Google Cloud Agent Platform Workshop**! This repository guides you through leveraging **Google Antigravity** as an autonomous assistant to accelerate the entire agent development lifecycle on Google Cloud. 

You will learn how to initialize an interactive Antigravity CLI (`agy`) session, use natural language to gather requirements, and let the agent orchestrate project scaffolding, evaluation, and deployment via the **Agents CLI in Agent Platform**.

---

## Table of Contents
1. [Overview](#overview)
2. [Before You Begin](#before-you-begin)
   - [Accessing Antigravity](#accessing-antigravity)
   - [Authenticate](#authenticate)
   - [Set Environment Variables](#set-environment-variables)
   - [Install Agents CLI](#install-agents-cli)
3. [Getting Started with Antigravity](#getting-started-with-antigravity)
   - [Download](#download)
   - [AGY 2.0 Desktop](#agy-20)
   - [Antigravity CLI (agy)](#antigravity-cli)
   - [Introduction to Slash Commands](#introduction-to-slash-commands)
4. [Create Your Agent Project](#create-your-agent-project)
   - [Step 1: Define the Goal](#step-1-define-the-goal)
   - [Step 2: Refine Requirements](#step-2-refine-requirements)
   - [Step 3: Review the Implementation Plan](#step-3-review-the-implementation-plan)
   - [Step 4: Evaluation & Deployment](#step-4-evaluation--deployment)
   - [Step 5: Verify the Deployment](#step-5-verify-the-deployment)
5. [Register with Gemini Enterprise](#register-with-gemini-enterprise)
6. [Conclusion & Key Benefits](#conclusion)

---

## Overview

This walkthrough highlights how **Google Antigravity** manages autonomous planning, generates artifacts for your approval, and executes asynchronous cloud deployments directly to **Agent Runtime**—allowing you to simultaneously run local validation and evaluation suites while your production infrastructure spins up.

| Google Antigravity | Agents CLI in Agent Platform |
| :---: | :---: |
| _Autonomous AI Assistant & Planning Agent_ | _Scaffolding, Evaluation & Deployment Engine_ |

---

## Before You Begin

### Accessing Antigravity
1. Follow installation instructions: visit [antigravity.google](https://antigravity.google/) and download **Antigravity 2.0**.
2. Log in using **YOUR** Google Cloud Credentials:
   * **Choose:** *"Use Google Cloud project instead"*
   * Log in with your **Google Cloud Identity**.
   * Select your **Google Cloud project-id** (with billing enabled) and your desired **location (region)**.

### Authenticate
Ensure your local environment is authenticated with Google Cloud:
```bash
gcloud auth login
gcloud auth application-default login
```

### Set Environment Variables
Set up your active project details:
```bash
export GOOGLE_CLOUD_PROJECT="YOUR_PROJECT_ID"
export GOOGLE_CLOUD_LOCATION="us-central1"
```

### Install Agents CLI
The **Agents CLI** is a CLI and skills package for building, evaluating, and deploying AI agents on Google Cloud using Google's **Agent Development Kit (ADK)**. 
While you primarily interact with the Antigravity CLI (`agy`), Antigravity relies on Agents CLI under the hood to handle scaffolding, evaluation, deployment, and observability.

Install the CLI and context-aware skills for Antigravity:
```bash
uvx google-agents-cli setup
```
> 💡 *Trouble installing? Check the official [Antigravity CLI Installation Docs](https://antigravity.google/docs/cli/install) for alternative setups.*

---

## Getting Started with Antigravity

### Download
Visit [antigravity.google/download](https://antigravity.google/download) and download the installer for your operating system. Launching the installer configures both the **Antigravity desktop application (AGY 2.0)** and the bundled **`agy` CLI** on your machine.

### AGY 2.0
AGY 2.0 provides a high-level birds-eye view into the tasks your Antigravity agents execute. Within this UI, you can:
* Manage multiple workspaces.
* Oversee dozens of agents simultaneously.
* Interact with your codebase primarily through natural language instruction rather than manual coding.

### Antigravity CLI
To begin an interactive assistant session in your terminal, run:
```bash
agy
```

#### Login Flow
1. Select the **"Use a Google Cloud project"** option when prompted.
2. Complete the standard Google OAuth flow in your web browser.
3. Copy the authorized code and paste it back into the Antigravity CLI.
4. Select your **billing project** and **Google Cloud Location** (e.g., `global` or `us-central1`).
5. Confirm your completion of the login process.

#### Introduction to Slash Commands
Slash commands control your Antigravity session instantly:
* `/models` — View and switch active models.
* `/skills` — List the skills available to your active agent.
* `/planning` — Manually enter Planning Mode.
* `/artifact` — Open and inspect generated artifacts.
* `/tasks` — Monitor background execution and deployment tasks.

---

## Create Your Agent Project

Antigravity acts as an autonomous software engineer that gathers requirements, builds a plan, scaffolds the project, and deploys it leveraging **Gemini** and the **Agents CLI**.

### Step 1: Define the Goal
In your active `agy` session, describe what you want to build in natural language:
```text
# Use your own idea for agent!! 
"I want to build an agent that can tell me the weather"
```
Antigravity will automatically trigger the underlying Agent CLI workflow skill to kick off the project.

### Step 2: Refine Requirements
The agent will ask follow-up questions to narrow down the scope. Provide your detailed prototype goals:
```text
"I want to understand the current temperature, forecasting, and outfit recommendations. For the time being, let's just mock the APIs. I want this to be a prototype that we deploy to Agent Runtime."
```
> 🛡️ **Permission Request:** When Antigravity asks for permission to run `agents-cli scaffold create`, select **Option 3** to grant the agent permission to run subsequent `agent-cli` commands automatically.

### Step 3: Review the Implementation Plan
Instead of immediately outputting code, Antigravity enters **Planning Mode**.
1. Once the plan is ready, Antigravity notifies you that an artifact is ready for review.
2. Type `/artifact` to open and inspect the generated implementation plan.
3. If everything looks correct, select **Approve** to proceed.

### Step 4: Evaluation & Deployment
Once approved, Antigravity executes the plan, altering the scaffolded project files using `agents-cli scaffold enhance` to configure the Agent Runtime logic and trigger deployment in the background.

* **Check Status:** Monitor background tasks at any time by typing `/tasks`.
* **Local Testing:** While deploying, you can run tests locally:
  ```text
  "Can we test the agent while we’re waiting for it to deploy?"
  ```
  Antigravity will execute `agents-cli run` to verify the logic and display a successful local response.
* **Evals and Coverage:** Proactively generate validation suites:
  ```text
  "Let's be sure to have adequate test coverage for evals too."
  ```

### Step 5: Verify the Deployment
Once notified that the deployment task is complete, ask the agent where to find the live environment:
```text
"That's great news, where can I see the deployed agent?"
```
Antigravity will provide a **Google Cloud Console** link opening the **Agent Runtime playground environment**, allowing you to interact directly with your live agent.

---

## Register with Gemini Enterprise

Once your agent is successfully deployed to Agent Runtime, publish it to your wider enterprise organization:
```text
"This is great, could we also publish to Gemini Enterprise?"
```

---

## Conclusion

**Google Antigravity** empowers the next era of enterprise builders. By seamlessly orchestrating **Agents CLI** under the hood, it enables your organization to transform how agents are built, deployed, and managed on **Gemini Enterprise Agent Platform**.

Powered by **Gemini 3.5 Flash**, Antigravity delivers exceptional computational efficiency, rapid development cycles, and reduced operational costs for production-scale AI initiatives.

### Why It Matters:
* 🔒 **Built-in Safety:** Connects directly to the Agent Platform, keeping corporate data secure without exposure risks.
* 🎛️ **Centralized Control:** A single workspace to orchestrate and direct complex, multi-step agent workflows.
* 🔌 **Ecosystem Interoperability:** Natively leverages the Agents CLI, offering immediate enterprise-grade expertise on Google Cloud.
* ⚡ **Faster Execution:** Automates infrastructure setup so engineering teams can focus on building business logic quickly.
