# fuzzyfloat

A utility library that provides transparent floating point types with tolerances for equality comparison.

# Getting Started

```python
>>>from fuzzyfloat import rel_fp
>>>value = rel_fp(100)
>>>value == 100
True
>>>value == 99.99999999
True
>>>value == 100.00000001
True
>>>value = 1000
>>>value == 1000.0000001
True
>>>value = 10000
>>>value == 10000.000001
True
>>>value = 100000
>>>value == 100000.00001
True
```
```python
>>>from fuzzyfloat import abs_fp
>>>value = abs_fp(100)
>>>value = 100000
>>>value == 100000.00001
False
>>>value == 100000.00000001
True
```

# Setting different tolerances

```python
from fuzzyfloat import FuzzyFloatMeta

class my_fp(metaclass=FuzzyFloatMeta, rel_tol=1e-05, atol=0.01):
    pass
```

# Using a different underlying type

```python
import numpy as np
from fuzzyfloat import FuzzyFloatMeta

class np_fp(metaclass=FuzzyFloatMeta, ftype=np.float128):
    pass
    
class c_fp(metaclass=FuzzyFloatMeta, ftype=complex):
    pass

```