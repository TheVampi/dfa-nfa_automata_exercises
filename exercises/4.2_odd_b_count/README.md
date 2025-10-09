# Exercise 4.2: Strings with an Odd Number of 'b's

## 1. Language Description
This automata recognizes the language `L = {w ∈ {a,b}* | w has an odd number of 'b's}`. The language consists of all strings over the alphabet `{a, b}` that contain an odd number of the symbol 'b'. The number of 'a's is irrelevant.

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `b`
    2.  `ab`
    3.  `bab`
    4.  `bba`
    5.  `bbb`
    6.  `aaab`
    7.  `ababa`
    8.  `babbb`
    9.  `aaaaab`
    10. `bbbbba`

* **Rejected Strings:**
    1.  `ε` (empty string)
    2.  `a`
    3.  `aa`
    4.  `bb`
    5.  `aba`
    6.  `baba`
    7.  `aabb`
    8.  `baab`
    9.  `bbbb`
    10. `aaabb`

---
## 3. Automata Diagram
![Automata Diagram](./automata.svg)

---
## 4. Automata Type and Justification
* **Type**: **DFA (Deterministic Finite Automata)**.
* **Justification**: It is a DFA because for every state, there is exactly one defined transition for each symbol in the alphabet (`a` and `b`). The automata's path is uniquely determined, and it does not use ε-transitions.

---
## 5. Formal Definition (5-Tuple)
The 5-tuple `M = (Q, Σ, δ, q₀, F)` that defines this automata is:
* **Q** = `{q0, q1}`
* **Σ** = `{a, b}`
* **q₀** = `q0`
* **F** = `{q1}`
* **δ** (Transition Function):

| State | Input 'a' | Input 'b' | Description |
| :---: | :---: | :---: | :--- |
| **q0** | q0 | q1 | Even 'b's count (Initial) |
| **q1** | q1 | q0 | Odd 'b's count (Accepting) |

---
## 6. Source Files
* **Graphviz Source:** [View `automata.dot`](./automata.dot)
* **JFLAP File:** [Download `automata.jff`](./automata.jff)