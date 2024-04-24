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




