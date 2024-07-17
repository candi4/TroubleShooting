# Fundamentals
About Fundamentals of Python

## Usage
### *args, **kwargs
```
def f(a, *args, **kwargs):
    print(a)
    print(args)
    print(kwargs)
f(1,2,b=3)
```
```
1
(2,)
{'b': 3}
```

