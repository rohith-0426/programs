# PYTHON PACKAGES                                                   
![Alt text]( https://www.python-course.eu/images/packages_script_350w.webp "a title")



In this article, you'll learn to divide your code base into clean, efficient modules using Python packages. Also, you'll learn to import and use your own or third party packages in a Python program.

# INTRODUCTION

We don't usually store all of our files on our computer in the same location. We use a well-organized hierarchy of directories for easier access.

Similar files are kept in the same directory, for example, we may keep all the songs in the "music" directory. Analogous to this, Python has packages for directories and modules for files.

As our application program grows larger in size with a lot of modules, we place similar modules in one package and different modules in different packages. This makes a project (program) easy to manage and conceptually clear.

Similarly, as a directory can contain subdirectories and files, a Python package can have sub-packages and modules.

A directory must contain a file named __init__.py in order for Python to consider it as a package. This file can be left empty but we generally place the initialization code for that package in this file.

Here is an example. Suppose we are developing a game. One possible organization of packages and modules could be as shown in the figure below.



![Alt text]( https://www.includehelp.com/python/images/python-packages-example.jpg "a title")



> Importing module from a package

We can import modules from packages using the dot (.) operator.

For example, if we want to import the start module in the above example, it can be done as follows:
> import Game.Level.start

Now, if this module contains a function named select_difficulty(), we must use the full name to reference it.

> Game.Level.start.select_difficulty(2)

If this construct seems lengthy, we can import the module without the package prefix as follows:

> from Game.Level import start

We can now call the function simply as follows:

> start.select_difficulty(2)

Another way of importing just the required function (or class or variable) from a module within a package would be as follows:

> from Game.Level.start import select_difficulty


Now we can directly call this function.

> select_difficulty(2)

Although easier, this method is not recommended. Using the full namespace avoids confusion and prevents two same identifier names from colliding.

While importing packages, Python looks in the list of directories defined in sys.path, similar as for module search path.


# A SIMPLE EXAMPLE


![Alt text]( https://www.python-course.eu/images/packages_300w.webp "a title")

We will demonstrate with a very simple example how to create a package with some Python modules. First of all, we need a directory. The name of this directory will be the name of the package, which we want to create. We will call our package "simple_package". This directory needs to contain a file with the name __init__.py. This file can be empty, or it can contain valid Python code. This code will be executed when a package is imported, so it can be used to initialize a package, e.g. to make sure that some other modules are imported or some values set. Now we can put all of the Python files which will be the submodules of our module into this directory. We create two simple files a.py and b.py just for the sake of filling the package with modules.

The content of a.py:

>def bar():
    print("Hello, function 'bar' from module 'a' calling")

The content of b.py:

> def foo():
    print("Hello, function 'foo' from module 'b' calling")

We will also add an empty file with the name __init__.py inside of simple_package directory.

Let's see what happens, when we import simple_package from the interactive Python shell, assuming that the directory simple_package is either in the directory from which you call the shell or that it is contained in the search path or environment variable "PYTHONPATH" (from your operating system):

> import simple_package

>simple_package/a
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-3-347df8a711cc> in <module>
----> 1 simple_package/a

NameError: name 'a' is not defined
simple_package/b
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-4-e71d2904d2bd> in <module>
----> 1 simple_package/b

NameError: name 'b' is not defined
We can see that the package simple_package has been loaded but neither the module "a" nor the module "b"! We can import the modules a and b in the following way:

>from simple_package

>import a, b a.bar()

>b.foo()

Hello, function 'bar' from module 'a' calling
Hello, function 'foo' from module 'b' calling
As we have seen at the beginning of the chapter, we can't access neither "a" nor "b" by solely importing simple_package.

Yet, there is a way to automatically load these modules. We can use the file __init__.py for this purpose. All we have to do is add the following lines to the so far empty file __init__.py:


>import simple_package.a

>import simple_package.b

It will work now:

***import simple_package***

***simple_package.a.bar()***

***simple_package.b.foo()***

Hello, function 'bar' from module 'a' calling
Hello, function 'foo' from module 'b' calling


# DIFFERENCE BETWEEN MODULES AND PACKAGES

![Alt text]( https://i0.wp.com/techvidvan.com/tutorials/wp-content/uploads/sites/2/2021/05/modules-vs-packages.jpg?fit=1200%2C628&ssl=1 "a title")