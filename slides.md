\titlepage

## Overview
\tableofcontents

# Introduction

# Object Oriented Programming

## What is OOP?

* A concept
* Patterns
* Create 'objects' from the patterns
* Object interaction

## A class

```cs
class ACDC
{
  //fields
  float _height;
  float _weight;
  bool _isMean;
  [...]
}
```

## A class with methods

```cs
class Student
{
  // fields
  string _name;
  float _height;
  float _weight;
  bool _isMean;
  Color _hairColor;

  // methods
  string GetName();
  void GoToClass();
  bool IsInClass();
  void Work();
}
```

## Example of using methods

```cs
public static void Main(string[] args)
{
  Student student = new Student();

  if (! student.IsInClass())
    student.GoToClass();
  else
    student.Work();
}
```

## Instantiating an object

* Instantiating is 'creating'
* the keyword: **new**
* the class constructor: a special method

## Constructor

* what is it?
* instanciate an object
* you can have several constructor per class
* there is a default one if none is given
* initialize the fields

## Example

```cs
class ACDC
{
  // fields
  string _name;
  int _height;
  int _age;
  [...]

  // method
  void AnswerQuestion();
  void Facepalm();
  [...]
}
```

## Example
```cs
class ACDC
{
  public ACDC()
  {
    this._name = "Cyril";
    this._height = 180;
    this._age = 2;
  }

  public ACDC(string name, int height, int age)
  {
    this._name = name;
    this._height = height;
    this._age = age;
  }
}
```

## Example

```cs
public static void Main(string[] args)
{
  ACDC inaxys = new ACDC();
  ACDC cuebrick = new ACDC("Cuebrick", 280, 20);

  inaxys.GetAge(); // returns 2
  cuebrick.GetAge(); // return 20
}
```

## Static fields

* Common to every instance of a class
* Cannot be accessed from instance
* Cannot be accessed with **this**.

##  Static Class

* Cannot be instantiated
* Every field is static

## Example

```cs
class ACDC
{
  public static int count;
  public ACDC()
  {
    ++count;
  }

  [...]
}
```

## Example

```cs
public static void Main(string[] args)
{
  ACDC garage = new ACDC();
  ACDC kirzie = new ACDC();

  ACDC.count; // count = 2;
}
```
# Advanced C#

## Keywords

* `var`
* `typeof`
* and a lot more (`yield`, `explicit`, `try`, `unsafe`, `using`)

## var

```cs
ACDC acdc = new ACDC();
// is the same thing as
var acdc = new ACDC();
```

## var and null

```cs
var tetra = new ACDC();
tetra = null;

ACDC tetra = new ACDC();
tetra = null;

var tetra = null; // compilation failed
```

## typeof

* Get the `System.Type` of a type
* Usually used with the `GetType` method

## Example

```cs
Human people = new Human[42];
[...]

foreach(Human person in people)
{
  Type type = person.GetType();
  if (type.Equals(typeof(ACDC))
    person.AnswerQuestion()
  else
    person.Sleep();
}
```

## Namespace

* Scopes where a set of related classes is implemented.
* Namespaces may nest, sub-namespaces are accessed using ..
* Namespaces use visibility. One can declared a class as private (only accessible in the current namespace) or public (accessible from anywhere).

## Example

```cs
Schools.Ionis.Epita.Students.best.ING1.best.ACDC inaxys = new Schools.Ionis.Epita.Students.best.ING1.best.ACDC();

inaxys.Sings("Best acdc rpz!");
```

## Exampe with namespace

```cs
using Schools.Ionis.Epita.Students.best.ING1.best.ACDC;

ACDC inaxys = new ACDC();
inaxys.Screams("This is SPARTAAAAAAAAAAAAAAAA");
```

## Operator overloading

* you can define opertors between classes (or types in general)
* In other words, you can use `+`, `-`, `*`, `/`, etc.

## Example

```cs
class Human
{
  Color skin;
  Color eyes;

  // Constructor
  [...]

  public static Human operator +(Human a, Human b)
  {
    return new Human(mix(a.skin, b.skin), mix(a.eyes, b,eyes));
  }
}
```

## Example

```cs
Human daddy = new Human(white, green);
Human mommy = new Human(black, brown);

Human baby = daddy + mommy; // metis and brown eyes, ofc
```

## Exceptions

* Manage errors
* Allows to create custom errors (new classes in fact)
* `Execption` is a class

## Throw

* Allows to send an exception

```cs
//blabla

throw new Exception("Flag Trish");

//blabla
```

## Try-Catch

```cs
public statuc void Main()
{
  try
  {
    int t = Convert.toInt32("42");
    // int t = Convert.toInt32("Phorty-twoh");
  } catch (Exception e) {
    Console.Error.WriteLine("You shall not pass!!:" + e.message);
  }
}

// 42 will work fine
// second will 'catch the exception'
```

## Generics

* Define type-safe data structures
* avoid code duplication

## Example

```cs
public class Stack<T>
{
  private T val;
  private Stack<T> next;

  /* equivalent to Push */
  public Stack<T>(T val, Stack<T> stack)
  {
    this.val = val;
    this.next = stack;
  }

  // ...
```

## Example

```cs
// ...

  public T Peek()
  {
    return val;
  }

  public Stack<T> Pop()
  {
    return next;
  }
}
```

## Example

```cs
Stack<int> stack = null;

for (int i = 0; i < 7; ++i)
  stack = new Stack<int>(i, stack);
// stack = 6 -> 5 -> 4 -> 3 -> 2 -> 1 -> 0 -> null

int four = stack.Pop().Pop().Peek();

Stack<int> tail = stack.Pop();
```

## Example

```cs
Stack<ACDC> stack = null;

foreach(var acdc in acdcs)
  stack = new Stack<ACDC>(acdc, stack);
// stack = inaxys -> chokapeek -> treta
//-> CueBrick -> Garage -> Kirzkjdnsie -> null

double four = stack.Pop().Pop().Peek();

Stack<ACDC> tail = stack.Pop();
```

## SURPRISE OCAML

* you thought it would go away?
* Ha, NEVER!

## Functionnal programming

* Function type (create functions)
* Function values (assign functions)
* Function arithmetic (add or substract functions)

## Func, Predicate, Action

```cs
Func<double, double> f = Math.Exp;
double e = f(1);

/* Func<string, void> act ... */
Action<string> act = Console.WriteLine;

/* Func<string, string, bool> p ... */
Predicate<string, string> p = String.Equals;
string str = "So cool";

if (p(str, "it is cool"))
  act("Stylai");
```

## Delegates, lambas and anonymous

```cs
Func<int, int> MultAnswer
= delegate(int x) { return 42 * n; };

// is equivalent to

Func<int, int> MultAnswer = n => 42 * n;

int answer = MultAnswer(1);
// answer = 42
```

## 1 + 1 = a birdplane

```cs
Action<string> hello =
  str => Console.WriteLine("Hello {0}!", str);

Action<string> bye =
  str => Console.WriteLine("Bye {0}…", str);

Action<string> greetings = hello + bye;

greetings("All");
// Hello All!
// Bye All

(greetings - hello)("All");
// Bye All
```

## Questions