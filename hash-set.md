# Hash Set (`set`)

## When to Use (언제 쓰나)
- Checking for duplicates (중복 확인)
- "Have I seen this value before?" (이 값 본 적 있나?)
- Removing duplicates (중복 제거)

## Why It's Fast (왜 빠른가)
| Operation (연산) | list | set |
|---|---|---|
| `x in` lookup (검사) | O(n) — scans one by one<br>처음부터 하나씩 | **O(1)** — average<br>평균 |
| Add (추가) | `append` O(1) | `add` O(1) |

`x in nums` on a list has to scan everything, while a set finds it directly via hashing.

list에서 `x in nums`는 전부 훑어야 하지만, set은 해시로 바로 찾는다.

## Basic Usage (기본 사용법)
```python
seen = set()          # empty set — careful: {} is an empty dict! (빈 set — 주의: {}는 빈 dict!)
seen.add(3)           # add (추가)
3 in seen             # True
seen.remove(3)        # remove, error if missing (삭제, 없으면 에러)
seen.discard(3)       # remove, no error if missing (삭제, 없어도 에러 X)

s = set([1, 2, 2, 3]) # {1, 2, 3} → duplicates removed (중복 자동 제거)
len(s)                # 3
```

## Common Pattern: "Seen Before?" (자주 쓰는 패턴: 본 적 있는지)
```python
seen = set()
for x in nums:
    if x in seen:
        # already seen (이미 본 값)
        ...
    seen.add(x)
```

## Watch Out (주의)
- No order → no index access (`s[0]` ❌)
  - 순서가 없음 → 인덱스로 접근 불가
- Can't store mutable values like lists (tuples are fine)
  - 리스트처럼 변경 가능한 값은 넣을 수 없음 (튜플은 가능)
- Need counts too? Use `dict` or `collections.Counter`
  - 개수까지 세야 하면 `dict` 또는 `collections.Counter`

## Related Problems (관련 문제)
- [217. Contains Duplicate](../problems/0217-contains-duplicate.md)
