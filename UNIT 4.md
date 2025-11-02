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


## ways of parallelism

1) functional decomposition (functional parallelism)
2) domain/data decomposition (data parallelism)

1)
We basically break down the problem / algorithm into different tasks and functions, and then each processor gets to work on each of these different problems/ tasks/part of the algorithm.
This is used when the number of functions is not fixed, when the work is not uniform.
Basically splitting the steps of the algorithm into different individual tasks 

2)
Breaking down data into chunks. Each processor gets the same function but on a different subset of data.

Use when:
- huge matrix to solve
- physics simulation domain
- finite difference computation
- simulation where domain is large but can be broken into regions\




## Phase parallel model
The phase parallel model is a model of computation that follows the bulk synchronous parallel style.
In this form of computing the entire program proceeds in form of steps/supersteps.

Each superstep is divided into two phases
The first is the computation phase

In this phase processes perform same operations on their own local data in parallel without any communication across them.

The next phase in this model is the interaction / communication phase
This is where all the processes exchange share merge information they need to perform synchronisaton for the next steps. Then a barrier happens, each process waits for other processes to complete

## Divide and conquer model

In this model of computation, the parent process of a program divides tasks and workload in smaller pieces among its child processes. The child processes then compute their workload in parallel and the results are merged by the parent.

The dividing and merging are done recursively. 

**When to use:**
- Problems can be broken into independent subproblems
- Natural recursion exists
- Merging results is cheaper than solving the whole problem

Examples: Merge sort, quick sort, matrix multiplication, binary search trees, fourier transform

## Pipeline model

In this model, the number of processes create a form of virtual pipeline, and then this pipeline is fed a continuous stream of data, which is executed at different stages of the pipeline simultaneously in an overlapped fashion. 



## Network programming

# socket
so what is a socket
A socket is basically a software endpoint that enables bidirectional communication between processes whether they are on the same machine or across the world 
A socket is a combination of IP address and port number.
