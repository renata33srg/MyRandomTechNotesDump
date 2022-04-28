# Python

## Definition

Python is a high-level **compiled-interpreted** programming language that supports multiple programming paradigms: imperative, object-oriented, and functional. It is a dynamically typed language with automatic memory management.  

> Brief concepts
> - Interpreted Language: the implementation of the python language on each computer is done through a process in which one of the main components is the interpreter (Compiler + Python Virtual Machine).
> - Supports Multiple Programming Paradigms:  
>    - Imperative or Procedural: Instructions are passed to the computer in the sequence they are to be executed.  
>    - Object Oriented: It uses structures called classes and objects and its main feature is to allow cross-platform programming.  
>    - Functional: Its main characteristic is the use of structures called functions . These functions separate code into blocks that each have a specific task.  
> - Dynamic Typing: the program itself “understands” what type of data is being used and therefore its type does not need to be previously declared.
> - Automatic Memory Management: Python constantly maintains or “cleans” unused memory through mechanisms such as the garbage collector and Reference Counting . That way, the programmer doesn't have to worry about manually managing memory.  

>
> ## PEP-8 and The Zen of Python
>
> PEP-8 (Python Enhancement Proposals) gives coding conventions for the Python code comprising the standard library in the main Python distribution.  
> The Zen of Python (PEP-20) is a collection of '19' guiding principles that influence the design of Python.    
>
>> *Beautiful is better than ugly*.  
>>    Perhaps the main reason for Python's popularity is how easy it is to use and understand, so the beauty of the code is at the heart of this language. In this quote, beauty is synonym of easy understanding.  
>> *Explicit is better than implicit*.  
>>    The best characteristic of any code is the clarity in what it proposes to do, no matter how verbose it may be. No gimmicks or hidden triggers, everything has to be at hand and easily accessible.  
>> *Simple is better than complex* **->** *Complex is better than complicated*.  
>>    All can be done using simple and/or complex techniques. Simple problems can use simple solutions, and complex problems will almost always require complex solutions. Always prefer simplicity over complexity, but sometimes using simple solutions to complex problems can make them complicated, so understand how far the limits of this simplicity can go. 
>> *Flat is better than nested*.  
>>    Organization is important, and categorizing what you have is important, as long as organization doesn't become bureaucracy. It's okay to have a code on one page instead of separating it into several files, if this is something pragmatic and organized, and doesn't generate unnecessary bureaucracy (and not unnecessary complexity and complication)  
>> *Sparse is better than dense*.  
>>    Most programmers have always made a point of putting as much function into as little code as possible. This becomes crazy, high density of function per line code makes something extremely complicated to understand. It becomes more palatable to separate and break it into several lines.  
>> *Readability counts*.  
>>    No memory shortage excuses, don't shorten variable names. Give easy-to-understand and complete names to variables and functions. This makes the code more pleasant and understandable, as if it was a communication language, after all someone will actually read it there at some point.   
>> *Special cases aren't special enough to break the rules* **and** *Although practicality beats purity*.  
>>    Programming is full of “best practices” that programmers should look for in their code. Bypassing these practices for a quick hack can be tempting, but it can lead to a rat's nest of inconsistent and unreadable code. However, leaning back to adhere to the rules can result in unreadable and highly abstract code. The Java programming language's attempt to adjust all code to its object-oriented paradigm often results in a lot of standard code for even the smallest program. Walking the line between these two aphorisms becomes easier with experience. And over time, you'll not only learn the rules, you'll also learn when to break them.   
>> *Errors should never pass silently* **->** *Unless explicitly silenced*.  
>>    Functions should have exceptions, where applicable, it is preferable for a program to crash quickly when it encounters an error, rather than ignoring it and hiding it until it gets worse and worse (and harder to debug over time). Well, at least if you're silencing these errors, make sure you're doing it consciously, and with highly managed risks.  
>> *In the face of ambiguity, refuse the temptation to guess*.  
>>    Computers sometimes make us superstitious, as if everything were a matter of luck, just turn the system off and on to get it working again. To solve problems it is necessary to debug it and find the root cause and never mask it.   
>> *There should be one—and preferably only one—obvious way to do it*.  
>>    The idea is that if you have more than one way of doing the same thing, it can be a double-edged sword: having three or four ways of writing also means the effort of having to learn to read three or four different ways of doing the same thing. It gets more complex without actually being more efficient.   
>> *Although that way may not be obvious at first unless you're Dutch*.  
>>    Guido van Rossum, the creator of Python, was Dutch.  
>> *Now is better than never* **->** *Although never is often better than *right* now*.  
>>    Of course, code that can be finished in a timely manner is better than one that takes turns and turns and never gets done. However, all of these situations are far better than one that needs to be ready right away and full of problems that are incorrigible and bring more headaches.  
>> *If the implementation is hard to explain, it's a bad idea* **->** *If the implementation is easy to explain, it may be a good idea*.  
>>    As much as the implementation allows for very high performance computing, if it is impossible for other programmers to understand and debug the code, it will certainly be a bad idea in the short, medium and especially in the long term. Not that a code that is easy to explain guarantees its quality, but it is already an excellent start, and a good principle for it to be easily and incrementally possible for improvement in the medium and long term. Code support is critical in programming.  
>> *Namespaces are one honking great idea—let's do more of those!*  
>>    Namespaces are critical to preventing conflicts between local and global modules. Use and abuse them to avoid context problems. But this is just to avoid function and variable name problems, beware of bureaucracy and with all '18' principles above, it can make the code more complex if used incorrectly.  
>
>


## How do I run a Python script?

Python follows both compilation and interpretation as strategy for program execution in spite of being known as an *interpreted* programming language. In other words, Python scripts have to be processed by another "program" called **Python interpreter**.  
The Python interpreter is made up of compiler and Python Virtual Machine (PVM). It can be used as a **REPL (read-eval-print-loop)**, interactively, on the command line and, alternatively, **is possible to invoke Python with scripts of Python code**. In both cases, *the REPL interpreter parses the input and then compiles it into an intermediate language called Bytecode* (lower-level, platform independent, representation of the source code) and then this Bytecode is sent to the **PVM** to be interpreted and executed.  
  
> Steps executed when a Python code run
>
> 1. Compiler receives the source code 
> 2. Compiler checks the syntax of each line in the source code
>     2.1 If the compiler encounters an error, it halts the translation process with an error message (*Syntax error*)
>     2.2 Else if the instruction is well formatted, then it translates the source code to Bytecode
> 3. Bytecode is sent to the Python Virtual Machine
> 4. The Python Virtual Machine (PVM) receives as input the Bytecode along with another system inputs and the Library Modules
> 5. PVM executes the Bytecode
>     5.1 If any error occurs, it displays an error message (Runtime error)
>     5.2 Otherwise, if there is no error in execution, it results in the output
> 

The process of interpret and compile Python source code is called **implementation of Python**. The standard Python implementation is the  *CPython* (it comes by default with Python's installation), but it's possible to use different implementations, as Jython, IronPython, PyPy and so on.   
- CPython is an implementation of Python written in *C* that interprets and compiles code into Bytecode to run on the PVM.  
- Jython is an implementation of Python written in *Java* that interprets and compiles code into Java Bytecode to run on the Java Virtual Machine (JVM). So is possible to easily work with Java programs since you can call, as well as utilize, Java functions and classes directly from Jython without any additional effort which is immensely beneficial as Python users can get access into the enormous ecosystem of libraries and frameworks that come along with Java. Jython enables the use of Java class library functions from the Python program.  
- IronPython is an implementation of Python written in *C#* that interprets and compiles code into Common Language Runtime (CLR) to run on the .NET Virtual Machine. So other .NET languages can use the Python code easily as it uses .NET Framework, and Python Libraries.   
- PyPy is an implementation of Python written in *RPython* (Restricted Python) that uses something called JIT (Just-in-Time) Compilation, where the Bytecode is compiled into native machine code at runtime and so it speeds up the Python code execution process.   

> There are some details to keep in mind when it's decided to use non-default implementation of Python like:   
> - What's the project's target architecture?  
> - What are the project performance needs?  
> - Is it necessary to use the latest features of the language?  
> - How memory management happens (e.g. Garbage collector)?   
> - Does the project depend on packages that use extensions written in C?   
>

> ## Notes about file extensions
>
>> *.pyc* file: is the compiled bytecode generated by the interpreter. In case of importing modules, python build a *\*.pyc* that contains the bytecode to make importing again later easier (and faster)
>> *.pyd* file (Python Dynamic Module):  is platform-specific to the Windows class of operating systems. A *\*.pyd* file is a dynamic link library (DLL) file containing Python code (a module or a set of modules) which can be called out to and used by other Python applications. In order to make this library available to other Python programs, it is packaged as a dynamic link library. Dynamic link libraries (DLLs) are Windows code libraries that are linked to calling programs at runtime. 
>
> 

- So, how do you arrange for the interpreter to handle your Python? First, you need to make sure that your command window recognises the word “py” as an instruction to start the interpreter. If you have opened a command window, you should try entering the command *py* and hitting return:  

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

Now that we know the *py* command is recognized, you can give your Python script to it. You’ll have to give either an *absolute or a relative path to the Python script*. Let’s say your Python script is located in your desktop and is named *hello.py*, and your command prompt is nicely opened in your home directory so you’re going to do something similar to:  

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

---

## Definitions
 
**Expressions**: are representations of something, like: a string, a number or a class instance. Any value is an expression.  
**Statements**: are anythings that do some task, like: the assignment to a variable or a function call.   
**Containers**: are objects that contain references to other objects, like sequences (e.g lists or tuples) and mappings (e.g. dictionaries).  

**Sequence**: represents finite ordered sets indexed by non-negative numbers. The function *len()* returns the number of items of a sequence. When the length of a sequence is n, the index set contains the numbers 0, 1, …, n-1. Item **i** of sequence **a** is selected by *a[i]* and/or using integer indices via the *\a.__getitem__(i)*.  
Sequences also support slicing: * a __[ __i:j__] * selects all items with index k such that i <= k < j. When used as an expression, a slice is a sequence of the same type. This implies that the index set is renumbered so that it starts at '0'. Some sequences also support “extended slicing” with a third “step” parameter: *a[i:j:k]* selects all items of a with index x where x = i + n*k, n >= 0 and i <= x < j.  
Sequences are distinguished according to their mutability:
> **Immutable sequence**: object that cannot change once it is created. (If the object contains references to other objects, these other objects may be mutable and may be changed; however, the collection of objects directly referenced by an immutable object cannot change.). Examples: strings, tuples, bytes.    
> **Mutable sequences**: object that can be changed after they are created. The subscription and slicing notations can be used as the target of assignment and del (delete) statements. Examples: lists, byte arrays.

**Mapping**: represents finite sets of objects indexed by arbitrary index sets. The subscript notation *a[k]* selects the item indexed by k from the mapping a; this can be used in expressions and as the target of assignments or del statements. The function *len()* returns the number of items in a mapping. There is currently a single intrinsic mapping type: Dictionaries.  
> These represent finite sets of objects indexed by nearly arbitrary values. The only types of values not acceptable as keys are values containing lists or dictionaries or other mutable types that are compared by value rather than by object identity, the reason being that the efficient implementation of dictionaries requires a key’s hash value to remain constant. Numeric types used for keys obey the normal rules for numeric comparison: if two numbers compare equal (e.g., 1 and 1.0) then they can be used interchangeably to index the same dictionary entry.  
> Dictionaries didn't preserve insertion order in versions of Python before 3.6. Above that version, dictionaries preserve insertion order, meaning that keys will be produced in the same order they were added sequentially over the dictionary. Replacing an existing key does not change the order, however removing a key and re-inserting it will add it to the end instead of keeping its old place. Dictionaries are mutable; they can be created by the {...} notation.  



**Magic Methods**: are methods that are not directly invoked by the programmer when writing a code. They are system calls that are invoked on the back end automatically. The difference between magic and normal methods is that double underscores surround magic methods. That is why they are also called dunder methods. Dunder here means double underscores. *Magic methods are also used for operator overloading*. Example: The use of __getitem__() in a class allows the instances of a class to use the indexer operator [ ] with the reference variables of a class for accessing the value of a list, dictionary, or tuple from a specific index.