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

In the Spring of 2019 I started working on a [mlpack](https://www.mlpack.org/doc/mlpack-3.2.2/doxygen/bindings.html) automatically generated binding to R or [Rcpp](http://www.rcpp.org/) to be more precise. Both projects utilize a very powerful, yet complicated C++ language feature called templates. C++ is a statically typed language meaning your code is type checked at _compile-time_ versus _run-time_ in the case of R. In theory this language feature should allow the programmer to abstract away from concrete algorithms, to generic algorithms that operate on different data types and structures. However; in practice this can be quite difficult depending on the compiler and which C++ standard you're working with. This initial post aims to be the first of many on templates and help clarify the technical jargon.  

# "Template Class" or "Class Template"?

According to the C++ standard structs, classes and unions are called _class types_ . Additionally class is a subset of _class type_


# Instantiation and Specialization


```c++
template <typename T1, typename T2> // primary class template 
class AClass{
...
};


template<> // explicit specialization
class AClass<std::vector, int> {
...
};
```