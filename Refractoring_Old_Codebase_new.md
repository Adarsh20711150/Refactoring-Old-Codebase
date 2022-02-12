
# Refactoring an Old Codebase

Old codebase means source code that is no longer supported or needs improvement of any kind. In most cases, old code is converted to a modern software language, platform, and refactored.
Dealing with older code and code we didn't write can be a chore.


It is hard to work with old codebases 
The greatest challenge when working with older or unfamiliar code is our 
assumptions about the code.

We may think the code is bad. Whoever wrote it didn’t know what they were 
doing. We could have done a better job. But the truth is, there's usually is a reason why the code is how it is. And, if we didn’t write it, we might not know that reason.

That is why care needs to be taken while making improvements and changes to the codebase. we can’t just put a quick fix on any area. There might be some dependencies 
we are unaware of.

## what is refactoring?
Refactoring is a code improvement process, the goal of refactoring is to improve the quality and encourage the modification of the software product. Refactoring makes the code 
simpler: We have fewer code lines than we began with. Fewer lines of code mean fewer potential bugs.

## How to refractor?
- ### Test the Code
One way to understand the code is to create tests. we can also use a code 
quality tool over the code to identify potential problems.

This will help us understand what the code actually does. And it will reveal all 
potentially problematic areas. As soon as we understand the code we can make 
changes.

- ### Review Documentation
Reviewing documentation of the original requirements will help us understand how 
and where the code came from.

- ### Only Rewrite Code When It’s Necessary
It takes too much time and too many programmers to rewrite everything. 
And even if we do it, rewriting code can introduce new bugs. Or it can 
remove hidden functionality.

Refactor code that has some unit tests — so we know what we have.
Start with the deepest point of our code — it will be easiest to refactor.

Test after refactoring — to make sure we didn’t break anything.

Have a safety net — e.g., (CI) Continuous Integration — so we can revert to a previous build.

# OOPS - Object Oriented Programming

OOPs refers to a programming paradigm that uses objects. Object-oriented programming aims to implement real-world entities like inheritance, hiding, polymorphism, etc in programming. The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function.
## Pillars of OOPS
- ### Abstraction
Abstraction is the property by virtue of which only the essential details are displayed to the user. The non-essentials are not displayed to the user. Ex: A car is viewed as a car rather than its individual components.
- ### Encapsulation
It is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates. Another way to think about encapsulation is, it is a protective shield that prevents the data from being accessed by the code outside this shield. 

- ### Inheritance
It is the mechanism in java by which one class is allowed to inherit the features(fields and methods) of another class. 
- ### Polymorphism
It refers to the ability of OOPs programming languages to differentiate between entities with the same name efficiently. 

## OOPS in refactoring

### Old Codebase

class Animal
{
    // attributes
    int a;
    int b;

    //getters and setters
    public void setA(int a)
    {
        this.a=a;
    }
    public void setB(int b)
    {
        this.b=b;
    }
    public int getA()
    {
        return this.a;
    }
    public int getB()
    {
        return this.b;
    }
    //some method
    public void structure()
    {
        System.out.println("Multicellular being");
    }
}

class Dog extends Animal 
{
    // attributes
    int d;
    int e;

    //getters and setters
    public void setD(int d)
    {
        this.d=d;
    }
    public void setE(int e)
    {
        this.e=e;
    }
    public int getD()
    {
        return this.d;
    }
    public int getE()
    {
        return this.e;
    }

    //some method
    public void structure()
    {
        System.out.println("Multicellular being");
    }
}

class Cat extends Animal
{
    // attributes
    int f;
    int g;

    //getters and setters
    public void setF(int f)
    {
        this.f=f;
    }
    public void setG(int g)
    {
        this.g=g;
    }
    public int  getF()
    {
        return this.f;
    }
    public int  getG()
    {
        return this.g;
    }

    //some method
    public void structure()
    {
        System.out.println("Multicellular being");
    }
}

public class Zoo
{
    public static void main(String [] args)
    {
        Animal animal = new Animal();
        Dog dog = new Dog();
        Cat cat = new Cat();

        //setting values of an animal
        animal.setA(4);
        animal.setB(5);

        //setting values of a dog
        dog.setD(7);
        dog.setE(6);

        //setting values of cat 
        cat.setF(8);
        cat.setG(9);
        
        //printing all the attributes of an animal
        System.out.println("Animal's a: "+animal.getA()+" "+"Animal's b: "+animal.getB());
        
        //printing all the attributes of a dog
        System.out.println("Dog's d: "+dog.getD()+" "+"Dog's e: "+dog.getE());

        //printing all the attributes of a cat
        System.out.println("Cat's f: "+cat.getF()+" "+"Cat's g: "+cat.getG());

        System.out.print("Structure of an animal: ");
        animal.structure();

        System.out.print("Structure of a dog: ");
        dog.structure();

        System.out.print("Structure of a cat: ");
        cat.structure();
    }
}

### Output
Animal's A:4 Animal's B:5 

Animal's A:4 Animal's B:5 Dog's d:6 Dog's e:7

Animal's A:4 Animal's B:5 Cat's f:8 Cat's g:9

Structure of an animal: Multicellular being

### Refactoring
- ### Abstraction
make the instance variables private so that user is limited only to user specific things.
- ### Constructor
Although using getters and setters increases the abstraction, but using constructor instead will enhance the readability and make the code concise.
- ### Static key word
If some code is same for all the classes then needs to be defined in only parent class.
- ### Inheritance
Use of super keyword to make the access of the base class attributes, methods and constructor easier.
- ### Polymorphism
Override toString() method of object class in  each class istead of the getter method to have a good readability.
- ### Encapsulation
All the data is already encapsulated into different classes so we are good to go with it.




## Code After Refactoring 

class Animal
{
    // abstracting the instance variables by making them private
    private int a;
    private int b;

    //constructor instead of setters
    Animal(int a, int b)
    {
        this.a=a;
        this.b=b;
    }

    //toString() method instead of getter methods
    public String toString()
    {
        return new String("Animal's A: "+this.a+" "+"Animal's B: "+this.b+" ");
    }

    //common method to all classes are made static so that can be reached by any class
    public static void structure()
    {
        System.out.println("Multicellular");
    }
}

class Dog extends Animal 
{
    // abstracting the instance variables by making them private
    private int d;
    private int e;

    //constructor instead of setters
    Dog(int a, int b, int d, int e)
    {
        super(a,b);
        this.d=d;
        this.e=e;
    }

    //toString() method instead of getter methods
    public String toString()
    {
        return new String(super.toString()+"Dog's d: "+this.d+" "+"Dog's e: "+this.e);
    }
    
}

class Cat extends Animal
{
    // abstracting the instance variables by making them private
    private int f;
    private int g;

    //constructor instead of setters
    Cat(int a, int b, int f, int g)
    {
        super(a,b);
        this.f=f;
        this.g=g;
    }

    //toString() method instead of getter methods
    public String toString()
    {
        return new String(super.toString()+"Cat's f: "+this.f+" "+"Cat's g: "+this.g);
    }

}


public class ZooRefractored
{
    public static void main(String [] args)
    {
        //Creating the object and initializing the values at the same time made easy using //CONSTRUCTOR
        Animal animal = new Animal(4,5);
        Dog dog = new Dog(4,5,6,7);
        Cat cat = new Cat(4,5,8,9);
        
        //printing all the attributes of an animal
        System.out.println(animal.toString());
        
        //printing all the attributes of a dog
        System.out.println(dog.toString());

        //printing all the attributes of a cat
        System.out.println(cat.toString());

        ////////////Using Common Methods//////////
        System.out.print("Structure of all animal is: ");
        Animal.structure();
    }
}
### Output
Animal's A: 4 Animal's B: 5 

Animal's A: 4 Animal's B: 5 Dog's d: 6 Dog's e: 7

Animal's A: 4 Animal's B: 5 Cat's f: 8 Cat's g: 9

Structure of all animal is: Multicellular

### Reference
- https://www.geeksforgeeks.org/object-oriented-programming-oops-concept-in-java/
- https://blogs.oracle.com/javamagazine/post/refactoring-java-part-2-stabilizing-your-legacy-code-and-technical-debt
- https://www.perforce.com/blog/qac/8-tips-working-legacy-code
    
