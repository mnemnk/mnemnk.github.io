---
title: Board
---

Boards function like bulletin boards where agents can exchange information with each other.

Mnemnk has two types of nodes: `Board In` and `Board Out`.

![](/images/guide/board/board-in-out.png)

Agents can write values to a "board" by sending values to `Board In` with a specified board name.

![](/images/guide/board/board-in.png)

The written values are output to agents connected to `Board Out` nodes with the same board name.

![](/images/guide/board/board-out.png)

Using boards provides a way to transmit information without directly connecting agents.

## Board Name

Boards are distinguished by their names.

Multiple `Board In` nodes can exist with the same name. 
They all write values to the same board.

Similarly, multiple `Board Out` nodes can exist with the same name.
When a value is written to a board with that name, the value is output from all `Board Out` nodes with the same name.

:::note
`Board In` and `Board Out` nodes without a board name set are invalid.
They will not function.
:::

### Board Name `*`

`Board In` can be set with a special name `*`.

In this case, `Board In` uses the channel name that the connected agent used when outputting data as the board name.

This is used, for example, when writing API agent outputs to a board.

![](/images/guide/board/board-star.png)

`Board Out` cannot use `*` as a board name.

## Communication Across Flows

Value propagation through boards is not limited to within a flow.

By using boards with common names, agents can send and receive data across different flows.

This functionality of boards makes it possible to divide flows into logical units and use them in coordination.
