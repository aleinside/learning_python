# LEGB

Local -> Enclosed -> Global -> Built in

![legb](http://sebastianraschka.com/images/blog/2014/scope_resolution_legb_rule/scope_resolution_1.png)

## Example 1.1

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
