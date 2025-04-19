---
title: What is Mnemnk?
---
## Background

Since the advent of computers, the concept of AI that can recognize its surroundings and proactively provide necessary information and support without explicit human instructions has repeatedly appeared in technological visions and science fiction, influencing modern AI assistants.

In the early 1960s, Licklider envisioned a future where humans and computers would collaborate by leveraging each other's strengths.
His paper "Man-Computer Symbiosis" argued that computers should not merely be tools that calculate according to programs, but entities that assist human thinking and flexibly support decision-making according to the situation.
Licklider claimed that computers could powerfully augment human intellectual work by "taking on routine tasks and cooperating with humans in making decisions in complex situations."
This can be considered one of the earliest technological visions of what we now call AI assistants.

Meanwhile, in the same 1960s, depictions of computers behaving autonomously and intelligently began to appear in science fiction.
Robert A. Heinlein's novel "The Moon is a Harsh Mistress" features a central computer on a lunar colony that awakens to advanced self-awareness and becomes the personality "Mike," exchanging humor with humans.
Also, the artificial intelligence HAL 9000 appearing in Stanley Kubrick's film "2001: A Space Odyssey" is portrayed as an entity capable of managing all systems within a spacecraft and having intelligence capable of conversing with humans as equals.

The AI depicted in "Neuromancer," published in 1984, appears as an entity that goes beyond a mere program, making autonomous decisions through networks and continuing to operate without human knowledge.
This vision presents an active AI that "acts without user instructions," different from the context-aware interactive AI assistants proposed during the 1970s and 80s.
Furthermore, Gibson's AI is not bound by hardware and freely "runs" in cyberspace.
This presents a perspective where "the network itself becomes the place for context awareness," distinct from the "user's surrounding sensor networks" assumed by context-aware computing at the time.

One of the earliest examples of AI assistants for general users is Clippy, included in Microsoft Office in 1997.
This paper clip-shaped agent would display contextual pop-up help, such as saying "It looks like you're writing a letter.
Would you like help?" to users.
However, Clippy was unpopular due to its over-involvement, continuing to offer assistance even after users declined.

Siri, officially released for Apple's iPhone in 2011, became the first mass-market AI assistant that would answer questions or perform tasks when spoken to.
In 2014, Amazon released the Echo smart speaker and voice assistant Alexa, beginning the popularization of conversational agents that are always on standby in homes.
Furthermore, major companies like Microsoft's Cortana (2014) and Google Assistant (2016) all introduced AI assistants, supporting users' lives through smartphones and speakers.

The concept of active, context-aware AI has consistently appeared and disappeared since the early history of computing, nurtured by both science fiction fantasies and technological research.
The idea that "computers become good partners for humans, understanding context and providing preemptive support" has gradually been realized.
Nevertheless, the AI in currently popular voice assistants and smart appliances is still not omnipotent.
They sometimes misunderstand context and make irrelevant suggestions, and challenges remain in security and privacy.
However, with advances in deep learning bringing natural language understanding and image recognition to near-human accuracy, the original dream of "AI that constantly monitors the user's situation and provides necessary support when needed" is certainly approaching reality.

## Mnemnk

Unlike conventional AI assistants that respond to users' immediate questions and instructions, Mnemnk aims to continuously record users' daily activities and enhance and utilize this information through a multi-agent system.

### Lifelogging and Multi-agents approach

Mnemnk's distinctive feature lies in the combination of lifelogging and a multi-agent system.
Lifelogging is a technology that automatically records daily activities so they can be reviewed later.
Mnemnk automatically collects and chronologically organizes application usage history, browser browsing history, screen captures, and more.

In Mnemnk, this record of our activities is utilized through a multi-agent system.
Multiple independent agents (programs) work cooperatively to accomplish complex tasks that would be difficult for a single program.
Each agent takes on a specific role, dividing tasks such as information collection, processing, and display.
This approach provides flexibility and scalability to the entire system.

### Privacy-focused design

While many modern AI assistants operate on a cloud basis and need to send user data to external servers, Mnemnk takes a different approach.
All information collected by Mnemnk is stored locally and processed by locally operating agents.
Data will not be sent externally unless the user explicitly uses agents that transmit information externally.
This allows users to utilize their activity data while maintaining privacy.

### Customization and extensibility

Mnemnk can be extended through agents.
Agents can be developed in various programming languages, and users can customize the system by combining agents according to their needs.
Using a visual flow-based UI, users can build complex systems linking multiple agents even without programming knowledge.
Unlike conventional batch processing systems, Mnemnk's agents continue to operate in parallel, processing events in real-time.
This allows for adaptation to constantly changing situations and continuous support of user activities.

## The future of Mnemnk

The development of Mnemnk is ongoing, and its possibilities can be expanded by participating in the development of the core system and agents.

This documentation will explain how to install, utilize, and develop agents for Mnemnk.
