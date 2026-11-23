# Python Syntax Mistakes (파이썬 문법 실수 모음)

## `=` vs `==`
```python
x = 3      # assignment — stores a value (대입 — 값을 넣음)
x == 3     # comparison — checks equality → True/False (비교 — 같은지 확인)
```
`if x = 3:` is a syntax error. (`if x = 3:`은 문법 에러.)

## Colon + Indentation, Not Braces (중괄호 대신 콜론 + 들여쓰기)
```python
# ❌ C / Java style (C / Java 스타일)
if (x == 3) {
    ...
}

# ✅ Python (파이썬)
if x == 3:
    ...
```
- Parentheses around conditions are optional
  - 조건 괄호 `( )`는 없어도 됨
- Blocks start after `:` and are defined by **indentation** (usually 4 spaces)
  - 블록은 `:` 다음 줄부터 **들여쓰기**로 구분 (보통 공백 4칸)

## Variable Names (변수 이름)
- Don't use **built-in names** like `list`, `dict`, `set`, `str`, `sum`, `max` as variables
  - `list`, `dict`, `set`, `str`, `sum`, `max` 같은 **내장 이름**을 변수로 쓰지 않기
- `for x in list:` ❌ → check the actual input variable name (`nums`, etc.)
  - 입력 변수 이름(`nums` 등)을 확인
- Using an undefined variable → `NameError`
  - 정의하지 않은 변수 사용 → `NameError`

## Integers Are Not Iterable (정수는 반복할 수 없다)
```python
for numbers in nums:   # numbers is a single int (numbers는 정수 하나)
    for x in numbers:  # ❌ TypeError: 'int' object is not iterable
```

## Loop by Value vs by Index (값으로 돌기 vs 인덱스로 돌기)
```python
for x in nums:                 # values (값)
for i in range(len(nums)):     # indices → nums[i] (인덱스)
for i, x in enumerate(nums):   # both (둘 다)
```

## Related Problems (관련 문제)
- [217. Contains Duplicate](../problems/0217-contains-duplicate.md)
