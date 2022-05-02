# Python

## Index

1. [Definition](#definition)  
1.1. [Brief Concepts](#brief-concepts)  
1.2. [PEP-8 and The Zen of Python](#pep-8-and-the-zen-of-python)  
2. [How do I run a Python script?](#how-do-i-run-a-python-script)  
3. [How do I make Python scripts executable?](#how-do-i-make-python-scripts-executable)  
4. [How do I make an executable from a Python script?](#how-do-i-make-an-executable-from-a-python-script)  
5. [Language Semantic Concepts](#language-semantic-concepts)  
5.1 [Expressions](#expressions)  
5.2 [Statements](#statements)  
5.3 [Containers](#containers)  
5.4 [Sequence](#sequence)  
5.5 [Mapping](#mapping)  
5.6 [Magic Methods](#magic-methods)  
6. [Unit Tests](#unit-tests)  
6.1 [Writing Tests](#writing-tests)  
6.2. [Throwing Exceptions](#throwing-exceptions)  
6.3. [Asserting Values](#asserting-values)  
6.4. [Running Tests](#running-tests)  
6.5. [Environment](#environment)  
6.6. [Mocking Objects](#mocking-objects)  
6.6.1. [Mocking Class](#mock-class)  

  
---
  
## Definition

Python is a high-level **compiled-interpreted** programming language that supports multiple programming paradigms: imperative, object-oriented, and functional. It is a dynamically typed language with automatic memory management.  

### Brief concepts
 - Interpreted Language: the implementation of the python language on each computer is done through a process in which one of the main components is the interpreter (Compiler + Python Virtual Machine).
 - Supports Multiple Programming Paradigms:  
    - Imperative or Procedural: Instructions are passed to the computer in the sequence they are to be executed.  
    - Object Oriented: It uses structures called classes and objects and its main feature is to allow cross-platform programming.  
    - Functional: Its main characteristic is the use of structures called functions . These functions separate code into blocks that each have a specific task.  
 - Dynamic Typing: the program itself “understands” what type of data is being used and therefore its type does not need to be previously declared.
 - Automatic Memory Management: Python constantly maintains or “cleans” unused memory through mechanisms such as the garbage collector and Reference Counting . That way, the programmer doesn't have to worry about manually managing memory.  


### PEP-8 and The Zen of Python

PEP-8 (Python Enhancement Proposals) gives coding conventions for the Python code comprising the standard library in the main Python distribution.  
The Zen of Python (PEP-20) is a collection of '19' guiding principles that influence the design of Python (as follows).  
  
>  
> *__Beautiful is better than ugly__*  
>> Perhaps the main reason for Python's popularity is how easy it is to use and understand, so the beauty of the code is at the heart of this language. In this quote, beauty is synonym of easy understanding.   
>  
> *__Explicit is better than implicit__*   
>> The best characteristic of any code is the clarity in what it proposes to do, no matter how verbose it may be. No gimmicks or hidden triggers, everything has to be at hand and easily accessible.  
>  
> *__Simple is better than complex --> Complex is better than complicated__*  
>> All can be done using simple and/or complex techniques. Simple problems can use simple solutions, and complex problems will almost always require complex solutions. Always prefer simplicity over complexity, but sometimes using simple solutions to complex problems can make them complicated, so understand how far the limits of this simplicity can go.  
>    
> *__Flat is better than nested__*  
>> Organization is important, and categorizing what you have is important, as long as organization doesn't become bureaucracy. It's okay to have a code on one page instead of separating it into several files, if this is something pragmatic and organized, and doesn't generate unnecessary bureaucracy (and not unnecessary complexity and complication)  
>    
> *__Sparse is better than dense__*  
>> Most programmers have always made a point of putting as much function into as little code as possible. This becomes crazy, high density of function per line code makes something extremely complicated to understand. It becomes more palatable to separate and break it into several lines.  
>    
> *__Readability counts__*  
>> No memory shortage excuses, don't shorten variable names. Give easy-to-understand and complete names to variables and functions. This makes the code more pleasant and understandable, as if it was a communication language, after all someone will actually read it there at some point.   
>    
> *__Special cases aren't special enough to break the rules --> Although practicality beats purity__*  
>> Programming is full of “best practices” that programmers should look for in their code. Bypassing these practices for a quick hack can be tempting, but it can lead to a rat's nest of inconsistent and unreadable code. However, leaning back to adhere to the rules can result in unreadable and highly abstract code. The Java programming language's attempt to adjust all code to its object-oriented paradigm often results in a lot of standard code for even the smallest program. Walking the line between these two aphorisms becomes easier with experience. And over time, you'll not only learn the rules, you'll also learn when to break them.   
>    
> *__Errors should never pass silently --> Unless explicitly silenced__*  
>> Functions should have exceptions, where applicable, it is preferable for a program to crash quickly when it encounters an error, rather than ignoring it and hiding it until it gets worse and worse (and harder to debug over time). Well, at least if you're silencing these errors, make sure you're doing it consciously, and with highly managed risks.  
>    
> *__In the face of ambiguity, refuse the temptation to guess__*  
>> Computers sometimes make us superstitious, as if everything were a matter of luck, just turn the system off and on to get it working again. To solve problems it is necessary to debug it and find the root cause and never mask it.   
>    
> *__There should be one—and preferably only one—obvious way to do it__*  
>> The idea is that if you have more than one way of doing the same thing, it can be a double-edged sword: having three or four ways of writing also means the effort of having to learn to read three or four different ways of doing the same thing. It gets more complex without actually being more efficient.   
>    
> *__Although that way may not be obvious at first unless you're Dutch__*  
>> Guido van Rossum, the creator of Python, was Dutch.  
>    
> *__Now is better than never --> Although never is often better than *right* now__*  
>> Of course, code that can be finished in a timely manner is better than one that takes turns and turns and never gets done. However, all of these situations are far better than one that needs to be ready right away and full of problems that are incorrigible and bring more headaches.  
>    
> *__If the implementation is hard to explain, it's a bad idea --> If the implementation is easy to explain, it may be a good idea__*  
>> As much as the implementation allows for very high performance computing, if it is impossible for other programmers to understand and debug the code, it will certainly be a bad idea in the short, medium and especially in the long term. Not that a code that is easy to explain guarantees its quality, but it is already an excellent start, and a good principle for it to be easily and incrementally possible for improvement in the medium and long term. Code support is critical in programming.  
>    
> *__Namespaces are one honking great idea—let's do more of those!__*  
>> Namespaces are critical to preventing conflicts between local and global modules. Use and abuse them to avoid context problems. But this is just to avoid function and variable name problems, beware of bureaucracy and with all '18' principles above, it can make the code more complex if used incorrectly.  
>  
>


## How do I run a Python script?

Python follows both compilation and interpretation as strategy for program execution in spite of being known as an *interpreted* programming language. In other words, Python scripts have to be processed by another "program" called **Python interpreter**.  
The Python interpreter is made up of compiler and Python Virtual Machine (PVM). It can be used as a **REPL (read-eval-print-loop)**, interactively, on the command line and, alternatively, **is possible to invoke Python with scripts of Python code**. In both cases, *the REPL interpreter parses the input and then compiles it into an intermediate language called Bytecode* (lower-level, platform independent, representation of the source code) and then this Bytecode is sent to the **PVM** to be interpreted and executed.  
  
> Steps executed when a Python code runs  
>  
> 1. Compiler receives the source code  
> 2. Compiler checks the syntax of each line in the source code  
>  2.1 If the compiler encounters an error, it halts the translation process with an error message (*Syntax error*)  
>  2.2 Else if the instruction is well formatted, then it translates the source code to Bytecode  
> 3. Bytecode is sent to the Python Virtual Machine  
> 4. The Python Virtual Machine (PVM) receives as input the Bytecode along with another system inputs and the Library Modules  
> 5. PVM executes the Bytecode  
>  5.1 If any error occurs, it displays an error message (Runtime error)  
>  5.2 Otherwise, if there is no error in execution, it results in the output  
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
>  
> **Notes about file extensions**
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
Python 3.10.4 (tags/v3.10.4:9d38120, Mar 23 2022, 23:13:41) [MSC v.1929 64 bit (AMD64)] on win32
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
C:\Users\YourUser> py Desktop\hello.py
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
|--- | --- |
| [Nuitka](https://nuitka.net/) | (Cross-platform) |  
| [PyInstaller](http://www.pyinstaller.org/) | (Cross-platform) |  
| [PyOxidizer](https://pyoxidizer.readthedocs.io/en/stable/) | (Cross-platform) |  
| [cx_Freeze](https://marcelotduarte.github.io/cx_Freeze/) | (Cross-platform) |  
| [py2app](https://github.com/ronaldoussoren/py2app) | (macOS only) |  
| [py2exe](http://www.py2exe.org/) | (Windows only) |  

---

## Language Semantic Concepts  
  
### Expressions
Are representations of something, like: a string, a number or a class instance. Any value is an expression.  
  
### Statements
Are anythings that do some task, like: the assignment to a variable or a function call.   
  
### Containers
Are objects that contain references to other objects, like sequences (e.g lists or tuples) and mappings (e.g. dictionaries).  
  
### Sequence
Represents finite ordered sets indexed by non-negative numbers. Main features:  
  1. The function *len()* returns the number of items of a sequence.  
    1.1 When the length of a sequence is n, the index set contains the numbers 0, 1, …, n-1.   
    2.1 Item **i** of sequence **a** is selected by *a[i]* and/or using integer indices overriding via the *a.\_\__getitem\_\__(i)*.   
  2. Sequences also support slicing: *a[i:j]* selects all items with index k such that `i <= k < j`.  
    2.1 When used as an expression, a slice is a sequence of the same type. This implies that the index set is renumbered so that it starts at '0'. 
  3.Some sequences also support “extended slicing” with a third “step” parameter: *a[i:j:k]* selects all items of a with index x where `x = i + n*k`, `n >= 0` and `i <= x < j`.  
  4. Sequences are distinguished according to their mutability:  
    4.1 **Immutable sequence**: object that cannot change once it is created. (If the object contains references to other objects, these other objects may be mutable and may be changed; however, the collection of objects directly referenced by an immutable object cannot change.). Examples: strings, tuples, bytes.    
    4.2 **Mutable sequences**: object that can be changed after they are created. The subscription and slicing notations can be used as the target of assignment and del (delete) statements. Examples: lists, byte arrays.  
  

### Mapping
Represents finite sets of objects indexed by arbitrary index sets. Main features:  
  1. The subscript notation *a[k]* selects the item indexed by **k** from the mapping **a**.  
    1.1. This can be used in expressions and as the target of assignments or del statements . 
  2. The function *len()* returns the number of items in a mapping.  
  3. There is currently a single intrinsic mapping type: Dictionaries.  
  > These represent finite sets of objects indexed by nearly arbitrary values.  
  > The only types of values **not acceptable as keys are values containing lists or dictionaries or other mutable types that are compared by value rather than by object identity**, the reason being that the efficient implementation of dictionaries requires a key’s hash value to remain constant. Numeric types used for keys obey the normal rules for numeric comparison: if two numbers compare equal (e.g., 1 and 1.0) then they can be used interchangeably to index the same dictionary entry.  
  > Dictionaries didn't preserve insertion order in versions of Python before 3.6. Above that version, dictionaries preserve insertion order, meaning that keys will be produced in the same order they were added sequentially over the dictionary. Replacing an existing key does not change the order, however removing a key and re-inserting it will add it to the end instead of keeping its old place. Dictionaries are mutable; they can be created by the {...} notation.  

  
### Magic Methods
Are methods that are not directly invoked by the programmer when writing a code. They are system calls that are invoked on the back end automatically. The difference between magic and normal methods is that double underscores surround magic methods. That is why they are also called dunder methods. Dunder here means double underscores. *Magic methods are also used for operator overloading*. Example: The use of \_\__getitem\_\__() in a class allows the instances of a class to use the indexer operator [ ] with the reference variables of a class for accessing the value of a list, dictionary, or tuple from a specific index.  

---

## Unit tests

*PyUnit* is a Python native library for unit tests (doesn't need to be installed and it's under the name of **unittest**) and can be implemented by importing the entire module or just the resources that will be used.  

### Writing tests
>  - To create tests with PyUnit it's necessary to create a Test Class that extends the TestCase class present in the unittest module;  
>  - PyUnit finds test methods by the prefix **test** in their name;  
>  - Finally, it's necessary to call the main function of the unittest module within the `if __name__ == "__main__":` expression of the module to execute the tests created.  
>   
>  Basic structure example: 
>  ```python
>  import unittest
>
> class TestClass(unittest.TestCase):
> 
> def test_meu_metodo(self):
> self.assertEqual(valor_esperado , valor_real, "mensagem caso o teste falhe")
> 
> if __name__ == "__main__":
> unittest.main()
>  ```  

Applying in a real example: considering the need to test the following frete_gratis method of the Compra class in isolation:  

```python
class Compra:
    def frete_gratis(self, valor):
        return valor >= 150
```

Creating the CompraTest class inside the tests folder, as the test_frete_gratis method, according to the code below:  
```python
import unittest
from compra import Compra

class CompraTeste(unittest.TestCase):
    def test_frete_gratis(self):
        nova_compra = Compra()
        self.assertTrue(nova_compra.frete_gratis(200))

if __name__ == "__main__":
unittest.main()
```
The assertTrue method defines that the return of nova_compra.frete_gratis(200) must be True otherwise the test fails. In this case, it will return True because 200 is greather than 150 (what it's being compared inside the method).  

### Throwing exceptions

In certain situations it's necessary to know if a unit will generate an error, or an Exception. For this kind of situation, *PyUnit* has a specific method called **assertRaises()** that determines whether the code being tested should throw an exception and what type of exception it should throw. The assertRaises method has the following syntax:  
```python
assertRaise(tipo_erro, codigo_testado [, parâmetros, caso, existam)]
```  
  
Its use is very simple, it's declared as a common assert, but slightly different:  
  - In its first parameter the type of error is informed  
  - Then the name of the function that will be tested (without the calling parentheses)  
  - Finally the parameters, if any, that must be assigned to the function being tested by assertRaises.  

```python
def test_frete_gratis_exception(self):
    nova_compra = Compra()
    self.assertRaises(TypeError, nova_compra.frete_gratis, "duzentos")
```

If the unit tested with assertRaises does not throw an exception the test will fail. The method receives and compares an integer, not a string.  
  
### Asserting values
  
It's a native Python statement that checks if the following declared expression has a passable value like True in an if. If not, it will raise an AssertionError and display an error message, if defined.  
```python
assert expressao [, "mensagem"]
```

When used in a test method, the assert statement behaves similarly to the assert methods, as shown below:  
```python
import unittest
from compra import Compra

class CompraTeste(unittest.TestCase):
    def test_frete_gratis(self):
        nova_compra = Compra()
        assert nova_compra.frete_gratis(100), "erro em Compra.frete_gratis"

if __name__ == "__main__":
unittest.main()        
```
In this case, the value 100 is lower than 150, so the comparison in the method will return False and the assert in test case will fail.  

### Running Tests

To run the tests just run the file in the terminal with the python command: `python classe_de_teste..py`  

Then the command line terminal will give a response similar to the following if no errors are detected in the tests:
```sh
> python classe_de_teste.py
        ..
        ----------------------------------------------------------------------
        Ran 2 tests in 0.001s

        OK
```
In the example above PyUnit is indicating that two tests were run and no errors were found.  

### Environment
In many situations it is necessary to reuse instances in more than one test within a test class. The test environment consists of the objects that will be used in all tests of the test class.  
*PyUnit* has the following tools for assembling and disassembling test environments:  
> - **setUp**: is the TestCase superclass method that is executed before each test in the same class, ideal for instantiating objects with predefined values. It's like the `@BeforeAll` annotation from JUnit 5.  
> - **tearDown**: is the TestCase superclass method that is executed after each test in the same class, ideal for closing connections to databases, files, etc. It's like the `@AfterAll` annotation from JUnit 5.  
>   
> Although these methods are useful, it's a good practice to only use them when it's necessary, as they can make reading the code more difficult.  
>  

Knowing that large applications tend to run their tests autonomously, in a process that can take hours until the entire system is covered by them. In this context, it is important that each test in the stack can be executed without any connection to the previous one as a guarantee that failure in a given test will not compromise the reliability of the following ones. Otherwise, it may be necessary to trace back problems such as tests that fail depending on the order in which they are executed, which can easily consume programmer hours.

The setUp method is mainly used to create implementations that will be shared by all tests, such as objects with many attributes:  
```python
import unittest

from funcionario import Funcionario
from folha_pagamento import FolhaPagamento

class FolhaPagamentoTest(unittest.TestCase):
    def setUp(self):
        self.funcionario = Funcionario(3000, "Cláudio André Mergen Taffarel", 1, 171.9)
        self.folha = FolhaPagamento()

    def test_calcula_salario_liquido_controle(self):
        self.assertEqual(2222.07, folha.calcula_salario_liquido(self.funcionario))

    def test calcula_salario_liquido_isento_INSS(self):
        self.funcionario.salario = 1693.72
        self.assertEqual(1366.6, folha.calcula_salario_liquido(self.funcionario))

    def test_calcula_salario_liquido_tres_dependentes(self):
        self.funcionario.dependentes = 3
        self.assertEqual(2250.51, folha.calcula_salario_liquido(self.funcionario))
```

The tearDown method is intended to allow the recovery of the original state before after each test has been executed. Consider that there's a log class available in this way, which is obtained from a factory and which, when performing its actions, keeps in memory data such as the name of the file used, a buffer of its content, among other things.  

```python
import unittest

from analizador import Analizador

class AnalizadorTest(unittest.TestCase):
    def setUp(self):
        self.analizador = Logger.analizador

    def test_nome_arquivo_log_valido_letras_maiusculas(self):
        resultado = analizador.nome_arquio_log_valido("log_salvo.LOG")
        self.assertTrue(resultado)

    def test_nome_arquivo_log_valido_letras_minusculas(self):
        resultado = analizador.nome_arquio_log_valido("log_salvo.log")
        self.assertTrue(resultado)

    def tearDown(self):
        self.analizador = null
```

In this way, if any subsequent test uses the same log class, the data stored during the execution of this test will not cast doubt on its result.  

### Mocking objects

To validate a model to be persisted, it's possible to use a mock object to replace the persistence class, which in this case is necessary for the completion of the action, but still indirectly important. That way, the focus is on validation and exempt test code from connection errors, among others.  
A mock is a fake object constructed from a class. This object is created and used instead of a dependency on the scenario to be tested. Thus, the test code become free from errors indirectly related to the main objective in a given test context.  

To create a mock object of a class that needs to be simulated inside the test, it's used the **@patch** annotation, by default the methods of this mock do nothing. A mock is a fake object, which can be created from a class, but is not an instance of that class. When it's needed that a mock's method generated in this way returns something, it's created a new mock for that method and inform what value this mock should return when it is called in the constructor of the Mock class as the return_value value.  


<table>
<tr>
<td> Class </td> <td> First test:  get_quotacao_dolar method will have a return equal to 3 </td>
</tr>
<tr>
<td>

```python
from api.helpers.currency import Currency

class FolhaPagamento:

def pagamento_moeda_estrangeira(self, tipo_moeda, valor, currency: Currency):
    if (tipo_moeda == Currency.QUOTACAO_DOLAR):
        return valor * currency.get_quotacao_dolar()
    elif(tipo_moeda == Currency.QUOTACAO_EURO):
        return valor * currency.get_quotacao_euro()
    elif(tipo_moeda == Currency.QUOTACAO_LIBRA):
        return valor * currency.get_quotacao_libra()
    else:
        raise ValueError("moeda não disponível")
    return 0
```

</td>
<td>

```python
class FolhaPagamentoTeste(unittest.TestCase):

    @patch('helpers.Currency')
    def test_pagamento_dolar(self, fake_currency):
        folha = FolhaPagamento()
        fake_currency.get_quotacao_dolar = Mock(return_value=3)
        resultado = folha.pagamento_moeda_estrangeira("dolar", 3000, fake_currency)
        assert resultado == 9000, "valor incorreto"
```

</td>
</tr>
</table>

  
>  
> Line 3 : The @patch annotation defines that the test argument (except the self of a method) will be a mock object of type Currency within the scope of that test.
> @patch('nome.da.Classe')  
> Line 6 : a mock is created for the fake_currency get_quotacao_dolar method with a return value defined through the return_value parameter of the Mock() class constructor  
> The patch decorator makes it easy to create mock classes or objects in the module under test. The attribute in question (except a method's self ) will be replaced by a mock during the test and restored after the test is finished.  
>  

#### Mock class
Mock is a flexible object designed to replace the use of sketches and test doubles in code. A Mock can be called and create attributes as new mocks when accessed. Accessing the same attributes will always return the same mocks. Mocks record how they are used, allowing assertions to be made about interacting with your code.  

```python
class unittest.mock.Mock(spec=None, side_effect=None, return_value=DEFAULT, wraps=None, name=None, spec_set=None, unsafe=False, kwargs)
```

Arguments  
<details>
  <summary>spec:</summary>
  
  Defines which attributes will be used during the test. Accepts a string list or an object. Any mock attribute that is called must be declared in the spec or an AttributeError will be raised, however it allows assignment/creation of new attributes. If an object is passed in spec , the __class__ magic method will return the class of the spec, this allows mocks to pass isinstance().  
  
</details>

<details>
  <summary>spec_set:</summary>
  
  It's a stricter version of spec. Prevents any reference to an attribute that is not declared in spec_set.  
</details>

<details>
  <summary>side_effect:</summary>
  
  It can be either a function to be executed when the mock is called, an iterable or an exception (class or instance) to be thrown:  
  - If a function is passed, it will be called with the same arguments as the mock and, unless the function has the default return of the mock, the return value of the function will be the one used.  
  - Alternatively, side_effect can be an exception class or instance. In that case an exception will be thrown when the mock is called.  
  - If side_effect is an iterable then each call will result in the next value of the iterable.  

  side_effect can be set to None to empty it.
</details>

<details>
  <summary>return_value:</summary>
  
  Declare the return value when the mock is executed. By default it is a new mock.
</details>

<details>
  <summary>unsafe:</summary>
  
   By default, accessing any attribute with name starting with assert, assret, asert, aseert or assrt will raise an AttributeError. Passing unsafe=True will allow access to these attributes.
</details>


<details>
  <summary>wraps:</summary>
  
  Item for the mock object to wrap. If wraps is not None then calling the Mock will pass the call through to the wrapped object (returning the real result). Attribute access on the mock will return a Mock object that wraps the corresponding attribute of the wrapped object (so attempting to access an attribute that doesn’t exist will raise an AttributeError).  
</details>

<details>
  <summary>name:</summary>
  
  Defines a name for the mock that will be used as your __repr__ . The name propagates in child mocks.  
</details>

#### Mocking magic methods

Mock allows the mockup of Python's magic methods. This allows mock objects to replace objects that implement Python protocols. As magic methods are seen differently from other methods, this functionality was specifically implemented. So not all magic methods are supported, although the list includes most of them.  
It's possible to mock magic methods by defining the desired method for a mock function or object.

<table>
<tr>
<td> Example 1 - Using function (the first argument must be self) </td> <td> Example 2 - Using object </td>
</tr>
<tr>
<td>

```python
def __str__(self, *args, **kwargs):
        return "string de testes"

    def test_stringficador(self):
        gateway = Mock()
        gateway.__str__ = self.__str__
        self.assertEqual(str(gateway), "string de testes")
```

</td>
<td>

```python
def test_stringficador(self):
        gateway = Mock()
        gateway.__str__ = Mock(return_value = "string de testes")
        self.assertEqual(str(gateway), "string de testes")
```

</td>
</tr>
</table>


Magic method calls do not appear in method_calls but appear in mock_calls.  
Note : If the spec keyword was used in the Mock creation as an argument then defining a magic method that is not in the spec will result in an AttributeError error.  

---

