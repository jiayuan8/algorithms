## Greatest Common Divisor

```python
        def gcd(a, b):
        		# requires a > b > 0
            if a % b == 0:
                return b
            else:
                return gcd(b, a - a // b * b)
```

