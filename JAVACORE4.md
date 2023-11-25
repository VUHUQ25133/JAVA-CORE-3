# BUỔI 4: MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG
## 1. Tính đóng gói
    - Là kỹ thuật ẩn giấu thông tin không liên quan và hiển thị ra thông tin liên quan với mục đích giảm thiểu mức độ phức tạp phát triển phần mềm.
- Để đạt được đóng gói trong Java chúng ta cần: 
  - Khai báo các biến của một lớp là private. 
  - Cung cấp phương thức setter và getter là public để có thể sửa đổi và xem các giá trị biến.
```
public class Student {
    private String name;
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
public static void main(String[] args){
        Student student = new Student();
        student.setName("DEPTRY");
        System.out.println(student.getName());
    }
```
## 2. Tính kế thừa
- Là sự liên quan giữa 2 class với nhau, trong đó có class cha (Superclass) và class con (Subclass).

- Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên nó chỉ truy cập được các thành viên public và protected của class cha.

==> Kế thừa trong Java là có thể tạo ra một class mới được xây dựng trên các lớp đang tồn tại.
```
class Subclass_name extends Superclass_name{
    //methods and fields
}
```
VD:
```
class Student1{
    private String name;
    Student1 (String name){
        this.name=name;
    }
    public String getName(){
        return name;
    }

}
class Student2 extends Student1{
    private int age;
    Student2 (String name,int age){
        super(name);
        this.age=age;
    }
    public int getAge() {
        return age;
    }
}
public class Student {
    public static void main(String[] args){
        Student2 student = new Student2("DEPTRY",19);
        System.out.println("Name: " + student.getName());
        System.out.println("Age:  " + student.getAge());
    }
}
```
### Các kiểu kế thừa:
### a) Đơn kế thừa
VD:
```
public class Animal {
    public void eat() {
        System.out.println("eating...");
    }
}
public class Dog extends Animal {
    public void bark() {
        System.out.println("barking...");
    }
}
public class TestInheritance {
    public static void main(String args[]) {
        Dog d = new Dog();
        d.bark();
        d.eat();
    }
}
```
###  b) Kế thừa nhiều lớp
VD:
```
class Animal{
    public void Go(){
        System.out.println("go...");
    }
}
class Dog extends Animal{
    public void Sleep(){
        System.out.println("zzz...");
    }
}
class BabyDog extends Dog{
    public void Smile(){
        System.out.println("Haha...");
    }
}
public class Test {
    public static void main(String[] args){
        BabyDog babyDog = new BabyDog();
        babyDog.Go();
        babyDog.Sleep();
        babyDog.Smile();
    }
}
```
### c) Kế thừa thứ bậc
VD:
```
class Animal{
    public void Go(){
        System.out.println("go...go ...");
    }
}
class Dog extends Animal{
    public void Sleep(){
        System.out.println("zzz...zzz...");
    }
}
class BabyDog extends Animal{
    public void Smile(){
        System.out.println("He...He...");
    }
}
public class Test {
    public static void main(String[] args){
        BabyDog babyDog = new BabyDog();
        babyDog.Go();
        babyDog.Smile();
    }
}
```
### *Lợi ích của kế thừa trong Java*
- Để ghi đè phương thức (Method Overriding), do đó có thể thu được tính đa hình tại runtime.
- Để làm tăng tính tái sử dụng của code.
### *Tại sao đa kế thừa không được support trong Java*
Để giảm thiểu sự phức tạp và đơn giản hóa ngôn ngữ, đa kế thừa không được support trong java. Hãy suy xét kịch bản sau: Có 3 lớp A, B, C. Trong đó lớp C kế thừa từ các lớp A và B. Nếu các lớp A và B có phương thức giống nhau và bạn gọi nó từ đối tượng của lớp con, như vậy khó có thể xác đinh được việc gọi phương thức của lớp A hay B. Java sẽ print ra lỗi “compile time error” nếu bạn cố tình kế thừa 2 class.

## 3. Tính đa hình
*Là khả năng một đối tượng có thể thực hiện một tác vụ theo nhiều cách khác nhau.*
- Được thể hiện rõ nhất qua việc gọi phương thức của đối tượng. Các phương thức hoàn toàn có thể giống nhau, nhưng việc xử lý luồng có thể khác nhau. Hay nói cách khác: Tính đa hình cung cấp khả năng cho phép người lập trình *gọi trước một phương thức của đối tượng*, tuy chưa xác định đối tượng có phương thức muốn gọi hay không. Đến khi thực hiện (run-time), chương trình mới xác định được đối tượng và gọi phương thức tương ứng của đối tượng đó.
- Trong Java, chúng ta sử dụng nạp chồng phương thức (method overloading) và ghi đè phương thức (method overriding) để có tính đa hình. 
  - Nạp chồng (Overloading): Đây là khả năng cho phép một lớp có nhiều thuộc tính, phương thức cùng tên nhưng với các tham số khác nhau về loại cũng như về số lượng. Khi được gọi, dựa vào tham số truyền vào, phương thức tương ứng sẽ được thực hiện. 
  - Ghi đè (Overriding): là hai phương thức cùng tên, cùng tham số, cùng kiểu trả về nhưng thằng con viết lại và dùng theo cách của nó, và xuất hiện ở lớp cha và tiếp tục xuất hiện ở lớp con. Khi dùng override, lúc thực thi, nếu lớp Con không có phương thức riêng, phương thức của lớp Cha sẽ được gọi, ngược lại nếu có, phương thức của lớp Con được gọi.

VD:
```
class Animal {
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.makeSound(); // In ra: "Animal makes a sound"

        Dog dog = new Dog();
        dog.makeSound(); // In ra: "Dog barks"
    }
}
```
