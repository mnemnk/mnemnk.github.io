---
title: Flow and Channel
---

In this section, I'll explain Flows and Channels in Mnemnk.

## Flow

A flow is a collection of agents with connections established from output channels to input channels.

You can create a new flow from the File > New menu, and Mnemnk App can maintain multiple flows.
The names of flows are displayed on the left side of the Agents page.
It's important to note that agents within flows that aren't currently selected will continue to operate.

When you save a flow, it will be automatically loaded the next time you start the application.

:::note
Flows that were saved while in a running state will automatically start again when Mnemnk App launches.
:::

### Connection

There are no specific restrictions on connections between agents.

You can connect multiple agents to a single input channel, and you can also connect a single output channel to multiple agents.

![](/images/guide/flow-and-channel/in-out-channels.png)

An agent's `process` method is called when data is sent to its input channel, and it can produce output at any time.

When an output agent has multiple connections, the order in which data is sent to those connections is not defined and cannot be guaranteed.
For example, in the image above, if `Unit Input` is connected to both the `in` and `reset` channels of `Counter`, when you click the unit in `Unit Input`, the count might increment by 1 and then reset to 0, or it might reset to 0 and then become 1.
The order is indeterminate.

## Channel

Input channels and output channels have names.

These names are merely hints about what kind of data is received and what kind of data is output.
As we've seen, when connecting agents, the input channel name doesn't need to match the output channel name.

The input channel name is used by the agent to distinguish which of its channels received the data, and it has no relation to the source output channel name.[^1]

The output channel name is a label used by agents with multiple output channels to determine which output channel to send data through.[^2]

### Channel `*`

#### Input Channel `*`

While I mentioned that only the input channel name is used and the output channel name is irrelevant, there's an exception when the input channel name is `*`.

When the input channel name is `*`, the output channel name is passed to the agent's `process` method.[^3]
If you look closely at the `Debug Data` display in the image above, you'll see `"ch": "count"`.
This `count` comes from the output channel name of the `Counter` agent.

The input channel name `*` is used when there's a need to know the name of the output channel.
(e.g., `Board In` agent, `Debug Data` agent)

#### Output Channel `*`

When the output channel name is `*`, it indicates that all outputs from the agent will (also) be output through that output channel.
Note that the channel name used for output will be the channel name specified by the agent when outputting data, not `*`.

The output channel name `*` is used when an agent wants to output various types of data through the same output.
(e.g., `Board Out` agent, `API` agent)

#### Both Sides `*`

The same rules apply when both the input channel name is `*` and the output channel name is `*`.
Following the rules above, the channel name specified by the output agent will be used in the call to the input agent's `process` method.

:::caution
To agent developers:

Even for agents with a single input or output, you should avoid casually setting the channel name to `*`.
Use `*` only when these special rules are necessary.
:::

[^1]: The input channel name is equivalent to the parameter names `x` and `y` in a function `fn f(x, y) ->` in programming languages, which are completely unrelated to the variable names `foo` and `bar` used when calling the function like `f(foo, bar)`.

[^2]: Languages that allow naming return values are rare, but [Go](https://go.dev/tour/basics/7) is one that does.

[^3]: This is similar to rest props.
