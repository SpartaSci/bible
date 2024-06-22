---
aliases:
  - FSM
---

> A *finite state machine* is a machine that evolves through a finite number of states. Each time we want to describe a FSM in an accurate and complete way, we can represent its behaviour using a *state transition diagram*. In which, each state is represented as node, and the edges represent the transitions.

**Mealy FSM**: updates the output based on the *current state* and *input* value or conditions causing the transition. ^613268
- output update is part of the transition label
- with the input that condition causing the transition

**Moore FSM**: the output value depends only on the *current state*.
- output is placed in a box near the state and is independent from the current input
- the input is still in the transition label



A FSM can always be implemented with (for both):
- register storing the machine's state
- a combinational network generating the **next state** based on the *current state and input values*
- they differ only on the output generation




![](https://media.licdn.com/dms/image/D5622AQH7v5_YOTL-nQ/feedshare-shrink_2048_1536/0/1691636209601?e=2147483647&v=beta&t=6Tqiw_pCQIoX7FRZcfY6U8YMpRlUnpVP8PBLpkWUWKY)
![](https://d8it4huxumps7.cloudfront.net/bites/wp-content/banners/2023/7/64c0dd8417393_mealy_vs_moore_machine_whats_the_difference.jpg)
