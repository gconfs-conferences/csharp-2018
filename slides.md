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
  ACDC cyril = new ACDC();
  ACDC cuebrick = new ACDC("Cuebrick", 280, 20);

  cyril.GetAge(); // returns 2
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
