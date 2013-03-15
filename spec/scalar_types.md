Scalar Types
====

At the core of the S.IM.PL Type system are a set of "Scalar Types". These scalar types are the foundation of the type system, and represent a mixture of common primitives shared accross many languages, and a few additional types which improve the quality of life of developers. Additionally, it is possible for developers to add additional sclar types to the S.IM.PL system; this allows for a degree of extensibility, just at the cost of cross-platform compatibility. 

In general, you can think of these scalar types as belonging to three categories: 
1. Core Types - These are the core scalar types which *must* be implemented in any and all implementations of S.IM.PL for core S.IM.PL functionality to be vialbe. 
2. Extended Types - These are types that are not a part of the bare-bones set o functionality needed to implement S.IM.PL, but are expected to be implemented across all S.IM.PL implementations.
3. Custom Types - These are scalar types that are written by developers for the sake of extensibility; Custom types are not guarenteed to be found in all simpl implementations; If certain custom types are very popular, we could always consider making them Extended or Core types. 

This document outlines the core and extended scalar types. All of the scalar type implementations provide a mapping from the native representation of the type in a language to a string representation, and a mapping from a string represnetation of the type to a native represnetation. We thus outline what string outputs we expect for different types, and expect implementors to conform to this. Uniformity at this point enables implementations of S.IM.PL to seamlessly communicate type information without additional boilerplate code. 

An implementor should choose the most natural idiomatic mapping from a given scalar type to the language type. In cases where this mapping is not possible, custom data types shoulo be considered for the mapping. 

Type Listings 
=====
Core Types
====



Extended Types
====


Type Specifications
=====
Core Types
====

Extended Types 
==== 
