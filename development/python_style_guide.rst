Python Coding Style Guide
===========================

This guide contains the rules and recommendations considered current best
practice when writing code for Suisei Entertainment products.

Python is the main programming language used in most Suisei Entertainment
products. Although the Python programming language defines its own style guide
in the form of `PEP8 <https://www.python.org/dev/peps/pep-0008/>`_, there are
other good style guides out there for the language, for example the `Google
Python Style Guide <https://google.github.io/styleguide/pyguide.html>`_. The
coding style used by Suisei Entertainment is mainly based on these two guides.

The rules and recommendations described here are not strictly enforced, but
they are checked by pylint when the linter is executed.

.. contents::

How to Use This Guide
-------------------------------------------

Pylint
-------------------------------------------

Always make sure to run pylint on your code to identify potential errors early
on. It finds problems that are typically caught by a compiler for less dynamic
languages like C and C++. Because of the dynamic nature of Python, some
warnings may be incorrect; however, spurious warnings should be fairly
infrequent.

In case of false positives pylint warnings can be suppressed.

To suppress warnings, you can set a line-level comment:

.. code-block:: python

    dict = 'something awful'  # Bad Idea... pylint: disable=redefined-builtin

Recommendations when suppressing a pylint warning:

* Always suppress the warning in the narrowest possible scope, typically just
  in the single code line causing the false positive. This can be done by
  using the control statement in an inline comment. If it is not possible, you
  can disable the warning in function scope, and only disable warnings in file
  scope if there is absolutely no other option.
* Always prefer the symbolic name over the alphanumeric code when suppressing
  warnings, they are easier to understand.
* Add additional comments next to the control statement that explains why they
  are necessary.
* Always use ``#pylint: disable`` instead of the deprecated ``#pylint:
  disable-msg``.

Coverage
-------------------------------------------

Always make sure to run coverage test on your code to make sure that it has
the necessary test coverage. The minimum test coverage expected on any modules
of the Tenshi platform is 90%+.

Imports
-------------------------------------------

Use ``import`` for modules and packages only. Do not use relative names in
imports. Even if the module is in the same package, use the full package name.
This helps prevent unintentionally importing a package twice.

Recommendations when using import:

* Use ``import x`` for importing packages and modules.
* Use ``from x import y`` where x is the package prefix and y is the module
  name with no prefix.
* Use ``from x import y as z`` if two modules named y are to be imported or if
  y is an inconveniently long name.

Packages
-------------------------------------------

Import each module using the full pathname location of the module.

Exceptions
-------------------------------------------

Exceptions are allowed and are the preferred way to handle application errors,
but they must to be used with care.

Recommendations when using exceptions:

* Raise exceptions like this: ``raise MyException('Error message')`` or ``raise
  MyException``. Do not use the two-argument form (``raise MyException,
  'Error message'``) or deprecated string-based exceptions (``raise 'Error
  message')``.
* Modules or packages should define their own domain-specific base exception
  class, which should inherit from the built-in Exception class.
* Never use catch-all ``except:`` statements, or catch ``Exception`` or
  ``StandardError``, unless you are re-raising the exception or in the
  outermost block in your thread (and printing an error message). Python is
  very tolerant in this regard and except: will really catch everything
  including misspelled names, sys.exit() calls, Ctrl+C interrupts, unittest
  failures and all kinds of other exceptions that you simply don't want
  to catch.
* Minimize the amount of code in a try/except block. The larger the body of
  the try, the more likely that an exception will be raised by a line of code
  that you didn't expect to raise an exception. In those cases, the
  try/except block hides a real error.
* Use the ``finally`` clause to execute code whether or not an exception is
  raised in the try block. This is often useful for cleanup, i.e., closing a
  file.
* When capturing an exception, use as rather than a comma. For example:

.. code-block:: python

    try:
      raise Error
    except Error as error:
      pass

Global Variables
-------------------------------------------

Avoid global variables in favor of class variables. Some exceptions are:

* Default options for scripts.
* Module-level constants. For example: PI = 3.14159. Constants should be named
  using all caps with underscores; see Naming below.
* It is sometimes useful for globals to cache values needed or returned by
  functions.
* If needed, globals should be made internal to the module and accessed through
  public module level functions; see Naming below.


Nested/Local/Inner Classes and Functions
-------------------------------------------

Nested/local/inner classes and functions are fine. A class can be defined
inside of a method, function, or class. A function can be defined inside a
method or function. Nested functions have read-only access to variables defined
in enclosing scopes. Allows definition of utility classes and functions that
are only used inside of a very limited scope.


List Comprehensions
-------------------------------------------

List comprehensions and generator expressions provide a concise and efficient
way to create lists and iterators without resorting to the use of map(),
filter(), or lambda. They are okay to use for simple cases, but should be
avoided in more complex cases as they can be hard to read and understand. As a
general rule, each portion must fit on one line: mapping expression, for
clause, filter expression. Multiple for clauses or filter expressions are not
permitted. Use loops instead when things get more complicated.

Good:

.. code-block:: python

  result = []
  for x in range(10):
      for y in range(5):
          if x * y > 10:
              result.append((x, y))

  for x in xrange(5):
      for y in xrange(5):
          if x != y:
              for z in xrange(5):
                  if y != z:
                      yield (x, y, z)

  return ((x, complicated_transform(x))
          for x in long_generator_function(parameter)
          if x is not None)

  squares = [x * x for x in range(10)]

  eat(jelly_bean for jelly_bean in jelly_beans
      if jelly_bean.color == 'black')

Bad:

.. code-block:: python

  result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]

  return ((x, y, z)
          for x in xrange(5)
          for y in xrange(5)
          if x != y
          for z in xrange(5)
          if y != z)


Default Iterators and Operators
-------------------------------------------

Use default iterators and operators for types that support them, like lists,
dictionaries, and files.

The built-in types define iterator methods, too. Prefer these methods to
methods that return lists, except that you should not mutate a container while
iterating over it.

Good:

.. code-block:: python

  for key in adict: ...
  if key not in adict: ...
  if obj in alist: ...
  for line in afile: ...
  for k, v in dict.iteritems(): ...

Bad:

.. code-block:: python

  for key in adict.keys(): ...
  if not adict.has_key(key): ...
  for line in afile.readlines(): ...

Generators
-------------------------------------------

Use generators as needed. Fine. Use "Yields:" rather than "Returns:" in the doc
string for generator functions.

Lambda Functions
-------------------------------------------

Lambdas define anonymous functions in an expression, as opposed to a statement.
They are often used to define callbacks or operators for higher-order functions
like ``map()`` and ``filter()``.

They are okay for one-liners as they can be convenient. But they are harder to
read and debug than local functions. The lack of names means stack traces are
more difficult to understand. Expressiveness is limited because the function
may only contain an expression.

If the code inside the lambda function is any longer than 60–80 chars, it's
probably better to define it as a regular (nested) function.

For common operations like multiplication, use the functions from the operator
module instead of lambda functions. For example, prefer ``operator.mul`` to
``lambda x, y: x * y``.

Conditional Expressions
-------------------------------------------

Conditional expressions are mechanisms that provide a shorter syntax for if
statements. For example: ``x = 1 if cond else 2``.

They can be shorter and more convenient than an if statement, but may be harder
to read than an if statement. The condition may be difficult to locate if the
expression is long.

Okay to use for one-liners. In other cases prefer to use a complete if
statement.

Default Argument Values
-------------------------------------------

You can specify values for variables at the end of a function's parameter list,
e.g., ``def foo(a, b=0)``:. If foo is called with only one argument, b is set
to 0. If it is called with two arguments, b has the value of the second
argument.

Often you have a function that uses lots of default values, but - rarely - you
want to override the defaults. Default argument values provide an easy way to
do this, without having to define lots of functions for the rare exceptions.
Also, Python does not support overloaded methods/functions and default
arguments are an easy way of "faking" the overloading behavior.

Default arguments are evaluated once at module load time. This may cause
problems if the argument is a mutable object such as a list or a dictionary.
If the function modifies the object (e.g., by appending an item to a list), the
default value is modified.

Do not use mutable objects as default values in the function or method
definition.

Good:

.. code-block:: python

  def foo(a, b=None):
     if b is None:
         b = []

Bad:

.. code-block:: python

  def foo(a, b=[]):
         ...
  def foo(a, b=time.time()):  # The time the module was loaded???
         ...
  def foo(a, b=FLAGS.my_thing):  # sys.argv has not yet been parsed...
         ...

Properties
-------------------------------------------

