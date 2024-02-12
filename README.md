# Python-Decorators-Unravelled
Learn all you want to know about python decorators
## What are Decorators?
Decorators in Python are functions that enhance the behavior of other functions or classes at runtime. They are indicated by the '@' symbol followed by the decorator function name. Decorators enable the addition of functionality to existing code or the creation of more flexible and reusable code. They wrap one piece of code with another, modifying behavior by either adding functionality like logging or timing to functions or enforcing rules on classes. By separating cross-cutting concerns into separate functions, decorators help avoid clutter in the main codebase and facilitate easy modification or removal of added functionality later.

## Why are Decorators Useful in Python?
Decorators are useful in Python for a number of reasons. Firstly, they can help you to write
more efficient and maintainable code by reducing repetition and clutter in your main codebase.
By separating out cross-cutting concerns into separate functions, you can make your code
easier to read and modify. For example, if you have several functions that require input
validation, you can create a decorator that handles the validation and apply it to each function.
Secondly, decorators can simplify common tasks such as logging, timing, or input validation,
allowing you to focus on the core logic of your program. For example, you can create a logging
decorator that automatically logs the inputs and outputs of each function in your program.
This can be useful for debugging and monitoring the performance of your program.
Finally, decorators can help you to create more flexible and reusable code by separating out
functionality into modular pieces. By creating decorators that add specific functionality to your
code, you can reuse those decorators across multiple functions and classes. This can save you
time and effort, and make your code more maintainable in the long run.

## How Decorators Work in Python?
Decorators work by wrapping the original function or class with another function that modifies
its behavior. When a decorator is applied to a function, it takes the original function as an
argument and returns a new function that wraps it. This new function can add functionality to
the original function, such as logging or timing. When a decorator is applied to a class, it
modifies the behavior of the class itself, rather than its methods.
In Python, you can define your own decorators using the '@' symbol followed by a decorator
function name. Decorator functions can take arguments and return functions, allowing you to
create flexible and reusable decorators. You can also apply multiple decorators to a single
function or class, allowing you to combine different functionalities in a modular way.
One important thing to keep in mind when using decorators in Python is that they can change
the behavior of your code in unexpected ways if not used correctly. For example, if you apply a
decorator to a function that is already decorated, you may get unexpected results. It's
important to understand how decorators work and to use them judiciously to avoid introducing
bugs into your code.

Another thing to keep in mind is that decorators can have performance implications, especially
if you apply them to functions that are called frequently or have large inputs. When using
decorators, it's important to benchmark your code to ensure that the decorator is not
introducing significant overhead.
Overall, decorators are a powerful and flexible feature of Python that allow you to modify or
enhance the behavior of functions or classes at runtime. By using decorators, you can write
more efficient, readable, and maintainable code, and create more flexible and reusable
functions and classes. In the next chapter, we'll explore function decorators in more detail and
provide practical examples of how to use them.

## Function Decorators
Function decorators are a powerful tool in Python that allow you to modify or enhance the
behavior of functions at runtime. In this chapter, we'll cover the basics of function decorators,
including how to apply them using the @ symbol, how to write your own function decorators,
how to apply multiple decorators to a single function, and how to use decorators with
arguments.

## Decorating Functions With the @ Symbol
The most common way to apply a decorator to a function in Python is to use the @ symbol
followed by the decorator function name. This syntax is called "pie syntax," because the
decorator functions are stacked on top of each other like a pie. Using this syntax can make it
easier to read and write code, as it allows you to separate out the function's behavior from the
decorator's behavior.
When a decorator is applied to a function, the decorator function takes the original function as
an argument and returns a new function that wraps it. This new function can add functionality
to the original function, such as logging or timing. The decorator function is essentially a
higher-order function that takes a function as an argument and returns a new function that
modifies its behavior.

## Writing Your Own Function Decorators
You can also write your own function decorators in Python. Function decorators are simply
functions that take a function as an argument and return a new function that wraps the
original function. This can be useful when you need to add functionality to existing code, or
when you want to create more flexible and reusable code.
To write your own function decorator, you need to define a function that takes a function as an
argument and returns a new function that wraps the original function. This new function can
add any functionality that you want, such as timing or logging. For example, to write a timing
decorator, you might write:

import time
def timing_decorator(func):
def wrapper():
start_time = time.time()
result = func()
end_time = time.time()
print(f"Elapsed time: {end_time - start_time}")
return result
return wrapper
This decorator function takes a function as an argument, wraps it in a new function that adds
timing functionality, and returns the new function. You can then apply this decorator to any
function that you want to time.

## Applying Multiple Decorators to a Single Function
You can also apply multiple decorators to a single function in Python. When you apply multiple
decorators, the function is wrapped by each decorator in turn, from the inside out. This can be
useful when you need to apply multiple types of functionality to a function, such as logging,
timing, and input validation.
To apply multiple decorators to a single function, you simply stack them on top of each other
using the @ syntax. For example, to apply both a timing decorator and a logging decorator to a
function, you might write:
@timing_decorator
@logging_decorator
def my_function():
# function body
In this case, the my_function function is first wrapped by the logging_decorator function,
which adds logging functionality, and then wrapped by the timing_decorator function, which
adds timing functionality.

## Decorators with Arguments
You can also create decorators that take arguments in Python. To do this, you need to define a
decorator function that takes arguments, and then return a new function that takes a function

as an argument and returns a new function that wraps the original function. This can be useful
when you need to customize the behavior of a decorator for different use cases.
For example, to create a timing decorator that takes an argument specifying the time unit, you
might write:
import time
def timing_decorator(time_unit):
def decorator(func):
def wrapper():
start_time = time.time()
result = func()
end_time = time.time()
print(f"Elapsed time: {(end_time - start_time) / time_unit}")
return result
return wrapper
return decorator
In this case, the timing_decorator function takes an argument specifying the time unit, and
returns a new function that takes a function as an argument and returns a new function that
wraps the original function. The wrapper function calculates the elapsed time and divides it by
the time unit argument before printing it.
Decorators with arguments can be used in a variety of scenarios. For instance, you might use a
decorator with arguments to enforce different levels of logging depending on the function or
method being called, or to validate different types of inputs depending on the specific use case.

## Decorator Classes
In addition to using functions as decorators in Python, you can also use classes as decorators.
Decorator classes are defined by implementing the __call__ method, which allows instances
of the class to be called like functions.
Decorator classes are useful when you need to maintain state across multiple calls to the
decorated function or when you want to reuse the same decorator across multiple functions.
For example, you might use a decorator class to count the number of times a function is called:

class CallCounter:
def __init__(self, func):
self.func = func
self.counter = 0
def __call__(self, *args, **kwargs):
self.counter += 1
return self.func(*args, **kwargs)
In this example, the CallCounter class takes a function as an argument and stores it as an
instance variable. The __call__ method increments the counter each time the function is
called and returns the result of calling the original function.
To use the decorator class, you would instantiate it with the function you want to decorate, and
then call the resulting instance:
@CallCounter
def my_function():
# function body
my_function() # calls my_function and increments the counter

## Chaining Decorators
In addition to applying multiple decorators to a single function, you can also chain decorators
together. Decorator chaining allows you to apply multiple decorators to a single function in a
specific order.
To chain decorators together, you can simply apply each decorator to the previous decorator's
result using the @ syntax. For example, to chain three decorators together, you might write:
@decorator1
@decorator2
@decorator3
def my_function():
# function body

In this case, the my_function function is first wrapped by the decorator3 function, then by the
decorator2 function, and finally by the decorator1 function. The result is a function that has
been modified by all three decorators.
In summary, function decorators are a powerful tool in Python that allow you to modify or
enhance the behavior of functions at runtime. By using the @ syntax, writing your own
decorators, applying multiple decorators to a single function, using decorators with
arguments, and exploring decorator classes and chaining, you can create more efficient,
readable, and maintainable code. In the next chapter, we'll explore class decorators and how to
use them in Python.

## Class Decorators
In addition to function decorators, Python also supports class decorators. Class decorators are
similar to function decorators, but they allow you to modify or enhance the behavior of classes
at runtime. In this chapter, we'll cover the basics of class decorators, including how to apply
them using the @ symbol, how to write your own class decorators, how to apply multiple
decorators to a single class, and how to use decorators with arguments.

## Decorating Classes with the @ Symbol
The @ symbol can also be used to apply decorators to classes in Python. When a decorator is
applied to a class, the decorator function takes the original class as an argument and returns a
new class that wraps it. This new class can add functionality to the original class, such as
logging or timing.

For example, to apply a logging decorator to a class, you might write:
@logging_decorator
class MyClass:
# class body
In this case, the MyClass class is wrapped by the logging_decorator function, which adds
logging functionality.

## Writing Your Own Class Decorators
You can also write your own class decorators in Python. Class decorators are simply functions
that take a class as an argument and return a new class that wraps the original class. This can
be useful when you need to add functionality to existing classes, or when you want to create
more flexible and reusable code.
To write your own class decorator, you need to define a function that takes a class as an
argument and returns a new class that wraps the original class. This new class can add any
functionality that you want, such as logging or validation. For example, to write a decorator
that adds a description attribute to a class, you might write:

def description_decorator(cls):
cls.description = 'This is a class with a description attribute.'
return cls
This decorator function takes a class as an argument, wraps it in a new class that adds a
description attribute, and returns the new class. You can then apply this decorator to any class
that you want to add a 'description' attribute to.

## Applying Multiple Decorators to a Single Class
You can also apply multiple decorators to a single class in Python. When you apply multiple
decorators, the class is wrapped by each decorator in turn, from the inside out. This can be
useful when you need to apply multiple types of functionality to a class, such as logging,
timing, and input validation.
To apply multiple decorators to a single class, you simply stack them on top of each other
using the @ syntax. For example, to apply both a logging decorator and a timing decorator to a
class, you might write:
@logging_decorator
@timing_decorator
class MyClass:
# class body
In this case, the MyClass class is first wrapped by the timing_decorator function, which adds
timing functionality, and then wrapped by the logging_decorator function, which adds
logging functionality.

## Decorators with Arguments
You can also create decorators that take arguments in Python. To do this, you need to define a
decorator function that takes arguments, and then return a new function that takes a class as
an argument and returns a new class that wraps the original class. This can be useful when you
need to customize the behavior of a decorator for different use cases.
For example, to create a decorator that adds a description attribute to a class with a custom
description, you might write:

def description_decorator(description):
def decorator(cls):
cls.description = description
return cls
return decorator
In this case, the description_decorator function takes an argument specifying the custom
description, and returns a new function that takes a class as an argument and returns a new
class that wraps the original class. The wrapper class adds a description attribute with the
custom description to the original class.
To use the decorator with arguments, you would call it with the custom description and then
apply the resulting decorator function to the class:
@description_decorator('This is a custom description.')
class MyClass:
# class body
In this example, the MyClass class is wrapped by the description_decorator function with the
custom description 'This is a custom description’.
In summary, class decorators are a powerful tool in Python that allow you to modify or
enhance the behavior of classes at runtime. By using the @ syntax, writing your own
decorators, applying multiple decorators to a single class, and using decorators with
arguments, you can create more efficient, readable, and maintainable code. In the next
chapter, we'll explore advanced decorator topics and best practices in Python.




