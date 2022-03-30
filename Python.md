# Python FAQ

## How do I run a Python program under Windows?

You need to realize that your Python scripts have to be processed by another program called the Python interpreter. The interpreter reads your script, compiles it into bytecodes, and then executes the bytecodes to run your program.  

- So, how do you arrange for the interpreter to handle your Python? First, you need to make sure that your command window recognises the word “py” as an instruction to start the interpreter. If you have opened a command window, you should try entering the command _py_ and hitting return:  

```sh
C:\Users\YourUser> py
```

You should see something like:  

```sh
Python 3.6.4 (v3.6.4:d48eceb, Dec 19 2017, 06:04:45) [MSC v.1900 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
```

You have started the interpreter in “**interactive mode**”. That means you can enter Python statements or expressions interactively and have them executed or evaluated while you wait. This is one of Python’s strongest features. Check it by entering a few expressions of your choice and seeing the results:  

```sh
>>> print("Hello")
Hello
>>> "Hello" * 3
'HelloHelloHello'
```

Many people use the interactive mode as a convenient yet highly programmable calculator. When you want to end your interactive Python session, call the **exit()** function or hold the Ctrl key down while you enter a Z, then hit the “Enter” key to get back to your Windows command prompt.  

You may also find that you have a Start-menu entry such as Start -> Programs -> Python 3.x -> Python (command line) that results in you seeing the >>> prompt in a new window. If so, the window will disappear after you call the **exit()** function or enter the Ctrl-Z character; Windows is running a single “python” command in the window, and closes it when you terminate the interpreter.  

Now that we know the _py_ command is recognized, you can give your Python script to it. You’ll have to give either an *absolute or a relative path to the Python script*. Let’s say your Python script is located in your desktop and is named *hello.py*, and your command prompt is nicely opened in your home directory so you’re going to do something similar to:  

```sh
C:\Users\YourName> py Desktop\hello.py
hello
```

## How do I make Python scripts executable?

On Windows, the standard Python installer already associates the *.py* extension with a file type (Python.File) and **gives that file type an open command that runs the interpreter** (C:\Program Files\Python\python.exe "%1" %*).   
This is enough to make scripts executable from the command prompt as ‘*foo.py*’. If you’d rather be able to execute the script by simple typing ‘*foo*’ with no extension you need to add *.py* to the **PATHEXT environment variable**.

## How do I make an executable from a Python script?

You don’t need the ability to compile Python to C code (or any other language) if all you want is a stand-alone program that users can download and run without having to install the Python distribution first. There are a number of tools that determine the set of modules required by a program and bind these modules together with a Python binary to produce a single executable.  

One is to use the **freeze tool**, which is included in the Python source tree as *Tools/freeze*. It converts Python byte code to C arrays; a C compiler you can embed all your modules into a new program, which is then linked with the standard Python modules.  

It works by scanning your source recursively for import statements (in both forms) and looking for the modules in the standard Python path as well as in the source directory (for built-in modules). It then **turns the bytecode for modules written in Python into C code (array initializers that can be turned into code objects using the marshal module) and creates a custom-made config file that only contains those built-in modules which are actually used in the program**. It then *compiles the generated C code and links it with the rest of the Python interpreter to form a self-contained binary which acts exactly like your script*.  

The following packages can help with the creation of console and GUI executables:  

| Package | Platform |
| [Nuitka](https://nuitka.net/) | (Cross-platform) |
| [PyInstaller](http://www.pyinstaller.org/) | (Cross-platform) |
| [PyOxidizer](https://pyoxidizer.readthedocs.io/en/stable/) | (Cross-platform) |
| [cx_Freeze](https://marcelotduarte.github.io/cx_Freeze/) | (Cross-platform) |
| [py2app](https://github.com/ronaldoussoren/py2app) | (macOS only) |
| [py2exe](http://www.py2exe.org/) | (Windows only) |

## Is a *.pyd file the same as a DLL?

- To answer this, first we need to know what is Bytecode and how the Python Virtual Machine works as well as what are the other types of python files
	
> ### Bytecode, Python Virtual Machine and .pyc / .pyo / .pyd files
>
>> Python ships with an interpreter that can be used as a **REPL (read-eval-print-loop)**, interactively, on the command line. Alternatively, **you can invoke Python with scripts of Python code**. In both cases, *the REPL interpreter parses your input and then compiles it into bytecode* (lower-level machine instructions) and then this bytecode is sent to the Python Virtual Machine to be interpreted and translated into machine-executable code.  
>>
>> However, it differs enough from other virtual machines like the Java virtual machine or the Erlang virtual machine. The virtual machine, in turn, interfaces with the operating system and actual hardware to execute native machine instructions while the Python Virtual Machine is just an interpreter of the bytecode generated translating it into machine-executable code.  
>>
>> The critical thing to keep in mind when you see *.pyc*, *.pyo* and *.pyd* file types, is that these are files created by the Python interpreter when it transforms code into compiled bytecode. **Compilation of Python source into bytecode is a necessary intermediate step in the process of translating instructions from source code in human-readable language into machine instructions that your operating system can execute**.  
>>
>> #### The .pyc File Type
>>
>> These files are automatically generated by the interpreter when you import a module, which speeds up future importing of that module. These files are therefore only created from a *.py* file if it is imported by another *.py* file or module.  
>>
>> Here is an example Python module which we want to import. This module calculates factorials.  
>>
>> ```python
# math_helpers.py

# a function that computes the nth factorial, e.g. factorial(2)
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

# a main function that uses our factorial function defined above
def main():
    print("I am the factorial helper")
    print("you can call factorial(number) where number is any integer")
    print("for example, calling factorial(5) gives the result:")
    print(factorial(5))

# this runs when the script is called from the command line
if __name__ == '__main__':
    main()
```
>>



Yes, *.pyd* files are dll’s, but there are a few differences. If you have a DLL named *foo.pyd*, then it must have a function *PyInit_foo()*. You can then write Python “import foo”, and Python will search for foo.pyd (as well as foo.py, foo.pyc) and if it finds it, will attempt to call PyInit_foo() to initialize it. You do not link your .exe with foo.lib, as that would cause Windows to require the DLL to be present.

Note that the search path for foo.pyd is PYTHONPATH, not the same as the path that Windows uses to search for foo.dll. Also, foo.pyd need not be present to run your program, whereas if you linked your program with a dll, the dll is required. Of course, foo.pyd is required if you want to say import foo. In a DLL, linkage is declared in the source code with __declspec(dllexport). In a .pyd, linkage is defined in a list of available functions.