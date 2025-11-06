# Extra Credit: Even 'a's and Even 'b's

## 1. Language Description
This automata recognizes the language `L = {Z ∈ {a,b}* | Z contains an even number of 'a's AND an even number of 'b's}`. The count for both symbols must be even. Zero is considered an even number, so the empty string (`ε`) is accepted.

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `ε` (empty string)
    2.  `aa`
    3.  `bb`
    4.  `aabb`
    5.  `bbaa`
    6.  `abab`
    7.  `baba`
    8.  `aaaa`
    9.  `bbbb`
    10. `ababbaba`

* **Rejected Strings:**
    1.  `a`
    2.  `b`
    3.  `ab`
    4.  `ba`
    5.  `aab`
    6.  `bba`
    7.  `aaa`
    8.  `bbb`
    9.  `abb`
    10. `baa`

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
* **F** = `{q0}`
* **δ** (Transition Function):

| State | Input 'a' | Input 'b' | Description (Parity 'a's, Parity 'b's) |
| :---: | :---: | :---: | :--- |
| **q0** | q2 | q1 | (Even, Even) - Initial & Accepting |
| **q1** | q3 | q0 | (Even, Odd) |
| **q2** | q0 | q3 | (Odd, Even) |
| **q3** | q1 | q2 | (Odd, Odd) |

---
## 6. Source Files
* **Graphviz Source:** [View `automata.dot`](./automata.dot)
* **JFLAP File:** [Download `automata.jff`](./automata.jff)

---
## 7. Regular Grammar (Type 3)
This automaton can be converted into an equivalent Type 3 Regular Grammar `G = (V, T, P, S)`:
* **V (Variables):** `{S, Q1, Q2, Q3, Q4, Q5, Q6, Q7, Q8, Q9, Q10, Q11}`
* **T (Terminals):** `{a, b, c, d, z}`
* **S (Start Symbol):** `S`
* **P (Production Rules):**
    * `S → Q1` | `Q6` | `Q9` (from ε-transitions)
    * `Q1 → a Q1`
    * `Q1 → b Q1`
    * `Q1 → c Q2`
    * `Q2 → b Q3`
    * `Q3 → b Q4`
    * `Q4 → a Q5`
    * `Q4 → b Q5`
    * `Q5 → a Q5`
    * `Q5 → b Q5`
    * `Q6 → z Q7`
    * `Q7 → b Q8`
    * `Q8 → b Q4`
    * `Q9 → d Q10`
    * `Q10 → b Q11`
    * `Q5 → ε` (because `Q5` is an accepting state)
    * `Q11 → ε` (because `Q11` is an accepting state)

---
## 8. Derivation Example
This shows how the grammar generates the accepted string "**aabcbbabab**".

### Derivation Path
1.  `S → Q1`
2.  `Q1 → a Q1`
3.  `Q1 → a Q1`
4.  `Q1 → b Q1`
5.  `Q1 → c Q2`
6.  `Q2 → b Q3`
7.  `Q3 → b Q4`
8.  `Q4 → a Q5`
9.  `Q5 → b Q5`
10. `Q5 → a Q5`
11. `Q5 → b Q5`
12. `Q5 → ε`

### Parse Tree
![Parse Tree Diagram](./parse_tree.svg)

* **Graphviz Source (Parse Tree):** [View `parse_tree.dot`](./parse_tree.dot)