
# Coding Challenge: Use a Decorator like a Function

### The Challenge

Implement the decorator `add_two` in the following code fragment:

    @add_two
    def get_number(a):
        return a

    print(get_number(40))
    print(add_two(40))

Leave the above code unchanged!

You have mastered this challenge when your output is:

    42
    42


### What you can practise in this coding challenge

* decorator functions
* decorator classes
* metaclasses


### Motivation

This is a challenge for advanced Python users. 

A **decorator class** and a **function** are two different things, right?
In Python, not necessarily! Basically, you can make anything in Python mimick anything else. 

Advocates of statically typed languages will cringe here, of course. On the other hand, in this challenge you see one of the hinges that makes it easy to combine Python with almost anything else.

Implementing a decorator that works like a function may help you to understand dynamic typing in Python at a deeper level.

My own solution worked on Python3.

### Optional goals

If this was too easy for you, try the following constraints:

#### 1. The decorator must be implemented as a class

This will require using a `metaclass`.

#### 2. The decorator must work if piled up multiple times

So that:

    @add_two
    @add_two
    def get_number(x):
        return x

    get_number(40)

results in `42`.


#### Have fun!
