

Simpl: An Overview
=====
S.IM.PL stands for "Support for Information Mapping between Programming Languages." It is an architecture and a set of common standards designed to improve and radically simplifiy the development of applications which may transfer data across many different programming languages. 

Language interoperability should never be painful; currently, polyglot programming poses a set of uniqu challeneges, and often requires the writing of boilerplate code. 

"Universal" formats such as JSOn are great, in and of themselves, but the need to map parsed JSON to our data structures in each languages presents a need to write boring, endlessly repetive boilerplate code that needs to be written *all the time* Additionally, the more code that we end up writing in this space, the more bugs that tend to fester in our data layers.

This is, ultimately, undesirable. Since serialization and deserialization are a common way to save and restore data, levereaging this as core functionality and definiing a set of common conventions for serailziation and deserialization allows us to realize our goal of painless cross-language development. 

Even if your project is not designed for mulitple languages; designing wtih simpl serialization and deserialization at your data layer will facilitate ports to ohte rlanguages in the future. We've used SIMPL in our own lab to interface javascript web applications with Java servers and Objective C IPhone clients. It's been a vibrant foundation for our work, and the general contribitions of inter-language interoperability are well worth pursuing. 

Simpl: The Core Architecture
====

Simpl has four major functions, which present the core of the architecutre of the system. 
1. Description
2. De/Serialization 
3. Translation
4. Invocation

Description refers to the way that different types are "described" and understood within the context of the S.IM.PL type system. Description includes making a mapping between certain scalar types in a given language to their correlates within the S.IM.PL type system. (For example, an int in C# will get mapped to a IntegerType... both int and Integer in Java will also get mapped to the IntegerType.) Descriptions function at the core of S.IM.PL; all of the core functionalities of the system are derived from haivng some sort of undersatnding of the types that we use. Descriptions naturally drive serialization and deserializatoin, they provide the basis for translation of representations between lnguages, and they provide the information nescessary to perform method invocatoins.

In general, we focus on a few different types of descrpitions to cover all of the different types that S.IM.PL supports. S.IM.PL descrpitions include:
* ClassDescriptors - Descriptions of Classes, their methods, and their fields
* FieldDesrciptors - Description of a field, with type information
* EnumerationDescriptors - Description of an Enumerated type, which holds possible values and their meaning as integers, if specified
* ParameterDescriptors - Description of a parameter; either in a method formal or the parameter of a given MetaInformationDescriptor 
* MethodDescriptors - Description of a method of a given class; used for S.IM.PL invocation
* MetaInformationDescriptors - Description of an annotation / additional information added to a given class.


