### Java stuff

class Adhvay {
    Public static void main (string []args)
    {
        int a = 2;
        int b = 3;
        float c = 2.5;
        string d = "adhvay";
    }

class Student {
    string name;
    int age;
    int roll no;
}

## this is a class, a data type that can hold multiple data types, we can make our own classes. A class is like a blueprint

class Adhvay {

Public static void main()
    Student a = new Student();
# here type is student, and it is pointing to the address of the object, student


## There are two types of memory, static memory and head memory
- data stored in static memory can be accessed fast, but in heap memory it takes time
- when u make an object of a class(copy of a class), it is made in heap memory

```
public class Main
{
    static class Student{
        String name;
        int age;
        int rollno;
        int marks;
    }
    
	public static void main(String[] args) {
	    Student s1 = new Student();
	    s1.name = "Adhvay";
	    s1.age = 69;
	    s1.rollno = 690;
	    s1.marks = 100;
	    
	    Student s2 = new Student();
	    s2.name = "Ligma";
	    s2.age = 420;
	    s2.rollno = 69420;
	    s2.marks = 69;
	    
	    System.out.println(s1.name);
	    System.out.println(s1.age);
	    System.out.println(s1.rollno);
	    System.out.println(s1.marks);
	    
	    System.out.println(s2.name);
	    System.out.println(s2.age);
	    System.out.println(s2.rollno);
	    System.out.println(s2.marks);
	    
	}
}
```
public class Main
{
    static class Student{
        String name;
        int age;
        int rollno;
        int marks;
    }
    
	public static void main(String[] args) {
	    Student s1 = new Student();
	    s1.name = "Adhvay";
	    s1.age = 69;
	    s1.rollno = 690;
	    s1.marks = 100;
	    
	    Student s2 = new Student();
	    s2.name = "Ligma";
	    s2.age = 420;
	    s2.rollno = 69420;
	    s2.marks = 69;
	    
	    System.out.println(s1.name);
	    System.out.println(s1.age);
	    System.out.println(s1.rollno);
	    System.out.println(s1.marks);
	    
	    System.out.println(s2.name);
	    System.out.println(s2.age);
	    System.out.println(s2.rollno);
	    System.out.println(s2.marks);
	    
	}
}
