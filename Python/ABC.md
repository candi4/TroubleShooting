# ABC
Defines abstract base classes (ABCs)
Classes or methods made by ABC should be overrided.

## Basic
```python
from abc import ABC, abstractmethod

class MyABC(ABC):
    @abstractmethod
    def method(self):
        raise NotImplementedError()
```
