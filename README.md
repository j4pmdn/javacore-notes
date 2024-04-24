# java-core-notes
## When you make things faster it will make you slower
## Understand the concept, rather than memorizing the code
## Java
Là một ngôn ngữ lập trình biên dịch cấp cao được biết đến với các tính năng bảo mật mạnh mẽ, nhiều thư viện được xây dựng sẵn và nền tảng độc lập được phát triển bởi James Gosling và nhóm của ông tại Sun microsystem có tên đầu tiên là Oak và sau đó được đặt tên là Java dựa trên một loại cà phê trong Indonesia.  That very famous for "Write Once, Run Anywhere" qoute that has JVM.
## Java Virtual Machine
Đó là trình biên dịch Java Byte-code, là dạng mã đã biên dịch từ mã nguồn Java. Nó cũng chịu trách nhiệm xử lý việc thu gom rác để cấp phát và giải phóng bộ nhớ động.
## OOP (Object Oriented Programming)
Đó là tổ chức cấu trúc của mã mô phỏng các đối tượng thực tế thông qua các đối tượng phần mềm có hành vi và thuộc tính riêng của chúng. And has 4 Pillars of Inheritance, Polymorphism, Encapsulation, and Abstraction.
## Why java is not fully Object-oriented
Bacause of primitive types byte, short, int, long, float, and double.
## Java naming conventions
* **Classes should be noun, always capital letter for each word, and should match to the file name.**
```
Foo✅ file name should be Foo.java
FooBar✅ file name should be FooBar.java
```
* **Method should be verb and use camel casing.**
```
Foo foo = new Foo();
foo.greet()✅
foo.greetBar()✅
```
* **Variable should be noun and use camel casing.**
```
String foo;✅
int fooBar;✅
```
* **Constant Variable should be in snake case, always have value when declared, and all caps.**
```
float PI = 3.14;✅
int DEFAULT_VALUE = 1;✅
```
* **Note: Bằng cách viết mã dựa trên quy ước đặt tên, nó sẽ làm cho mã của bạn dễ đọc, có thể tuân theo mã chất lượng doanh nghiệp và khi đọc mã, bạn có thể xác định ngay lập tức phân biệt hàm, biến và lớp là gì.**

## Access modifiers
* **public**: can be used anywhere in the program
* **protected:** can only be used by child class and not avaiable globally.
* **private:** only available inside the specific class it was declared on
* **package-private:** the default access modifier that only available in the specific package it was declared on.
**Note:** In inheritance access modifier cannot be more restricted than the declared one. for example

| Modifier | Class | Package | Subclass | World
| ----------- | ----------- |----------- | ----------- | ----------- |
| public | Y | Y | Y| Y |
| protected | Y | Y | Y | N
| default | Y | Y | N | N |
| private | Y | N | N | N |
## Non-access modifiers

* **final:** Used to declare a constant variable, prevent methods from being overwritten, and prevent other classes from extending the class.
* **static:** Used for variables, methods, and classes that are not directly bound to an encapsulating class instance.

**Note:** Static methods and variables should be accessed via the class itself instead of an object instance.
## When to use static keyword?
* **Bạn nên sử dụng từ khóa "static" khi bạn muốn chia sẻ dữ liệu hoặc chức năng giữa tất cả các thể hiện của lớp mà không cần tạo thể hiện mới. Tuy nhiên, cần lưu ý rằng việc sử dụng quá nhiều biến và phương thức tĩnh có thể làm cho mã của bạn trở nên khó hiểu và khó bảo trì, vì chúng có thể tác động toàn cục và ảnh hưởng đến các phần khác trong ứng dụng của bạn.**
```
Foo foo = new Foo();
foo.getTotalFoo(); // static method in Foo class
instead
FooHelper.getTotalFoo(); // are much more readable and concise
```
## Variable scoping
* **Global variable: declared in encapsulating class that accesible anywhere in the class.**
* **Local variable: declared usually inside the method and only accessible within that method.**
```
public class Foo {
  private String bar; // Global scope available anywhere in this class
  public void greetBar() {
    String foo; // Local scope only available inside this method
  } 
}
```
**Note: Scoping of methods and variable in java are always only within the curly brackets {} it was declared on**
## Guard clause
* **Guard clause is used to invert the logic and return early if the there was an validation triggered.**
* **Prevent nested if else**
* **When you use guard clause you will never use else statement in your life.**
* **Used with conjunction of throwing an error or return.**
```
// old code
public void add(String name) {
  if (name.equals("bar")) {
     // Rest of the code
  } else {
     System.out.println("Your are not bar");
  }
}

// New code
public void add(String name) {
  if (!name.equals("bar")) {
    System.out.println("You are not bar");
    // Here we check immediately if hes bar and return or throw an error early.
    return;
    // throw new Exception
  }
  // Rest of the code
}
```
#### What are most prefer return or throw an error
* **Đối với tôi, việc đưa ra lỗi sẽ an toàn hơn nhiều vì bạn có thể đảm bảo rằng phần còn lại của mã sẽ không thực thi nếu xác thực được kích hoạt, không giống như lỗi trả về có thể ẩn nấp nếu mã tiếp tục thực thi sau khi xác thực được kích hoạt.**

## What is class
* **Class acts like a blueprint to create an object that has properties = fields and behavior = methods.**
## What is abstract class and method
### Abstract Class
* **Used for not to create uncessary object**
* **Abstract class cannot be instantiate or created**
### Abstract Method
* **Abstract method is a method that has no implementation/body**
* **Abstract method is meant to be overwritten.**
## What is interface
* **By default methods in interface are public and abstract**
* **By default fields in interface are public, final and static.**
* **Used when you need multiple inheritance.**
* **Used when you need just a contract that implementing class can do what method is declared in interface.**
* **Used when you dont need class heirarchy because interfaces bypass class heirarchy.**
* **Interface can have static methods and default methods**
## Difference between static and default method in interface
* **They both need a body/implementatiom when declared in interface**
* **Default method: Can be overwritten.**
* **Static method: Cannot be overwritten.**
## Inheritance
* **Used to achieve polymorphism**
* **Inheritance is used if theres a common fields and methods to make code reusable and readable.**
* **Also if you want to have a relation between to classes to mimic real world objects.**
```
public class Animal {
  private String name;
  public void eat() {}
}


public class Dog extends Animal {
  private String breed;
  public Dog(String name, String breed) {
    super(name);
    this.breed = breed;
  }

  @Override
  public void eat() {}
}
```
## Three types of inheritance
* **Single level: Class that extends in another class.**
* **Multi level: Extending to a class that extends to another class**
* **Heirarchial: The parent class has 1 or more child class.**
* ![](./inheritance.jpg)
**Note: statics can be inherited but cannot be overwritten.**
## Polymorphism
* **Poly có nghĩa là nhiều và hình thái có nghĩa là có nhiều cách biểu diễn.**
### Two types of Polymorphism
* **Static/ Compile time Polymorphism:** Achieved via method overloading meaning methods that have same name but return type, parameters types, and parameter ordering are not the same. Basically methods that only the same name are called method overloading.
```
public void m1() { }
public void m1(DataType arg1) { }
```
* **Dynamic/ Runtime Polymorphism:** Achieved via method overriding meaning child class can do what is declared in parent class but has its own implementation or behavior.
```
public class Person {
  public void greet() { }
}

public class Student extends Person {
  @Override
   public void greet() {
     System.out.println("Student is greeting");
   }
}

public class Teacher extends Person {
  @Override
  public void greet() {
    System.out.println("Teacher is greeting");
  }
}

// As you can see student and teacher are extending in person class that has greet method but when they override that method thats it you have polymorphism and they are now have their behavior how to do greet.
```
**Note: You cannot achieve method overriding without inheritance.**
## Encapsulation
* **Implementation level**
* **Wrapping up the implementation data members and methods in a class. Used for data hiding.**\
You can achieve this by simply using getters and setters.\
Usage of private and final keywords to hide and control what other class can access.
## Abstraction
* **Design level**
* **Meaning hiding unecessary details and only showing valuable information.**
* **For example: Khi bạn có xe và chìa khóa, bạn khởi động xe bằng chìa khóa và thế là xe hoạt động ngay. Nhưng làm thế nào để chìa khóa khởi động xe thì thông tin này chúng ta không cần biết nhưng quyền quan trọng của nó là việc kiêng cữ có nghĩa là che giấu những chi tiết không cần thiết và chỉ hiển thị những thông tin có giá trị.**
* **Example 2: There are two type of motor right manual that has clutch and automatic has only has accelerator and dont have clutch. Automatic abstracts the clutch that we dont need to manually manage the clutch instead automatically handling it behind the scenes that we dont to care about.**
## Difference of this and super keyword
* **this: is used to reference the methods and fields of current object.**
```
public class Foo {
  private String bar;
  public void Foo(String bar) {
    this.bar = bar;
    // here the this keyword contains the current class methods and variables that you can access.
  }
}
```
* **super: used to reference the methods and fields of super class.**
```
public class Foo {
  public void greet() {
  // Code here
  }
}

public class Bar extends Foo {
  @Override
  public void greet() {
    super.greet(); // Will call the super class greet() method
    this.greet() // Will call the this current class greet() method
  }
}
```


