# BUỔI 3: CÁCH JAVA LƯU TRỮ DỮ LIỆU
    Nội dung:
    - Cách Java lưu trữ dữ liệu(kiểu dữ liệu nguyên thuỷ, kiểu dữ liệu object, class object, wrapper, boxing, unboxing).
    - Các phương thức khởi tạo trong Java (từ khóa super và this).
    - Garbage Collector trong Java .
    - Pass by value trong Java
# 1. Cách Java lưu trữ dữ liệu
*Khi chạy chương trình Java, JVM sẽ yêu cầu hệ điều hành (Windows, Linux, Mac...) cấp phát một không gian bộ nhớ trong RAM. JVM sẽ phân chia không gian bộ nhớ này được cấp phát thành các vùng nhớ khác nhau để lưu những dữ liệu cần thiết cho việc chạy chương trình.*
## 1.1.  Trong Java, có 2 loại kiểu dữ liệu:
- Kiểu dữ liệu nguyên thủy: int, long, float, double, char, ...
- Kiểu dữ liệu đối tượng: Aray, String, Class, Interface, ...

## 1.2. Class Object
*Mặc định lớp Object là lớp cha của tất cả các lớp trong java. Nói cách khác nó là một lớp cao nhất trong java.*
![](image.png)
*Sử dụng lớp Object là hữu ích nếu bạn muốn tham chiếu bất kỳ đối tượng nào mà bạn chưa biết kiểu dữ liệu của đối tượng đó.*

>     Ví dụ: Giả sử phương thức getObject() trả về một đối tượng nhưng nó có thể là bất kỳ kiểu nào như Employee,Student, ... chúng ta có thể sử dụng biến tham chiếu của lớp Object để tham chiếu tới đối tượng đó.

## 1.3. Lớp Wrapper, Boxing, Unboxing

*Lớp Wrapper trong java cung cấp cơ chế để chuyển đổi kiểu dữ liệu nguyên thủy thành kiểu đối tượng (Boxing) và từ đối tượng thành kiểu dữ liệu nguyên thủy (Unboxing).*


```
//Các dạng Boxing
int a=100;
Integer i = new Integer(a);
Float f = new Float(4.5);
Charater ch = new Character('a');
Boolean b = new Boolean(true);

// Các dạng Autoboxing
int a = 500;
Integer i = a;
Float f = 4.5f;
Character ch = 'a';
```
```
//  Unboxing Cách 1
int a = 500;
Integer i = a;
int i2 = i.intValue();
Float f = 4.5f;
float f2 = f.floatValue();
Character ch = 'a';
char ch1 = a.charValue();

//  Unboxing Cách 2
int a = 500;
Integer i = a;
int i2 = i;
Float f = 4.5f;
float f2 = f;
Character ch = 'a';
char ch2 = ch;
```
## Các phương thức của lớp Wrapper:
*- parseX: Tham số truyền vào cho phương thức này là 1 chuỗi, kết quả nhận được là một giá trị nguyên thủy của chuỗi truyền vào.(VD: int i = Integer.parseInt("10");
float f = Float.parseFloat("4.5");)*

*- toString(): VD: String s = Integer.toString(10);*

*- xxxValue()*

*- compareTo()*

    Với việc bạn gọi lop1.compareTo(lop2), thì kết quả sẽ như sau.

    – Nếu kết quả của phương thức trả về một số âm, thì lop1 sẽ có giá trị nhỏ hơn lop2.
    – Nếu kết quả của phương thức trả về số 0, thì lop1 sẽ có giá trị bằng với lop2.
    – Nếu kết quả của phương thức trả về một số dương, thì lop1 sẽ có giá trị lớn hơn lop2.

# 2. Các phương thức khởi tạo
Cú pháp:
```
[khả_năng_truy_cập]  tên_phương_thức  () {
     // Các dòng code
}
```
## a. Super
*Là một biến tham chiếu, được sử dụng để tham chiếu trực tiếp đến đối tượng của lớp cha gần nhất.*
- Tham chiếu đến biến của lớp cha
    ```
    class Vehicle{
    int maxspeed = 50;
    }

    public class Bike extends Vehicle{
        int maxspeed = 100;
        void display(){
        System.out.println(super.maxspeed);
        }
        public static void main(String args[]){
            Bike b = new Bike();
            b.display(); // 50
        }
    }
    ```

- Truy xuất đến phương thức của lớp cha gần nhất
    ```
    class Hinhhoc{
        String ten;
        public void Display(){
            System.out.println(ten);
        }
    }

    public class HinhTron extends Hinhhoc{
        public HinhTron(){
            ten = "Hình Tròn";
        }
        public void Display(){
            super.Display();
            System.out.println("DONE");
        }
        public static void main(String args[]){
            HinhTron ht = new HinhTron();
            ht.Display();
        }
    }
    ```
- Gọi trực tiếp Constructor của lớp cha
    ```
    class Vehicle {
        Vehicle() {
            System.out.println("Vehicle created");
        }
    }
    
    class Bike2 extends Vehicle {
        Bike2() {
            super();//gọi Constructor của lớp cha  
            System.out.println("Bike created");
        }
    
        public static void main(String args[]) {
            Bike2 b = new Bike2();
        }
    }
    ```
## b. Từ khóa this
- Tham chiếu tới biến của lớp hiện tại: Nếu biến toàn cục và tham số trùng tên nhau thì this phân biệt 2 cái này:
    ```
    public class Student{
        int id;
        String name;
        Student(int id,String name){
            this.id=id;
            this.name=name;
        }
        void dis(){
            System.out.println(id + " " + name);
        }
        public static void main(String args[]){
            Student s1 = new Student(111, "BAC");
            Student s2 = new Student(222,"NAM");
            s1.dis();
            s2.dis();
        }
    }
    ```
- Gọi Constructor của lớp hiện tại
    ```
    public class Student{
        int id;
        String name;
        Student (){
            System.out.println("gọi Student");
        }
        Student(int id, String name) {
            this();
            this.id = id;
            this.name = name;
        }
        void in(){
            System.out.println(id + " " + name);
        }
        public static void main(String args[]) {
            Student s1 = new Student(111, "BAC");
            Student s2 = new Student(222, "NAM");
            s1.in();
            s2.in();
        }
    }
    ```

- Gọi phương thức của lớp hiện tại
    ```
    public class Student{
        void m(){
            System.out.print("Gọi phương thức bằng từ khóa this");
        }
        void in() {
            m();
        }
        public static void main(String args[]){
            Student s = new Student();
            s.in();
        }
    }
    ```

- Sử dụng từ khóa this như 1 tham số của phương thức/Constructor
    ```
    public class EG {
        void m(EG obj) {
            System.out.println("Hello Java");
        }

        void p() {
            m(this);
        }

        public static void main(String args[]) {
            EG o1 = new EG();
            o1.p();
        }
    }
    ```

- Trả về kết quả của lớp hiện tại
    ```
    Class A{
        A getA(){
            return this;
        }
        void msg(){
            System.out.println("Hello Java");
        }
    }
    Class Test1{
        public static void main(String args[]){
            new A().getA().msg();
        }
    }
    ```
    ```
    public class Student{
        String name;
        String age;
        public Student(String name, String age){
            this.name=name;
            this.age=age;
        }
        public Student getStudent(){
            return this;
        }
        public static void main(String args[]){
            Student s = new Student("Green","18");
            System.out.println(s.getStudent().name);
            System.out.println(s.getStudent().age);
        }
    }
    ```

# 3. Garbage Collection trong Java
*Trong java, garbage có nghĩa là các đối tượng không được tham chiếu.\
Garbage Collection là quá trình tự động lấy lại bộ nhớ không sử dụng thời gian chạy. Nói cách khác, đó là một cách để phá hủy các đồ vật không sử dụng.\
Nó được thực hiện tự động, Vì vậy, java cung cấp quản lý bộ nhớ tốt hơn.*

- Ưu điểm của Garbage Collection:
    Trong C++, sau khi khởi tạo một Object, các lập trình viên phải chủ động xóa vùng nhớ của Object bằng câu lệnh delete, nếu như không thực hiện việc này thì sẽ dẫn đến rò rỉ vùng nhớ. Với Garbage Collectors, lập trình viên Java sẽ không cần quan tâm đến việc xóa các Object mỗi lần ra khỏi hàm hay không còn dùng nữa. 
- Các Bước:
  - B1: Vô hiệu hóa đối tượng( Gán giá trị null, Gán đối tượng đến một tham chiếu khác, Bởi 1 đối tượng annonymous)
  - B2: 
    - Sử dụng phương thức System.gc(): Lớp hệ thống chứa phương thức static gc() để yêu cầu JVM chạy Garbage Collector.
    - Sử dụng phương thức Runtime.getRuntime().gc(): Lớp Runtime cho phép ứng dụng giao tiếp với JVM mà ứng dụng đang chạy. Do đó, bằng cách sử dụng phương thức gc() của nó, chúng ta có thể yêu cầu JVM chạy Garbage Collector.
 # 5. Pass by value
- Nếu chúng ta gọi 1 phương thức và truyền giá trị cho một giá trị cho phương thức đó được gọi là truyền giá trị (Pass by value).
- Việc thay đổi giá trị chỉ có hiệu lực trong phương thức được gọi, không có hiệu lực bên ngoài phương thức.

\
VD:

```
public class Operation1 {
    int data = 50;
 
    void change(int data) {
        data += 100;
    }
 
    public static void main(String args[]) {
        Operation1 op = new Operation1();
 
        System.out.println("Trước khi thay đổi: " + op.data);
        op.change(500);
        System.out.println("Sau khi thay đổi: " + op.data);
    }
}
```
