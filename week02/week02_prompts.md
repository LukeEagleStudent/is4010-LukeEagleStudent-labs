# Lab 02
## Problem 1: Debugging
## My Prompt:

Context: This is my buggy python code:
def sum_of_evens(numbers):
    """Calculate the sum of all even numbers in a list.

    Parameters
    ----------
    numbers : list of int
        A list of integers.

    Returns
    -------
    int
        The sum of all even numbers in the list.
    """
    total = 0
    for num in numbers:
        if num % 2 == 1:  # This line has a bug!
            total += num
    return total
Persona: You are a senior python developer
Task: Debug the code
Format: Please return a block of code

## ChatGPT Response:

def sum_of_evens(numbers):
    """Calculate the sum of all even numbers in a list.

    Parameters
    ----------
    numbers : list of int
        A list of integers.

    Returns
    -------
    int
        The sum of all even numbers in the list.
    """
    if not isinstance(numbers, list):
        raise TypeError("numbers must be a list of integers")

    total = 0
    for num in numbers:
        if not isinstance(num, int):
            raise TypeError("all elements in numbers must be integers")

        if num % 2 == 0:  # Fixed: check for even numbers
            total += num

    return total

## What I learned:
The modulo operator functions by returning the remainder of a division equation, so using it to find a remainder of 1 with a divisor of 2 will trigger when it finds an odd number, and with a remainder of 0 it will trigger on an even number
## Problem 2: Refactoring
## My Prompt:

Context: This is my convoluted python code
def get_names_of_adults(users):
    """Given a list of user dictionaries, returns a list of names of users
    who are 18 or older.

    Parameters
    ----------
    users : list of dict
        List of user dictionaries with 'name' and 'age' keys.

    Returns
    -------
    list of str
        Names of users who are 18 or older.
    """
    results = []
    for i in range(len(users)):
        if users[i]['age'] >= 18:
            results.append(users[i]['name'])
    return results
Persona: You are still a senior python developer
Task: Please refactor the code to be more clear, concise, and idiomatic
Format: Return a block of code

## ChatGPT Response:

def get_names_of_adults(users):
    """Return a list of names for users who are 18 or older.

    Parameters
    ----------
    users : list of dict
        Each dictionary must contain 'name' (str) and 'age' (int).

    Returns
    -------
    list of str
        Names of users who are 18 or older.
    """
    if not isinstance(users, list):
        raise TypeError("users must be a list of dictionaries")

    return [
        user["name"]
        for user in users
        if isinstance(user, dict)
        and "age" in user
        and "name" in user
        and isinstance(user["age"], int)
        and user["age"] >= 18
    ]
## What I learned:
Conversational AI can be used to make code more concise, instead of setting a definition for results and returning results, it just returns the result naturally. It also appends multiple and statements instead of searching for all criteria in a range
## Problem 3: Documenting
## My Prompt:

Context: This is my python code:
def calculate_area(length, width):
    if length <= 0 or width <= 0:
        raise ValueError("Length and width must be positive numbers.")
    return length * width

The function raises a ValueError for invalid inputs
Persona: You are still a senior python developer
Task: Please document the code
Format: Use professional NumPy-style docstring

## ChatGPT Response:

def calculate_area(length, width):
    """
    Calculate the area of a rectangle.

    Parameters
    ----------
    length : int or float
        The length of the rectangle. Must be a positive number.
    width : int or float
        The width of the rectangle. Must be a positive number.

    Returns
    -------
    int or float
        The calculated area of the rectangle (length * width).

    Raises
    ------
    ValueError
        If either `length` or `width` is less than or equal to zero.

    Examples
    --------
    >>> calculate_area(5, 3)
    15
    >>> calculate_area(2.5, 4)
    10.0
    >>> calculate_area(-1, 5)
    Traceback (most recent call last):
        ...
    ValueError: Length and width must be positive numbers.
    """
    if length <= 0 or width <= 0:
        raise ValueError("Length and width must be positive numbers.")
    return length * width

## What I learned:
This lab has given me a good insight into professional NumPy documenting, that showcases how functions are named and described so that future developers or even AI agents are not confused

