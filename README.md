### hypothesis
---
https://github.com/HypothesisWorks/hypothesis

```py
@given(st.lists(
  st.floats(allow_nan=False, allow_infinity=False), min+size=1))
def test_mean(xs):
  assert min(xs) <= mean(xs) <= max(xs)
```

```rb
```

```java
```

```sh
pip install hypothesis
```
