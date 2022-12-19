## Lambdas and Functional Interfaces

- Lambda is an anonymous function that is not associated to any class or identifier. It depends on functional interfaces to exists.  
- Properties of Lambdas are:  
    - Execution function name (method defined at functional interface)
    - Paramters list
    - Function body (**what have to be done** by the function, the definition of its behavior)
    - Return type
    
- Functional Interface (F.I.) is any interface that declares only one abstract method. The @FunctionalInterface annotation helps to identify the F.I. and makes some errors show up when more abstract methods are added to the interface, in other words, this annotation is not required to define a F.I., but helps to manage it.
- It's a prerequisite to the F.I. to have only one method in order to the Lambdas to be executed without any ambiguity. 

### Use cases of Functional Interfaces and Lambdas

<details>  
  <summary>- Method with no parameters and no return type</summary>  

> F.I.:  
>    ```java
>    public interface Nome {
>      public void imprimeNome()
>    }
>    ```
>Main method
>    ```java
>    public static void main(String[] args)
>      Nome nome = () -> System.out.println("Renata");
>      nome.imprimeNome();
>      //Renata
>    }
>    ```
>

</details>

<details>  
  <summary>- Method with parameters and no return type</summary>  

> F.I.:  
>    ```java
>    public interface OperacaoMatematica {
>      public void executaOperacao(int a, int b)
>    }
>    ```
>Main method
>    ```java
>    public static void main(String[] args)
>      OperacaoMatematica soma = (a, b) -> System.out.println(a+b);
>      soma.executaOperacao(10,20);
>      //30
>      OperacaoMatematica multiplicacao = (a, b) -> System.out.println(a * b);
>      soma.executaOperacao(4,3);
>      //12
>    }
>    ```
>
</details>  

<details>   
  <summary>- Method with parameters and with return type</summary>  

> F.I.:  
>    ```java
>    public interface TamanhoString {
>      public int retornaTamanho(String s)
>    }
>    ```
>Main method
>    ```java
>    public static void main(String[] args)
>      TamanhoString tamanho = s -> s.length();
>      System.out.println(tamanho.retornaTamanho("Teste"));
>      //5
>    }
>    ```
>
</details>

<details>  
  <summary>- Multiline functions</summary>  

> F.I.:  
>    ```java
>    public interface TamanhoString {
>      public int retornaTamanho(String s)
>    }
>    ```
>Main method
>    ```java
>    public static void main(String[] args)
>      TamanhoString tamanho = s -> {
>         int l = s.length();
>         System.out.println("String size is: "+l);
>         return l;
>      };
>      System.out.println(tamanho.retornaTamanho("AnotherTest"));
>      //String size is 11
>    }
>    ```
>
</details>  

## Predefined Functional Interfaces

| Name | Description | Functional Interface | Function Descriptor |
| --- | --- | --- | ---  |
| 1. Predicate  | Receives one object of any type, tests a condition and returns a boolean.  | Predicate<T>  | T -> boolean  |
| 2. Consumer  |  Receives one object of any type and returns nothing (only consumes). | Consumer<T> | T -> void |
| 3. Function | Receives one object of any type, applies a function/operation over it and returns the result (the type of returned object not necessarily needs to be the same of the received one). | Function<T, R> | T -> R  |
| 4. Supplier | Receives nothig and returns one object of any type (only supplies). | Supplier<T> | () -> T |
| 5. UnaryOperator | It's an extension of *Function*, but the difference is that it receives one object of any type, applies a function/operation over it and has to return one object with same type of the received one. | UnaryOperator<T> | T -> T |
| 6. BinaryOperator | It's also an extension of *Function*, but the difference is that it receives two objects of any type, applies a function/operation over them and has to return one object with same type of the received two. | BinaryOperator<T> | (T,T) -> T |
| 7. BiPredicate | It's an extension of *Predicate*, but the difference is that it receives two objects of any type, tests a condition and returns a boolean. | BiPredicate<L,R> | (L,R) -> boolean |
| 8. BiConsumer | It's an extension of *Consumer*, but the difference is that it receives two objects of any type and returns nothing. | BiConsumer<T,U> | (T,U) -> void  |
| 9. BiFunction | It's an extension of *Function*, but the difference is that it receives two objects of any type, applies a function/operation over them and returns the result (type of returned object not necessarily needs to be equal of any of the received two). | BiFunction<T,U,R> | (T,U) -> R |

  
