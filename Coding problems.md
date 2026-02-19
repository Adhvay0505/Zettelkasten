
## Phase 1: Absolute must-do (start here)

These show up _constantly_ and map directly to security tasks (parsing, validation, lookups).

1. **Two Sum** (#1)
    
2. **Valid Anagram** (#242)
    
3. **Contains Duplicate** (#217)
    
4. **Valid Parentheses** (#20)
    
5. **Longest Substring Without Repeating Characters** (#3)
    
6. **Group Anagrams** (#49)
    

🎯 Skills: hash maps, input validation, edge cases

---

## Phase 2: Strings & parsing (VERY security-relevant)

Think logs, payloads, sanitization.

7. **Valid Palindrome** (#125)
    
8. **Implement strStr()** (#28)
    
9. **Longest Common Prefix** (#14)
    
10. **Decode String** (#394)
    
11. **Minimum Remove to Make Valid Parentheses** (#1249)
    

🎯 Skills: string traversal, stacks, defensive coding

---

## Phase 3: Arrays & sliding window

Used for rate limiting, anomaly detection, thresholds.

12. **Maximum Subarray** (#53)
    
13. **Best Time to Buy and Sell Stock** (#121)
    
14. **Subarray Sum Equals K** (#560)
    
15. **Product of Array Except Self** (#238)
    

🎯 Skills: prefix sums, window logic, performance awareness

---

## Phase 4: Graphs & BFS/DFS (permissions, trust, attack paths)

This is where **Google / Meta** especially care.

16. **Number of Islands** (#200)
    
17. **Clone Graph** (#133)
    
18. **Course Schedule** (#207)
    
19. **Pacific Atlantic Water Flow** (#417)
    

🎯 Skills: graph modeling, traversal, cycle detection

---

## Phase 5: Trees (moderate depth only)

Don’t overdo trees — just enough to be fluent.

20. **Maximum Depth of Binary Tree** (#104)
    
21. **Validate Binary Search Tree** (#98)
    
22. **Lowest Common Ancestor of a Binary Tree** (#236)
    

🎯 Skills: recursion, correctness

---

## Phase 6: Realistic “security-style” coding

These feel _very_ close to actual interview prompts.

23. **LRU Cache** (#146)
    
24. **Design HashMap** (#706)
    
25. **Time Based Key-Value Store** (#981)
    
26. **Logger Rate Limiter** (#359)
    

🎯 Skills: system thinking, state, constraints

---

## Phase 7: One or two “stretch” problems (optional)

Do these **only if time permits**.

27. **Merge Intervals** (#56)
    
28. **Word Ladder** (#127)
    

---

## What you can safely SKIP for security roles

❌ Heavy DP (Knapsack, Edit Distance)  
❌ Segment trees  
❌ Bit tricks unless you already know them  
❌ Hard competitive problems

---

## How to practice (this matters more than the list)

For each problem:

1. Talk through **threat modeling mindset** (edge cases, bad input)
    
2. Write **clear, defensive code**
    
3. State time/space complexity
    
4. Mention how you’d **harden** it in production
    

Example:

> “I’d add input length caps to prevent DoS…”

Interviewers **love** that in security roles.

---

## Time estimate

- 1–2 problems/day → **3–4 weeks total**
    
- Re-do Phase 1–4 until you can solve them **cold**