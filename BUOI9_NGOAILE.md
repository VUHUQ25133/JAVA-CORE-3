# BUỔI 9: LUÔN CÓ NGOẠI LỆ, XỬ LÍ NGOẠI LỆ

## I. Checked và Unchecked Exception, Error
Exception là một sự kiện bất ngờ xảy ra trong quá trình thực thi chương trình làm phá vỡ luồng chạy bình thường của chương trình. Một ngoại lệ có thể xảy ra với nhiều lý do khác nhau, nó nằm ngoài dự tính của chương trình. Một vài ngoại lệ xảy ra bởi lỗi của người dùng, một số khác bởi lỗi của lập trình viên và số khác nữa đến từ lỗi của nguồn dữ liệu vật lý... 

#### Phân cấp của Exception trong java.
- Class ở mức cao nhất là ***Throwable***
- Hai class con trực tiếp là *Error* và *Exception*.
Trong nhánh *Exception* có một nhánh con *RuntimeException* là các ngoại lệ sẽ không được java kiểm tra trong thời điểm biên dịch.

Chúng ta có hai loại *exception* là ***Checked*** & ***Unchecked***
Tất cả các *Checked exception* được kế thừa từ lớp *Exception* ngoại trừ lớp *RuntimeException*. *RuntimeException* là lớp cơ sở của tất cả các lớp *Unchecked exception*. Đó cũng là dấu hiệu để nhận biết đâu là *Checked* và đâu là *Unchecked*.

### Checked Exception
Là những *exception* có thể nhìn thấy và kiểm tra tại thời điểm biên dịch, extends từ lớp *Throwable* ngoại trừ *RuntimeException* và *Error*.

VD:

```
class Main { 
    public static void main(String[] args) {
        BufferedReader fileInput = null;
        FileReader file = new FileReader("C:\\test\\a.txt"); 
        fileInput = new BufferedReader(file); 
          
        // Print first 3 lines of file "C:\test\a.txt" 
        for (int counter = 0; counter < 3; counter++)  
            System.out.println(fileInput.readLine()); 
          
        fileInput.close(); 
    } 
}
```
==> ***Exception in thread “main” java.lang.RuntimeException: Uncompilable source code – unreported exception java.io.FileNotFoundException; must be caught or declared to be thrown at Main.main(Main.java:5)***

#### Sử dụng Try - catch để xử lý Checked Exception
- ***Try - catch*** là một công cụ giúp bạn bao bọc lấy đoạn code có khả năng xảy ra *Exception*. Hoặc các đoạn code đã được báo lỗi bởi hệ thống (chính là các *Checked Exception*). Các đoạn code mình nói đến này sẽ được chúng ta bao trong khối *try*. Để rồi nếu quả thực cái *Exception* đó xảy ra trong khối try đó, thì hệ thống sẽ nhanh chóng ***bẻ*** luồng logic của ứng dụng, chuyển sang thực thi các đoạn code bên trong khối *catch*.
```
class Main {
    public static void main(String[] args) {
        BufferedReader fileInput = null;
        try {
                FileReader file = new FileReader("C:\\test\\a.txt");
                fileInput = new BufferedReader(file);
                // Print first 3 lines of file "C:\test\a.txt"
                for (int counter = 0; counter < 3; counter++) {
                    System.out.println(fileInput.readLine());
                }
                fileInput.close();
        } catch (FileNotFoundException e) {
                System.out.println("FileNotFoundException rồi!!!");
        } catch (IOException e) {
                System.out.println("IOException rồi!!!");
        }
    }
}
```
==> ***FileNotFoundException rồi!!!***


### UnChecked Exception
- Khái niệm: là các *exception* không được kiểm tra tại thời điểm biên dịch. Hầu hết các *Unchecked exception* xảy ra do dữ liệu không hợp lệ trong quá trình tương tác với chương trình. Bắt buộc chúng ta phải thêm các điều kiện để kiểm tra dữ liệu nhầm đảm bảo chương trình chạy đúng cho mọi trường hợp. 
  
VD:
```
class Example {  
    public static void main(String args[])
    {
        int num1=10, num2=0;
        int res=num1/num2;
        System.out.println(res);
    }
}
```

==> ***Exception in thread "main" java.lang.ArithmeticException: / by zero***

Hoặc **ArrayIndexOutOfBoundsException** vì truy cập vào phần tử ngoài mảng

###  Error
- Là những vấn đề nghiêm trọng liên quan đến môi trường thực thi của ứng dụng hoặc hệ thống mà lập trình viên không thể kiểm soát. Nó thường làm chết chương trình. Lớp Error định nghĩa các ngoại lệ mà không thể bắt (catch) từ chương trình. 

Ví dụ: OutOfMemoryError, VirtualMachineError, and StackOverflowError, …
VD: chương trình đệ quy vô tận
```
public static void print(){
    print();
}
```


### Finally
- Khi một ngoại lệ xuất hiện, phương thức đang được thực thi có thể bị dừng mà không được hoàn thành. Nếu điều này xảy ra, thì các đoạn mã phía sau *(ví dụ như đoạn mã có chức năng thu hồi tài nguyên, như các lệnh đóng tập viết ở cuối phương thức)* sẽ không bao giờ được gọi. Java cung cấp khối **finally** để giải quyết việc này. Thông thường khối **finally** chứa các câu lệnh mang tính chất dọn dẹp như: đóng kết nối CSDL, đóng tệp tin,…

Khối lệnh **finally** trong java luôn được thực thi cho dù có ngoại lệ xảy ra hay không hoặc gặp lệnh *return* trong khối *try*.

```
try{
    //Các lệnh có khả năng ném ra ngoại lệ
    } catch(Exception1 ex1){
    …
    } catch(Exception2 ex2){
    …
    } catch(Exception exn){
    …
    } finally{
    //Mã lệnh dọn dẹp
}
```
Khối *finally* là tuỳ chọn, không bắt buộc phải có. Khối này được đặt sau khối catch cuối cùng. Chương trình sẽ thực thi câu lệnh đầu tiên của khối *finally* ngay sau khi gặp câu lệnh *return* hay lệnh *break* trong khối try.

Khối *finally* bảo đảm lúc nào cũng được thực thi, bất chấp có ngoại lệ xảy ra hay không. Hình minh họa sự thực hiện của các khối *try*, *catch* và *finally*

### Throw và throws
- Từ khóa *throw* dùng để ném ra một ngoại lệ cụ thể.
Chúng ta có thể ném một trong hai ngoại lệ *checked* hoặc *unchecked* trong java bằng từ khóa *throw*. Từ khóa *throw* chủ yếu được sử dụng để ném ngoại lệ tùy chỉnh (ngoại lệ do người dùng tự định nghĩa).

- Nếu một phương thức không xử lý một ngoại lệ đã kiểm tra thì phương thức đó phải khai báo ngoại lệ bằng từ khóa *throws*. Từ khóa *throws* được khai báo ở cuối dấu ngoặc () trước khi bắt đầu một phương thức.

### Tạo ra Exception của riêng mình
Tự tạo exception *(Custom Exception)* là một loại ngoại lệ do bạn tự định nghĩa hoặc tạo riêng cho ứng dụng của mình. *Custom Exception* trong Java được sử dụng để tùy biến ngoại lệ theo yêu cầu của người dùng. Bằng cách tạo ngoại lệ tùy chỉnh, bạn có thể xác định kiểu ngoại lệ cũng như thông điệp ngoại lệ riêng cho ứng dụng của bạn.
#### Tại sao cần sử dụng Custom Exception?
Khi bạn phát triển một ứng dụng Java phức tạp, có thể bạn muốn xử lý các tình huống đặc biệt mà các lớp ngoại lệ có sẵn trong Java không đáp ứng. Trong trường hợp này, việc tạo một ngoại lệ tùy chỉnh sẽ giúp bạn:
- Định rõ tình huống đặc biệt mà bạn muốn xử lý.
- Cung cấp thông điệp ngoại lệ riêng để ghi log hoặc hiển thị cho người dùng cuối.
- Tùy chỉnh cách xử lý ngoại lệ để phù hợp với logic ứng dụng của bạn.

*Custom Exception* cho phép bạn tạo ra các tình huống xử lý ngoại lệ đặc biệt trong ứng dụng của bạn và làm cho mã của bạn dễ đọc và dễ bảo trì hơn.