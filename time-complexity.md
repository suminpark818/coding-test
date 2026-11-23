# Time Complexity (시간복잡도)

## Rough Guide (대략적인 기준)
Assume Python handles about **10–100 million** simple operations per second.

파이썬은 1초에 약 **1,000만 ~ 1억 번** 연산 정도로 생각하면 된다.

| Input size n (입력 크기) | Feasible complexity (가능한 복잡도) |
|---|---|
| up to ~500 | O(n³) |
| up to ~5,000 | O(n²) |
| ~100,000 or more (이상) | O(n log n), O(n) |

## Common Patterns (흔한 패턴)
| Code shape (코드 모양) | Complexity (복잡도) |
|---|---|
| Single loop (반복문 1개) | O(n) |
| Nested loops — compare every pair<br>이중 반복문 — 모든 쌍 비교 | O(n²) |
| Sorting `sorted()` (정렬) | O(n log n) |
| set / dict lookup (조회) | O(1) |
| `x in` on a list (list에서 검색) | O(n) ⚠️ |

## Watch Out: Hidden O(n) (주의: 숨은 O(n))
```python
for x in nums:
    if x in some_list:   # list lookup inside a loop → O(n²) overall! (반복문 안의 list 검색 → 전체 O(n²)!)
        ...
```
→ Convert `some_list` to a set to make it O(n)

→ `some_list`를 set으로 바꾸면 O(n)

## Related Problems (관련 문제)
- [217. Contains Duplicate](../problems/0217-contains-duplicate.md): nested loops O(n²) → set O(n)
  - 이중 반복문 O(n²) → set으로 O(n)
