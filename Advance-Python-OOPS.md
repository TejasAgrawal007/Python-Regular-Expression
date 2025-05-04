# Advance-Python-OOPS.md
---

## 🔶 1. Static, Class, and Instance Methods

### ➤ **Instance Method** – operates on object (`self`)

### ➤ **Class Method** – operates on class (`cls`)

### ➤ **Static Method** – utility function, no access to class or instance

```python
class Example:
    def instance_method(self):
        print("Instance method", self)

    @classmethod
    def class_method(cls):
        print("Class method", cls)

    @staticmethod
    def static_method():
        print("Static method")

e = Example()
e.instance_method()
Example.class_method()
Example.static_method()
```

---

## 🔶 2. Method Resolution Order (MRO) & Diamond Problem

MRO is how Python decides which method to call in multiple inheritance.

```python
class A: pass
class B(A): pass
class C(A): pass
class D(B, C): pass

print(D.mro())  # Order Python searches methods
```

🔸 Python uses **C3 Linearization** to resolve the order safely.

---

## 🔶 3. `__new__` vs `__init__`

* `__new__()` creates the object (used for immutable types like `int`, `str`).
* `__init__()` initializes it.

```python
class MyClass:
    def __new__(cls):
        print("__new__ called")
        return super().__new__(cls)

    def __init__(self):
        print("__init__ called")

obj = MyClass()
```

---

## 🔶 4. `__slots__` — Memory Optimization

Reduces memory by avoiding `__dict__`.

```python
class WithSlots:
    __slots__ = ['name', 'age']
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

---

## 🔶 5. Abstract Base Classes (ABC)

Define interfaces — force subclasses to implement methods.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self): pass

class Circle(Shape):
    def __init__(self, r): self.r = r
    def area(self): return 3.14 * self.r ** 2
```

---

## 🔶 6. `@property` — Getter/Setter

Make method behave like attribute.

```python
class Circle:
    def __init__(self, r): self._r = r

    @property
    def radius(self):
        return self._r

    @radius.setter
    def radius(self, value):
        self._r = value
```

---

## 🔶 7. Descriptors

Objects that manage access to other attributes via `__get__`, `__set__`, etc.

```python
class Descriptor:
    def __get__(self, obj, objtype=None):
        return "value from descriptor"

class MyClass:
    attr = Descriptor()

obj = MyClass()
print(obj.attr)
```

---

## 🔶 8. Metaclasses — Class of a Class

Control how classes are created.

```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        print(f"Creating {name}")
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    pass
```

---

## 🔶 9. Monkey Patching — Runtime Change

Modify code behavior dynamically.

```python
import math

def hacked_sqrt(x):
    return "hacked!"

math.sqrt = hacked_sqrt
print(math.sqrt(4))  # hacked!
```

---

## 🔶 10. Composition over Inheritance

Instead of inheriting, use class inside class.

```python
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()

    def drive(self):
        self.engine.start()
```

---

Would you like me to guide you through these one by one with small hands-on tasks or real-life examples next?
