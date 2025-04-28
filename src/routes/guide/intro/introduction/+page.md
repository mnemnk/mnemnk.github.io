---
title: What is Mnemnk
---

Mnemnk is a personal lifelogging platform that automatically records user activities and enhances them through a multi-agent system.
Here are the main features of this application.

## Features

### Automatic Activity Recording

The primary feature of Mnemnk is the combination of lifelogging and a multi-agent system.
It automatically collects and chronologically organizes application usage history, browser browsing history, screen captures, and more.
This allows users to review their activities later.

### Privacy-Focused

While many modern AI assistants operate on a cloud basis and need to send user data to external servers, Mnemnk stores all information locally and processes it with locally operating agents.
Data will not be sent externally unless the user explicitly uses agents that transmit information externally.

### Agent-Based Extensibility

System extensibility is implemented through agents.
Agents can be developed in various programming languages.
By combining various agents using a visual flow-based UI, users can build complex systems of interconnected agents without programming knowledge.

## Core Functions

### Agent Communication

Mnemnk agents have input and output channels through which they communicate with each other.
When an agent receives data, it processes it and generates output as needed.
Each agent operates independently and runs concurrently without blocking other agents' processes.

### Flows

A collection of placed and connected agents is called a "flow."
Multiple flows can be managed, and each flow continues to operate even in the background.

### Boards

Boards help reduce tight coupling between agents and enable the construction of large-scale systems spanning multiple flows.

## Key Agents

Mnemnk provides various agents:

- **Core Agents**: Unit Input, Boolean Input, Counter, Memory, Display Data, Debug Data, etc.
- **Database Agents**: Event Database, Database Insert, Database Select, etc.
- **Script Agents**: Rhai Expression, Template String, etc.
- **Lifelogging Agents**: Application, Screen, API, and others

## Use Cases

Mnemnk can be used not only as a lifelogging tool but also for various automation tasks, such as:

- Recording and analyzing daily activities
- Connecting browser history with work content
- Automating specific tasks using custom agents
- Integrating information from multiple data sources

Mnemnk is open-source, allowing users to customize and extend it according to their needs.
