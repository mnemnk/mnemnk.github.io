---
title: Agents
---

When discussing agents, one might initially think of intelligent AI agents capable of complex processing.

![](/images/guide/agents/chat-model-agent.png)

While this is certainly one type of agent, in Mnemnk the term encompasses a unified approach to handling various processes, from simple to sophisticated.

Examples range from basic agents that accept user input or display received data, to more complex ones that monitor active applications and output changes, or agents that receive events and store them in databases.

:::tip
The concept of "agents" as central to AI owes much to Marvin Minsky's influential work.
In his 1986 book "The Society of Mind"[^1], Minsky proposed the groundbreaking theory that human intelligence emerges from interactions between "many simple agents."
These agents, though individually capable of only simple processing and "mindless" on their own, collectively generate complex intelligent behavior through cooperation and competition.
This "society of agents" model forms the foundation of today's multi-agent systems and distributed AI.
:::

In Mnemnk, combining these various agents allows for building flows that perform complex processing.

![](/images/guide/agents/simple-chat-bot.png)

## Agent

Agents maintain independent internal states and operate asynchronously in parallel.
Let's explore agent functionality by building a simple flow with agents.

Agents can be placed on the flow by selecting their names from the Agents menu in the top right of the Agent page.
When merely placed, agents aren't yet active and appear dark and semi-transparent.

The following example shows the placement of `Integer Input`, `Memory`, and `Display Data` agents.

![](/images/guide/agents/first-agent-flow1.png)

### Config

Each agent can have settings appropriate to its type. For example, `Memory` can be configured to remember a maximum number of values.

These configuration values are saved to a JSON file when using the File > Save menu.

On the other hand, the internal state of agents, such as the values displayed by Display Data, are not saved to the JSON file.

<Expansion title="Global Config" showIcon={false}>

#### Global Config

Some agents, like the API agent, can have global configs that are common to all instances.

Global configs are set on the Settings page and are saved as Mnemnk App settings, similar to Core Settings.

Since they aren't saved to the flow's JSON file, they're suitable for settings dependent on the user's or machine's environment, such as database addresses.
(However, since they are still saved as configurations, caution is still necessary.)

</Expansion>

### Channels

Agents can have multiple input channels and multiple output channels.

Input channels are arranged on the left side of the agent.
Examples include the `in` and `reset` channels of the `Memory` agent, and the `data` channel of the `Display Data` agent.

Conversely, output channels are on the right side, such as
the `integer` channel of the `Integer Input` agent, and the `memory` and `reset` channels of the `Memory` agent.

Connecting these channels enables communication between agents.

After connecting `Integer Input`'s `integer` to `Memory`'s `in`, and `Memory`'s `memory` to `Display Data`'s `data`, press the play button ▶ at the bottom of the screen to activate the flow.
This results in the following display:

![](/images/guide/agents/first-agent-flow2.png)

When the value of `Integer Input` changes, the display in `Display Data` updates accordingly.
`Display Data` shows up to 10 of the most recent values output by `Memory`.

### Agent Operation

#### process

Agents have a `process` method that defines their operation.
This method is invoked when input arrives at **any one** of the agent's input channels, with the channel name and received data as arguments.

:::note
The method is not called only when all input channel values are ready.
:::

The results of `process` are then output to the output channels.
Some agents can produce different outputs to multiple output channels.

![](/images/guide/agents/web-base-loader-agent.png)

In some cases, depending on the data received, `process` might not produce any output.

#### Flow Execution

Pressing the play button ▶ on the Agent page executes `start` for each agent in the displayed flow, transitioning them to the execution state.
(It's also possible to select and execute/stop only specific agents.)

Agents in execution state wait for data to be sent to their input channels, which triggers the `process` method.
Some agents, like `Application` or `Screen`, can actively output data in the execution state without requiring `process` calls.
Flows execute through this data transmission from agent to agent.

<video src="/images/guide/agents/interval-timer.mp4" controls="true" width="720px">interval timer</video>

Agents don't just execute once in a flow; they remain in execution state until stopped, with `process` called each time input is received.

#### Parallel Operation

Each agent operates independently.
Even if one agent is continuously executing `process`, it doesn't block other agents from calling their `process` methods.

Each agent has its own event loop, and `process` is never called simultaneously within a single agent.
If new data arrives during `process` execution, it's temporarily placed in an event queue.

:::tip
Technically, each agent operates as an independent [tokio::task](https://docs.rs/tokio/latest/tokio/task/) with its own event loop.
:::

[^1]: Minsky, Marvin (1986). The Society of Mind. New York: Simon & Schuster. ISBN 0-671-60740-5.
