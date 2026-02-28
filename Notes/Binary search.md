---
date: 2026-02-20
tags:
  - algorithms
---
## How it works
- Looks at the middle element and checks if its the target
- If smaller than the target, repeat process on the right half
- If larger, repeat on the left half
- Eventually we converge on the target
- **O(log n)** time

Can be used on any list with a consistent increase or decrease (strings, bools, numbers)

## Code snippets
- [[Python Binary Search]]
