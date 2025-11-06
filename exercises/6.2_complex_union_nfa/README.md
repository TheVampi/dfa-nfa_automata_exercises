# Exercise 6.2: NFA for a Complex Union

## 1. Language Description
This automata recognizes the language `L = (a|b)*cbb(a|b)+ | zbb(a|b)+ | dbb`. The language is a union of three distinct patterns:
1.  Any string of 'a's and 'b's, followed by "cbb", followed by one or more 'a's or 'b's.
2.  The string "zbb", followed by one or more 'a's or 'b's.
3.  The literal string "dbb".

An NFA is the most direct way to model this language due to the top-level union.

---
## 2. Sample Strings
* **Accepted Strings:**
    1.  `dbb`
    2.  `cbba`
    3.  `cbbb`
    4.  `zbba`
    5.  `zbbb`
    6.  `acbba`
    7.  `bbbcbbb`
    8.  `zbbab`
    9.  `cbbab`
    10. `aabcbbabab`

* **Rejected Strings:**
    1.  `ε` (empty string)
    2.  `a`
    3.  `cbb` (must be followed by at least one 'a' or 'b')
    4.  `zbb` (must be followed by at least one 'a' or 'b')
    5.  `db`
    6.  `c`
    7.  `z`
    8.  `d`
    9.  `acbb`
    10. `azbb`

---
## 3. Automata Diagram
![Automata Diagram](./automata.svg)

---
## 4. Automata Type and Justification
* **Type**: **NFA (Non-deterministic Finite Automata)**.
* **Justification**: It is an NFA because it heavily relies on `ε`-transitions from the start state to non-deterministically choose which of the three patterns in the union to attempt to match. This branching into multiple possible paths without consuming input is a key characteristic of non-determinism.

---
## 5. Formal Definition (5-Tuple)
The 5-tuple `M = (Q, Σ, δ, q₀, F)` that defines this automata is:
* **Q** = `{q0, q1, q2, q3, q4, q5, q6, q7, q8, q9, q10}`
* **Σ** = `{a, b, c, d, z}`
* **q₀** = `q0`
* **F** = `{q5, q10}`
* **δ** (Transition Function):
    * `δ(q0, ε) = {q1, q6, q8}`
    * **Path 1**: `δ(q1, a) = {q1}`, `δ(q1, b) = {q1}`, `δ(q1, c) = {q2}`, `δ(q2, b) = {q3}`, `δ(q3, b) = {q4}`, `δ(q4, a) = {q5}`, `δ(q4, b) = {q5}`, `δ(q5, a) = {q5}`, `δ(q5, b) = {q5}`
    * **Path 2**: `δ(q6, z) = {q7}`, `δ(q7, b) = {q3}`
    * **Path 3**: `δ(q8, d) = {q9}`, `δ(q9, b) = {q10}`

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
    * `Q5 → ε` (because `q5` is an accepting state)
    * `Q11 → ε` (because `q11` is an accepting state)

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