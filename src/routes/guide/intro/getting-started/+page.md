---
title: Getting Started
---
Here, I'll explain the basic concepts and operations of Mnemnk for new users.

If you already have Mnemnk installed, you can follow along as you read.

## Agents

Mnemnk allows you to perform various processes by freely combining agents.

![](/images/guide/intro/getting-started/initial-agent-page.png)

Let's place a Counter agent by selecting Core/Utils/Counter from the "Agents" menu in the top right of the Agents page.

![](/images/guide/intro/getting-started/first-agent.png)

A newly placed agent starts in a stopped state.

You can start the agent by pressing the play button ▶ at the bottom of the screen or by right-clicking the agent and selecting "Start".

![](/images/guide/intro/getting-started/start-agent.png)

Agents have inputs and outputs.

Next, let's connect to other agents.

Place a Core/Input/Unit Input agent and connect the `unit` handle (left side) of the Unit Input to the `in` handle (right side) of the Counter.

![](/images/guide/intro/getting-started/connect-agents.png)

Even when you start the Unit Input agent, the Counter value won't change.

![](/images/guide/intro/getting-started/start-input.png)

When you click the unit on the Unit Input, the Counter value increases.
This happens because Unit Input sends a signal, and Counter receives it to increase its value.

![](/images/guide/intro/getting-started/click-input.png)

Mnemnk agents don't just run once when the play button is pressed; they continue to run constantly.

To confirm this, let's connect a Core/Utils/Interval Timer to the Counter.

![](/images/guide/intro/getting-started/interval-timer.png)

Agents process according to their inputs (if they have any) and produce outputs as needed.

## Flows

A collection of placed and connected agents is called a "flow."
Mnemnk can manage multiple flows.

You can create a new flow from File > New.

![](/images/guide/intro/getting-started/new-flow.png)

Enter a flow name, and a new empty flow will be created.

![](/images/guide/intro/getting-started/new-flow-dialog.png)

![](/images/guide/intro/getting-started/flow2.png)

Flows can be switched using the "Flows" menu on the left side of the screen.

The <span class="flex-none inline-block w-2 h-2 bg-green-500 rounded-full" title="active"></span> mark shown to the left of a flow name indicates that there are active agents within that flow.

An important point to note is that even when a flow is not displayed (i.e., it's in the background), the agents within that flow continue to run.

![](/images/guide/intro/getting-started/background-flow.png)

You can manipulate flows from the File menu.
Created flows can be saved from File > Save (Ctrl+S).
Saved flows are retained after Mnemnk App is closed and automatically loaded when next started.

Additionally, agents that were running when you last closed Mnemnk App will automatically start when Mnemnk App launches.

## Board

Mnemnk has distinctive agents called Board In and Board Out.

Set up a Board In agent and set the Board Name to `counter`.
Then connect it to the count of the Counter.

![](/images/guide/intro/getting-started/board-in.png)

This creates a board named `counter`.

Next, set up a Board Out agent and a Display Data agent.
By setting the Board Name of Board Out to `counter` as well, you can subscribe to the `counter` board you created earlier.

![](/images/guide/intro/getting-started/board-out.png)

Even though Display Data is not directly connected to Counter, it can receive data through Board In and Board Out.

Using Boards allows data exchange even between different flows.

Move to "flow2" from Flows and create Board Out and Display Data as before.

(You can also select multiple agents with shift + mouse drag and copy & paste them with Ctrl+C, Ctrl+V)

![](/images/guide/intro/getting-started/board-out-another-flow.png)

You can see that the same value being updated in the "main" flow is also displayed in "flow2".
This is because data is shared between flows through the board.

## Conclusion

Here, I've explained the basic concepts and operations of Mnemnk using simple agents.

In actual use, you'll likely build more complex flows that analyze and utilize lifelogging data with AI agents, rather than simple counters. However, no matter how complex the flow becomes, the basic principles learned here—placement of agents, connections, and communication through boards—remain the same.
