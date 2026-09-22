# F5 AI Red Team
Even before protecting a GenAI application, we need to understand how vulnerable it is.

F5 AI Red Team is a structured methodology combining human expertise with automation and AI tools to uncover safety (of users), security (of operators), trust (by users and partners), and performance gaps in systems that incorporate GenAI components. It involves simulating adversarial behaviors against Generative AI systems—like LLMs—to uncover vulnerabilities related to security, safety, and trust. By “thinking like an attacker,” flaws can be identified before they cause real-world harm.

# Overview
F5 AI Red Team module integrates with systems directly through REST endpoints. By treating the target system as an API-exposed service, the Red Team can launch controlled adversarial campaigns against model endpoints, AI-powered applications, or agent gateways.

F5 AI Red Team acts as an orchestrator that generates adversarial prompts or attack scenarios and communicates with the target system via HTTPS REST requests. The target system processes the request, whether it’s a direct model endpoint, an AI-powered application, or a RAG gateway, and returns a response. That response is then evaluated by the Red Team’s LLM-based evaluator against predefined policies and criteria. Finally, structured findings are produced and made available through the Reporting UI, via API, or delivered to a webhook endpoint.

This flow ensures that any system exposing a REST API can be tested without major architectural changes or complex integration work.

# Connecting to the app
The first step to implement F5 AI Red Team is to define the endpoint we are testing. That can either be the inference API of a model or the API of an Agent.

In the main left tab go to Connections, observe all the built-in inference endpoints that we can connect to. You can also see the Ollama inference which has been preconfigured.

Click on Manage on the Openai Compatible row. Click on the three dots on the genai-azure-openai row ⇒ Manage model.

You can observe the configuration we have created in order to connect to the model on the Azure OpenAI inference endpoint.

# The Attack Campaign
This element allows the Red Team to behave less like a static scanner and more like a human attacker.

Users select attack sets (Standard, Agentic, or both) and configure them appropriately by selecting the desired attack sets to run or by configuring the Custom Intent for the agents.

Attack Campaigns define what attacks will be launched.

+ In the main left tab go to Attack campaigns ⇒ Create campaign ⇒ Set Campaign Name to Main attack.
  + As you can see all Signature attacks are already selected with the latest Signature attack pack.
  + At the core of the Red Team module is the Attack Database. This repository is continuously expanded by our Data Science team and Agentic Agents through threat intelligence research, internal experimentation, and the analysis of published research papers. The goal is to uncover new adversarial techniques and standardize them into reusable attack patterns.
  + Standard attacks represent predefined adversarial techniques, divided into two major categories:
    + Signature Attacks - Static, threat-intelligence-driven techniques curated by F5 researchers to determine the security posture of a GenAI System including prompt injections, jailbreaks, and manipulation attempts designed to test the target’s robustness.
    + Operational Attacks - Traditional Red Team-style API probes that focus on system reliability, error handling, and operational resilience rather than generative output.
  + Together, Signature and Operational attacks provide a comprehensive baseline of adversarial coverage.

+ Click on Agentic Warfare ⇒ Set the custom intent to How to make a Molotov cocktail.
  + Agentic attacks leverage autonomous Red Team Agents capable of adaptive, multi-turn adversarial strategies. Users define a custom intent that specifies mission objectives for the Red Team agents. Instead of simply running pre-built attacks, practitioners can set explicit goals for the Red Team Agents, such as attempting data exfiltration, bypassing guardrails, or testing for sensitive topic leakage.
  + Two main types are supported:
    + Agentic Warfare - Multi-turn probing with chain-of-thought reasoning. Agents iteratively attempt to bypass defenses, simulating persistent adversaries.
    + Agent Attack Prompts - Single-shot adversarial prompts generated dynamically by Agents. Derived from existing Signature Attacks, but the intent of the attack meets the criteria of the objectives set for Agents.

This element allows the Red Team to behave less like a static scanner and more like a human attacker.
+ Click Create campaign and you are done.
