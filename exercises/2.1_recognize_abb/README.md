# Exercise 2.1: Recognize the string "abb"

## 1. Language Description
This automata recognizes the language `L = {abb}`, which consists solely of the string "abb". Any other string over the alphabet `Σ = {a, b}` is rejected.

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `abb`

* **Rejected Strings:**
    1.  `ε` (empty string)
    2.  `a`
    3.  `ab`
    4.  `abba`
    5.  `b`
    6.  `bb`
    7.  `aba`
    8.  `bba`
    9.  `aa`
    10. `aab`

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
* **Q** = `{q0, q1, q2, q3, q4}`
* **Σ** = `{a, b}`
* **q₀** = `q0`
* **F** = `{q3}`
* **δ** (Transition Function):

| State | Input 'a' | Input 'b' | Description |
| :---: | :---: | :---: | :--- |
| **q0** | q1 | q4 | Initial State |
| **q1** | q4 | q2 | Has seen "a" |
| **q2** | q4 | q3 | Has seen "ab" |
| **q3** | q4 | q4 | Has seen "abb" (Accepting) |
| **q4** | q4 | q4 | Trap State |

---
## 6. Source Files
* **Graphviz Source:** [View `automata.dot`](./automata.dot)
* **JFLAP File:** [Download `automata.jff`](./automata.jff)