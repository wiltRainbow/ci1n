# ci1n

```python
"""compress into 1 number (ci1n)
allows you to compress multiple numbers into one
"""
from math import ceil

BIT_SHIFTING_AMOUNT = 7
MAX_VALUE = 2**BIT_SHIFTING_AMOUNT - 1


def compress(input_numbers: list[int]):
    compressed = 0
    for number in input_numbers:
        if number > MAX_VALUE:
            raise ValueError(f"{number} > {MAX_VALUE}({BIT_SHIFTING_AMOUNT})")
        if number < 0:
            raise ValueError("Cannot handle negative values")
        compressed <<= BIT_SHIFTING_AMOUNT
        compressed += number

    return compressed


def decompress(compressed: int):
    output_numbers = []
    for i in range(ceil(len(f"{compressed:b}")/BIT_SHIFTING_AMOUNT)):
        output_numbers.insert(0, compressed & MAX_VALUE)
        compressed >>= BIT_SHIFTING_AMOUNT

    return output_numbers

```
