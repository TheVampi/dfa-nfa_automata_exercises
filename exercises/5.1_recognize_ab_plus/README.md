# Exercise 5.1 (Revised): Recognize the language (ab)+

## 1. Language Description
This automata recognizes the language `L = {(ab)+}`, which is defined by the regular expression `(ab)+`. This language consists of all strings formed by one or more concatenations of the substring "ab".

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `ab`
    2.  `abab`
    3.  `ababab`
    4.  `abababab`
    5.  `ababababab`
    6.  `(ab)⁶`
    7.  `(ab)⁷`
    8.  `(ab)⁸`
    9.  `(ab)⁹`
    10. `(ab)¹⁰`

* **Rejected Strings:**
    1.  `ε` (empty string)
    2.  `a`
    3.  `b`
    4.  `aa`
    5.  `bb`
    6.  `aba`
    7.  `bab`
    8.  `abba`
    9.  `aab`
    10. `bba`

---
## 3. Automata Diagram
![Automata Diagram](./automata.svg)

---
## 4. Automata Type and Justification
* **Type**: **DFA (Deterministic Finite Automata)**.
* **Justification**: It is a DFA because for every state, there is exactly one defined transition for each symbol in the alphabet (`a` and `b`). The automata's path is uniquely determined for any input string, and it does not use ε-transitions. A trap state (`q3`) is used to handle all invalid sequences.

---
## 5. Formal Definition (5-Tuple)
The 5-tuple `M = (Q, Σ, δ, q₀, F)` that defines this automata is:
* **Q** = `{q0, q1, q2, q3}`
* **Σ** = `{a, b}`
* **q₀** = `q0`
* **F** = `{q2}`
* **δ** (Transition Function):

| State | Input 'a' | Input 'b' | Description |
| :---: | :---: | :---: | :--- |
| **q0** | q1 | q3 | Initial State / Even position |
| **q1** | q3 | q2 | Odd position (after 'a') |
| **q2** | q1 | q3 | Even position (after 'b', Accepting) |
| **q3** | q3 | q3 | Trap State |

---
## 6. Source Files
* **Graphviz Source:** [View `automata.dot`](./automata.dot)
* **JFLAP File:** [Download `automata.jff`](./automata.jff)