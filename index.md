
# IT 179 Exam 1 review
## Chapter 1: Object Oriented Programming and Class Hierarchy's 
### 1.1 ADT's interfaces, and the java API
- Interface:

  - is like a contract that tells the applications programmer precisely what methods are available and describes operations they perform. It also tells the applications programmer what arguments, if any, must be passed to each method and what result the method will return.

  - The interface tells the code precisely what methods must be written but it does not provide a detailed algorithm or prescription for how to write them.
  
  - The important pont is that the particular implementation that is used will not affect other classes that interact with it because every implementation satisfies the contract.
  
  - An interface cannot contain constructors because it cannot be instantitated, one cannot create objects, or instances of it. However, it can be represented by instances of classes that implement it.

###Example 1.1
'''
/** _The interface for an ATM. */ 
**public interface ATM**{
      /**verify a user PIN
      @Param pin the users pin
      @return whether or not the users pin is verified*/
      boolean verifyPIN(string pin):
'''

**Because only the headings are shown, they are considered abstract methods**

**Note the implemets clause**
''' public class ATMbankAmerica implements ATM
    public class ATMforAllBanks implemnets ATM
'''

##1.2 Introduction to Object Oriented Programming (OOP)
- A major reason for the popularity of OOP is that it enables programmers to reuse previosuly written code saved as classes, reducing the time required to code new applicatins.

- If an application needs a new class that is similar to an existing class but not exactly the same, the programmer can create it by extending or inheriting from, the existing class. The new class (called the subclass) can have additional data fields and methods for increased functionality. Its objects also inherit the data fields and methods of the original class (called the superclass)
- Inheritance and hierarchical organiation allow you to capture the idea that one thing may be a refinement or an extension of anohter.

### Initializing data fields in a subclass
- a superclass constructor must be invoked as the first statement in the constructor body using a statement such as 'super(man, proc, ram, disk, procSpeed);'
**Example**

'''  Public Notebook(String man, String proc, double ram, int disk, double procSpeed, double screen, double wei){
                     **super(man, proc, disk, procSpeed);**
                     screenSize = screen;
                     weight = wei;
'''

### The No-Parameter Constructor
- If the execution of any constructor in a subclass does not invoke a superclass constructor, Java automatically invokes the no-parameter constructor for the superclass. Java does this to initialie that part of the object inherited from the superclass before the subclass starts to initialize its part of the object.
- **PITFALL**
  - IF the no-parameter constructor is defined in a subclass but it is not defined in the superclass, you will get a syntax error _constructor not defined._ You can also get this error if a subclass constructor does not explicitly  call a superclass constructor. There will be an implicit call to the no-parameter superclass constructor, so it must be defined.

###Protected Visibility for Superclass data Fields
- _Protected visibility:_
  - a data field (or method) with protected visibility can be accessed in the class defining it, in any subclass of that class, or in any class in the same package.
''' protected String manufacturer;
    manufacturer = man; 
'''

### Polymorphism 
- Polymorphism enables the JVM to determine at run time which of th classes in a hierarchy is referenced by a superclass variable or parameter. 
- In Java, a variable of a superclass type (general) can refernece an object of a subclass type (specific)

**Example**
''' Computer theComputer;
    theComputer = new Notebook("Bravo", "Intel", 4, 240, 2.4, 15.0, 7.5);
    System.out.println(TheComputer.tos]String());
'''
**The JVM would print theComputer even though it was first referenced as a computer object. This is because notebook is a type of computer.** 


## Chapter 2: Lists and the Collections Framework
- A list is an expandable collection of elemnets in which each element has a position or index. Some lists enable their elements to be accessed in arbitrary order (called _random access_ ) using a position value to select an element. Alternatively, you can start at the beginning and process the elements in sequence. 

###The List interface and ArrayList class
- An _array_ is an indexed data strcuture, which means you can select its elements in arbitrary order as determined by the subscript value.
- **You can't do the following with an array object:**
	- Increase or decrease its length (its fixed)
	- Add an eleent at a specified position without shifting the other elements to make room. 
	- Remove an element at a specifed position without shifting the other elements to fill in the resulting gap.

- The classes that implement JAVA list interface all provide methods to do these operations and more:
	- (method get) Return a reference to an element at a specified location.
	- (method get) Find a specified target value.
	- (method add) Add an element at the end of the list.
	- (method add) insert an element anywhere in the list.
	- (method remove) remove an element.
	- (method set) replace an element in the list with another
	- (method size) return the size of the list
	- sequentially access all the list elements without having to manipulate a subscript

-deprecated classes have been replaced by better classes and should not be used in new applications. 

- Even though an ArrayList class is an indexed collextion, you can't access its elements using a subscript. Instead, you use the get method to access its elements. **For example:** the statement 'String dwarf = myList.get(2)' stores a references to the string object "Jumpy" in varaible dwarf.
- **Subscripts cannot be used with ArrayList or indexed collections!**

### Generic collections
- _Generic collections (or generics):_
	- allow you to define a collection that contains references to objects of a specific type.

### Syntax Creating a Generic Collection
		**Form**
'''
		Collection ClasName<E> variable =  new CollectionClassName<>();
		Collection ClasName<E> variable =  new CollectionClassName<E>();
'''
	**Example**
''' 
		List<Person> people = new ArrayList<>();
		List<Stringn> myList = new ArrayList<String>();
		ArrayList<Integer> numList = new ArrayList<>();
'''
	**Meaning**
	An initiall empty _CollectionClassName<E>_ object is created that can be used to store references to objects of type E (the type parameter). The actual 		object type stored in an object type CollectionClassName<E> is specified when the object is created. If the CollectionClassName on the list is an
	interface, the CollectionClassName on the right must be a class that implements it. Otherwise, it must be the same class or a sublcass of the one on the
	left. 
	
	The exmaples above show different ways to create an ArrayList. In this text, we normally specify the interface name on the left of the = operator and the 	implemneting class on the right as show in the first two examples. Since the type parameter E must be the same on both sides of the assignment operator, 		Java 7 introduced the diamond operator <> whih eleiminates the need to specifiy the type parameter twice. 
	
	Each element of yourlist is a type object reference. The data types of the actual objects referenced by elements of yourList are not specified, and in facts, different elements can reference objects of differnet types. 
	A nongeneric collection in Java is very general in that it can store objects of different data types. A generic collection however, can store objects of one specified data type only. 
	Generics enable the compiler to do more strict type checking to detect erorrs at compile time instead of at run time.

### 2.5 single linked lists
**An example to understanding linked lists**
	
	One example would be maintaining a list of students who are waiting to register for a course. Instead of having the students waiting in actual line, you can give each student a number, which is the students position in te line. if someone drops out of the line, everyone with a higher number of the student that dropped gets a new number that is reduced by 1. If someone cuts into the line because they "need the course to graduate," everyone after this person gets a new number, which is one higher than before. The person maintaining the list is responsible for giving everyone their new number after a change.  

