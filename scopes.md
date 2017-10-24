# LEGB

Local -> Enclosed -> Global -> Built in

![legb](http://sebastianraschka.com/images/blog/2014/scope_resolution_legb_rule/scope_resolution_1.png)

---

As a warm-up exercise, let us first forget about the enclosed (E) and built-in (B) scopes in the LEGB rule and only take a look at LG - the local and global scopes.
What does the following code print?

```python
a_var = 'global variable'

def a_func():
    print(a_var, '[ a_var inside a_func() ]')

a_func()
print(a_var, '[ a_var outside a_func() ]')
```

a)

```python
raises an error
```

b)

```python
global value [ a_var outside a_func() ]
```

c)

```python
global value [ a_var inside a_func() ]
global value [ a_var outside a_func() ]
```

---

```python
a_var = 'global value'

def a_func():
    a_var = 'local value'
    print(a_var, '[ a_var inside a_func() ]')

a_func()
print(a_var, '[ a_var outside a_func() ]')
```

a)

```python
raises an error
```

b)

```python
local value [ a_var inside a_func() ]
global value [ a_var outside a_func() ]
```

c)

```python
global value [ a_var inside a_func() ]
global value [ a_var outside a_func() ]
```

---

```python
a_var = 'global value'

def outer():
    a_var = 'enclosed value'

    def inner():
        a_var = 'local value'
        print(a_var)

    inner()

outer()
```

a)

```python
global value
```

b)

```python
enclosed value
```

c)

```python
local value
```

---

```python
a_var = 'global variable'

def len(in_var):
    print('called my len() function')
    l = 0
    for i in in_var:
        l += 1
    return l

def a_func(in_var):
    len_in_var = len(in_var)
    print('Input variable is of length', len_in_var)

a_func('Hello, World!')
```

a)

```python
raises an error (conflict with in-built `len()` function)
```

b)

```python
called my len() function
Input variable is of length 13
```

c)

```python
Input variable is of length 13
```
