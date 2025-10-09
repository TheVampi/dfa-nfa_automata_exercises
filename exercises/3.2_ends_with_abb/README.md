# Exercise 3.2: Strings Ending with "abb"

## 1. Language Description
This automata recognizes the language defined by the regular expression `(a|b)*abb`. This includes all strings over the alphabet `Σ = {a, b}` that end with the substring "abb".

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `abb`
    2.  `aabb`
    3.  `babb`
    4.  `aaabb`
    5.  `ababb`
    6.  `baabb`
    7.  `bbabb`
    8.  `abababb`
    9.  `aaaaabb`
    10. `bbbbabb`

* **Rejected Strings:**
    1.  `ε` (empty string)
    2.  `a`
    3.  `b`
    4.  `ab`
    5.  `abba`
    6.  `abab`
    7.  `bba`
    8.  `aab`
    9.  `aa`
    10. `bb`

---
## 3. Automata Diagram
![Automata Diagram](./automata.svg)

---
## 4. Automata Type and Justification
* **Type**: **DFA (Deterministic Finite Automata)**.
* **Justification**: It is a DFA because for every state, there is exactly one defined transition for each symbol in the alphabet (`a` and `b`). The automata's path is uniquely determined for any input string, and it does not use ε-transitions.

---
## 5. Formal Definition (5-Tuple)
The 5-tuple `M = (Q, Σ, δ, q₀, F)` that defines this automata is:
* **Q** = `{q0, q1, q2, q3}`
* **Σ** = `{a, b}`
* **q₀** = `q0`
* **F** = `{q3}`
* **δ** (Transition Function):

| State | Input 'a' | Input 'b' | Description |
| :---: | :---: | :---: | :--- |
| **q0** | q1 | q0 | No part of "abb" suffix matched |
| **q1** | q1 | q2 | Suffix might be "a..." |
| **q2** | q1 | q3 | Suffix might be "ab..." |
| **q3** | q1 | q0 | Suffix is "abb" (Accepting) |

---
## 6. Source Files
* **Graphviz Source:** [View `automata.dot`](./automata.dot)
* **JFLAP File:** [Download `automata.jff`](./automata.jff)