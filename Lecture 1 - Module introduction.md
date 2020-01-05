# Lecture 1 - Module introduction
### Module info
- **Lecutrer:** Dr Kingsley Sage
- **E-mail:** khs20@sussex.ac.uk
- **Office:** Chichester CI-302

---
### Stable Match Algorithm
- Simple matching - very general type of problem
- **Perfect Match** - everyone on one side, match with exactly one person on the other
- **Stable Match** - no instabilities

**Problem Specification:**
- **Input:** two sets of same size, of elements to match A, B, each with set of preferences
- **Output:** mapping of A to B, such there is: **perfect match** and **no instabilities**

**What a problem is and isn't:**
- **Problem is:**
  - Sepcification of a relationship between **inputs** and **outputs**
  - Usually a **mapping** - one valid output for a given input
- **Problem isn't:**
  - An algorithm

**What an algorithm is and isn't:**
- **Algorithm is:**
  - Specifcation as to how to tackle a problem
  - Can be abstract
  - We will use informal pseudo-code language
- **Algorithm isn't:**
  - Not the same as a program
  - Programs implement algorithms
  - Same algorithm implemented in different languages

- **Solving** is finding an output for every input 

**Algorithm:**
```
while some blue person is free & has red people to propese to
  choose one such blue person *a*
  let *B* be next best option from *a*'s preference list
  if *B* is free
    assign *a* and *B* to be engaged
  else if *B* preferes *a* to *B*s fiance *a*'
    assign *a* and *B* to be engaged, and *a*' to be free
  else
    *B* rejects *a*
END
```

**Example Question Solution:**
A - X
B - Y
C - Z
D - W

#### Multiple Stable Matches
| Person | Preference1 | Preference2 |
|:---:|:---:|:---:|
| blueA | redA | redB |
| blueB | redB | redA |


| Person | Preference1 | Preference2 |
|:---:|:---:|:---:|
| redA | blueB | blueA |
| redB | blueA | blueB |

**Issues:**
- Will it terminate?
- Efficiency
- Will it always finds a stable match?
- Is it a fair algorithm?

#### Termination
**Need for *measure of progress*:**
- a value that monotonically increases as number of executions of loop increases
**Available options:**
1. Blue people still free -
2. Number of engaged couples -

#### Measure of progress
- The number of proposals made so far +
- Always increases by 1 when loop executed
- Upper limit on number of proposals is n^2
- The algorithm will always terminate

#### Efficiency
- Running time depends on time to execute loop once
- Can be done in constant time

#### Proving correctness
- A stable match is always found
- Proof by contradiction:
  - "There is an unstable pair in a match produced by the algorithm"
  - Contradicts 

---
### Counterexample
- All letter boxes are red
- I am a letter box, therefore I am red
- p -> q
- So is the reverese true?
- "I am red, therefore I am a letter box"?
- I could be a red Ferrari

**Contradiction** - in logic, a statement that is always false e.g. "p and ~p"

---
### Cracking Enigma
**Flaw in Enigma:**
- The designers ensured that pattern matching techniques could not be used to decipher messages
- Character could never encode to itself
- A deep cryptographic flaw
- This allowed attack on the cipher by proof by contradiction

**The crib**:
- Small, known part of a message
- Units had a habit of using standard phrases in the opening of their messages e.g. "weather forecast"
- Short part of message was known

**Attack:**
- Line up the cipher text with the crib
- Is there a contradiction? (Letter cannot encode to itself)
- No contradiction, adjust machine to give same outputs

**The Bombe:**
- Turing developed design for a device that would work through the setting until one was found that produced no contradictions
- "Bombe stop"
- Gives candidate settings

- Still, lot of settings
- A lot of other work to reduce the possible number of settings (to few million)
- Then the bombes were used
- Candidate settings, were further analysed to see if they produced German


---
### Sorting Algorithms
**Problem Specification:**
- **Input**: list of elements A in any order
- **Output**: permutation of A in a correct (ascending/descending) order

---
### Search Algorithms
**Problem Specification:**
- **Input:** a sequence of values A that are ordered ans a search item *a*
- **Output:** true if *a* is in A, false otherwise

---