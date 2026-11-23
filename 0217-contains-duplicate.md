# 217. Contains Duplicate

- **Difficulty (난이도)**: Easy
- **Key concepts (핵심 개념)**: [Hash Set](../concepts/hash-set.md), [Time Complexity (시간복잡도)](../concepts/time-complexity.md)

## Problem (문제)
Given an integer array `nums`, return `True` if any value appears **at least twice**, and `False` if every element is distinct.

정수 배열 `nums`가 주어질 때, 어떤 값이 **두 번 이상** 나오면 `True`, 모든 원소가 서로 다르면 `False`를 반환한다.

```
Input: nums = [1, 2, 3, 1]  →  Output: true   (1 appears at indices 0 and 3 / 1이 인덱스 0, 3에 등장)
Input: nums = [1, 2, 3, 4]  →  Output: false  (all distinct / 모두 다름)
```

## My First Attempt (처음 내 답)
```python
class Solution:
    def containsDuplicate(self, nums: list[int]) -> bool:
        for numbers in list:
            numbers = number
            for x in numbers:
                if(x=number){

                }
```

## What Went Wrong (틀린 점)
- `list` is a built-in type name → the input array is `nums`
  - `list`는 자료형 이름 → 입력 배열은 `nums`
- `number` was never defined, and it overwrites `numbers`
  - `number`는 정의된 적 없는 변수, 게다가 `numbers`를 덮어씀
- In the outer loop, `numbers` is a single integer, so it can't be iterated
  - 바깥 반복의 `numbers`는 정수 하나라서 `for`로 돌 수 없음
- Comparison uses `==`, not `=`
  - 비교는 `=`가 아니라 `==`
- Python uses `:` + indentation instead of `{ }`
  - 파이썬은 `{ }` 대신 `:` + 들여쓰기
- 👉 See [Python Syntax Mistakes (문법 실수 모음)](../concepts/python-syntax.md)

## Fixed Version of My Idea (의도대로 고친 답) — Nested Loops, O(n²)
```python
class Solution:
    def containsDuplicate(self, nums: list[int]) -> bool:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):  # compare only with later elements (i 다음부터 비교)
                if nums[i] == nums[j]:
                    return True
        return False
```
Correct, but risks **Time Limit Exceeded** when n is around 100,000.

정답은 맞지만 n이 10만 정도면 **시간 초과** 위험.

## Better Solution (더 좋은 답안) — Set, O(n)
```python
class Solution:
    def containsDuplicate(self, nums: list[int]) -> bool:
        seen = set()
        for x in nums:
            if x in seen:      # already seen → duplicate (이미 본 값 → 중복)
                return True
            seen.add(x)        # first time → record it (처음 보는 값 → 기록)
        return False
```

One-liner (한 줄 버전):
```python
return len(set(nums)) != len(nums)
```
- The loop version stops as soon as it finds a duplicate (early exit)
  - 반복문 버전은 중복을 찾는 즉시 멈춤 (조기 종료)
- The one-liner always converts the whole list to a set → shorter, but no early exit
  - 한 줄 버전은 항상 전체를 set으로 바꿈 → 짧지만 조기 종료 없음

## Takeaways (배운 점)
- **"Duplicate check / seen before?" → think of a set first**
  - **"중복 확인 / 본 적 있는지" → set 먼저 떠올리기**
- The idea (compare every pair) was right; the issues were syntax and time complexity
  - 아이디어(모든 쌍 비교)는 맞았음. 문제는 문법과 시간복잡도
