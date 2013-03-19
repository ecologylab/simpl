To Simpl Serialize a class: 
=====

1. Fields in the class must be annotated with the appropriate annotations from the DBAL
2. Each class must have a public, parameterless constructor
3. Any class referenced behind an interface must instantiate a default instance in the public, parameterless constructor. 
4. Any collection must instantiate a default instance in the public, parameterless constructor. 

For example: suppose I want to simpl serialize the following class: 
~~~java
public ListAndMapClass{
    public Map<String, Integer> myMap;
    public Collection<String> myCollection;
}
~~~

The type information present in these declarations is insufficient for deserialization. Rather than specializing the interface of this class, I should hide the type information inside the public, parameterless constructor. Such an example would work here: 

~~~java
public ListAndMapClass{
    @simpl_map
    public Map<String, Integer> myMap;
    @simpl_collection 
    public Collection<String> myCollection;

    public ListAndMapClass()
    {
        myMap = new HashMap<String, Integer>();
        myCollection = new LinkedList<String>();
    }
}
~~~
