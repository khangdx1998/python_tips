# **Replace if statement with if expression**
* ~~DONT DO THIS~~
```python
if condition:
    x = 1
else:
    x = 2
```
* **DO THIS**
```python
x = 1 if condition else 2
```

# **Symplify sequence comparation**
* ~~DONT DO THIS~~
```python
if len(list_of_hats) > 0:
    hat_to_wear = choose_hat(list_of_hats)
```
* **DO THIS**
```python
if list_of_hats:
    hat_to_wear = choose_hat(list_of_hats)
```
