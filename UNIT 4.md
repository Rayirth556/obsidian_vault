What is a first class function

A first class function is a function in python that can be treated as any other variable, meaning u cant store it in a variable, pass it an argument or return it from another function

EXAMPLE: Assigning a function to a variable
```python
def greet(name):
	return f"Hello, {name}!"
	
say_hello = greet # assigning function to another variable
print(say_hello("rayirth"))
```

EXAMPLE: Passing a function as an argument
```python
def apply(func, value):
	return func(value)
	
def sqaure(x):
	return x * x
	
print(apply(square,5)) # square is passed as a value to another function (apply)
```

EXAMPLE: Returning a function from another function

```python
def make_multiplier(n):
	def multiplier(x):
		return x * n
	return multiplier

times3 = make_multiplier(3)
```



HIGHER ORDER FUNCTIONS IN PYTHON:

A higher order function in python is a function that can either:
1) Accept another function as an argument, or 2) It can return a function

```python
def loud(text):
	return text.upper()

def quiet(text):
	return text.lower()
	
def hello(func):
	text = func("hello")
	
hello(loud)
```

FUNCTION RETURNING A FUNCTION

```python
def divisor(x):
	def dividend(x):
		return x / y
	return dividend
	
divide = divisor(2)
print(divide(10))
```



What is a closure:

A closure is a function in python that remembers the variables and its values from the environment where it was created, even after that environment has finished executing 


The ```map()``` function:
The map() function is a function that applies a function to each iteration in an iterable(like a list or an array) and returns a new iterator with the results
