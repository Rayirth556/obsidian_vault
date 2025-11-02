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





## Explicit parallelism

In this type of parallelism, the programmer specifies the the concurrency primitives, how tasks are split, synchronisation and optimization.

We do not depend on compiler/runtime to infer parallel execution automatically.

Flexible tradeoffs of explicit parallellism
* At the lowest level we can implement any synchronisation / parallel structure
* Maximum control, maximum power, hence max performance and efficiency
* But programmer must manage complexity, debugging is harder, race conditions risk increases.


Methods of parallelism:
1) message passing
   Mostly used in distributed memory systems.
   In this method of parallelism, we explicitely send messages between the processes/processors, i.e communication is explicit. For example, MPI(message passing interface) code running on cluster nodes
2) data parallel:
   Parallelism is achieved by splitting data into chunks and performing the same operations on them at the same time i.e in parallel.
   We basically dont tell the processes how to interact, the system does that based on the data division. Example: Matric Multiplication
3) Shared memory:
   Multiple threads / processes share the same address space. Communication happens via reading/writing the same memory space. Example: OpenMP threads on a single CPU machine.

OpenMP threads are basically units of execution managed by openMP application programming interface for parallel programming on shared memory systems. The enable the parallelisation of code by allowing a single program to execute multiple parts of a task concurrently.

4) Remote Memory Operation
   We can read / write to another process's memory without it being actively doing send/receive. THis way communication becomes more one sided and implicit
5) Threads
6) Combined models



## STEPS IN PARALLELISM

1) Identify parallelism

Before executing in parallel, we must identify what part of the program can run in parallel.

2) Start/ stop parallel execution

Once identified, you must be able to actually **spawn parallel actions**.

The language runtime must provide:

- creation of parallel threads / tasks / processes
- mapping / scheduling onto available processors
- eventually terminate / join them

Examples:
- pthreads → `pthread_create()`, `pthread_join()`
- MPI → calling `MPI_Init()` and creating processes
- CUDA → launching kernel `<<<grid, block>>>`

So this step is basically the mechanism to **launch parallel execution** and also to end it cleanly.

3) Coordinate parallel executions

Parallel executions must interact even if they are independent.

This involves:
- communication (send/receive, shared memory writes)
- synchronization (locks, barriers, semaphores)
- consistency (avoiding races, ordering access)
- task dependencies