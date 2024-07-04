# Threads

Threads are a way to run multiple tasks concurrently. They are lightweight processes that share the same memory space. 
Threads are useful when you want to run multiple tasks at the same time, but you don't want to create a new process 
for each task.

Threads are used in many applications, such as web servers, GUI applications, and games. They are also used in

- Real-time systems
- Multimedia applications
- Network servers
- Parallel computing
- And more

# Threads in python

docs:
- https://docs.python.org/3/library/threading.html

Python has built-in support for threads through the `threading` module. The `threading` module provides a way to create

- Threads
- Locks
- Conditions
- Semaphores
- And more

# Creating a thread
```
import threading

def my_function():
    print("Hello from a thread!")

# Create a thread
thread = threading.Thread(target=my_function)

# Start the thread
thread.start()

# Wait for the thread to finish
thread.join()
```

# Passing arguments to a thread
```
import threading

def my_function(arg1, arg2):
    print(f"Hello from a thread! arg1={arg1}, arg2={arg2}")

# Create a thread

thread = threading.Thread(target=my_function, args=(1, 2))

# Start the thread
thread.start()

# Wait for the thread to finish
thread.join()
```

# Thread synchronization
```
import threading

counter = 0

def increment():
    global counter
    for _ in range(1000000):
        counter += 1

# Create two threads
thread1 = threading.Thread(target=increment)
thread2 = threading.Thread(target=increment)

# Start the threads
thread1.start()
thread2.start()

# Wait for the threads to finish
thread1.join()
thread2.join()

print(counter) # Output: 2000000
```

# Locks
```
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(1000000):
        lock.acquire()
        counter += 1
        lock.release()

# Create two threads
thread1 = threading.Thread(target=increment)
thread2 = threading.Thread(target=increment)

# Start the threads
thread1.start()
thread2.start()

# Wait for the threads to finish
thread1.join()
thread2.join()

print(counter) # Output: 2000000
```

# example with 2 lock, and check that one lock loks only one side of app
```
import threa


