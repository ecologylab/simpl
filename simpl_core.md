

Simpl: An Overview
=====
S.IM.PL stands for "Support for Information Mapping between Programming Languages." It is an architecture and a set of common standards designed to improve and radically simplifiy the development of applications which may transfer data across many different programming languages. 

Language interoperability should never be painful; currently, polyglot programming poses a set of uniqu challeneges, and often requires the writing of boilerplate code. 

"Universal" formats such as JSOn are great, in and of themselves, but the need to map parsed JSON to our data structures in each languages presents a need to write boring, endlessly repetive boilerplate code that needs to be written *all the time* Additionally, the more code that we end up writing in this space, the more bugs that tend to fester in our data layers.

This is, ultimately, undesirable. Since serialization and deserialization are a common way to save and restore data, levereaging this as core functionality and definiing a set of common conventions for serailziation and deserialization allows us to realize our goal of painless cross-language development. 

Even if your project is not designed for mulitple languages; designing wtih simpl serialization and deserialization at your data layer will facilitate ports to ohte rlanguages in the future. We've used SIMPL in our own lab to interface javascript web applications with Java servers and Objective C IPhone clients. It's been a vibrant foundation for our work, and the general contribitions of inter-language interoperability are well worth pursuing. 


