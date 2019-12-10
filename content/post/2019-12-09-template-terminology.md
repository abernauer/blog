---
title: Template Terminology
author: Andrew Bernauer
date: '2019-12-09'
categories:
  - C++
tags:
  - C++
  - templates
  - mlpack
slug: template-terminology
---

# Intro 

In the Spring of 2019 I started working on a [mlpack](https://www.mlpack.org/doc/mlpack-3.2.2/doxygen/bindings.html) automatically generated binding to R or [Rcpp](http://www.rcpp.org/) to be more precise. Both projects utilize a very powerful, yet complicated C++ language feature called templates. C++ is a statically typed language meaning your code is type checked at _compile-time_ versus _run-time_ in the case of R. In theory this language feature should allow the programmer to abstract away from concrete algorithms, to generic algorithms that operate on different data types and structures. However, in practice this can be quite difficult depending on the compiler and which C++ standard you're working with. This initial post aims to be the first of many on templates and help clarify the technical jargon surrounding templates.  

# "Template Class" or "Class Template"?

According to the C++ standard structs, classes and unions are called _class types_ . **Class** includes the previous mentioned _class types_ preceded by the keywords _class_ and _struct_ , but not unions.

A lot of confusion surrounds the terminology of a class that is a template.

+ **class template**  i.e. class that happens to be a template. Or parametized representation of a family of classes.
+ **template class**  has the following uses
  + synonym for class template.
  + refer to classes generated from templates.
  + refer to named classes with a template-id.
  
As a result of the vagueness around the properties of a **template class** you should avoid use of the term.

Correspondingly, use _function template_ and _member function template_ as a good rule of thumb.




# Instantiation and Specialization

_Template insantiation_ is a procedure for creating a class, function, or member function from a template by passing values for its arguments.
The resulting entity is a _specialization_. Alternatively, the programmer can pass different arguments to the declaration e.g.

```c++
template <typename T1, typename T2> // primary class template 
class AClass{
...
};


template<> // explicit specialization
class AClass<std::vector, int> {
...
};

template <typename T> // partial specialization 
class AClass<T,T> { 
...
};

template <typename T> // partial specialization
class AClass<bool,T>{
...
};

```

# Definitions versus Declarations 

According to the C++ standard a _declaration_ is a C++ idea that introduces a name into a scope.
All of the information or the implementation of that name are not necessary  for a valid declaration e.g. :

```c++
class D; // a declaration of D as a class
void h (double g); // a declaration of h() as a function and g as a named parameter
extern int j; // a declaration of j as a variable

```

In contrast goto labels and macro definitions are not considered declarations in C++.  

Declarations become _definitions_ when the underlying implementation of their stucture are present, with variables this means when their storag space is allocated in memory. Classes and functions make this transition when a brace-enclosed body are present. e.g. :

```c++
class D{}; // definition and declaration of class D
void h(double g) { // definition and declaration of function h()
    std::cout << g << std::endl;

}

extern int j = 10; // initializer makes this a definition for j

int j; // global var declarations not preceded by extern qualifies as a definition
```

+ **declaration** of function template

```c++
template <typename T>
void funky (T);
```

+ **definition** of class template

```c++
template <typename T>
class B {};
```


# The One-Definition Rule




# Template Parameters versus Template Arguments


# Summary

+ Prefer the usage of terms like _class template_ , _function template_, and _member function template_ when talking about templates.
+ Templates can be specialized by passing arguments to it's declarations.
+ Declarations introduce a name into a C++ scope.
+ Definitions of classes and functions require a brace-enclosed body. 

# References 

_Vandvoorde, David_ . _Josuttis, Nicolai_. __C++ Templates The Complete Guide__
