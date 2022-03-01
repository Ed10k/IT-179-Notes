
# IT 179 Exam 1 review
## Chapter 1
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


                     


