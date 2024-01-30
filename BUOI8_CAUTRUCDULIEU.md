#BUỔI 8 - CẤU TRÚC DỮ LIỆU TRONG JAVA
## 1. Cấu trúc dữ liệu
*Thuật ngữ cấu trúc dữ liệu đề cập đến một tập hợp dữ liệu với các hoạt động và hành vi hoặc thuộc tính được xác định rõ ràng. Cấu trúc dữ liệu là một cách duy nhất để lưu trữ hoặc tổ chức dữ liệu trong bộ nhớ máy tính để chúng ta có thể sử dụng nó một cách hiệu quả. Cấu trúc dữ liệu trong hầu hết mọi lĩnh vực của Khoa học máy tính, đó là Đồ họa máy tính, Hệ điều hành, Trí tuệ nhân tạo, Thiết kế trình biên dịch và nhiều lĩnh vực khác.*
### Sự cần thiết của cấu trúc dữ liệu trong Java
Khi lượng dữ liệu phát triển nhanh chóng, các ứng dụng trở nên phức tạp hơn và có thể phát sinh các vấn đề sau:

- **Tốc độ xử lý**: Do dữ liệu đang tăng lên từng ngày, nên cần phải xử lý tốc độ cao để xử lý lượng dữ liệu khổng lồ này, nhưng bộ xử lý có thể không xử lý được lượng dữ liệu nhiều đó.
- **Tìm kiếm dữ liệu**: Hãy xem xét một kho có kích thước 200 mặt hàng. Nếu ứng dụng của bạn cần tìm kiếm một mục cụ thể, nó cần phải duyệt qua 200 mục trong mỗi lần tìm kiếm. Điều này dẫn đến làm chậm quá trình tìm kiếm.
- **Nhiều yêu cầu cùng một lúc**: Giả sử, hàng triệu người dùng đang đồng thời tìm kiếm dữ liệu trên một máy chủ web, thì có khả năng máy chủ bị lỗi.

*Để giải quyết các vấn đề trên, chúng ta sử dụng cấu trúc dữ liệu. Cấu trúc dữ liệu lưu trữ và quản lý dữ liệu theo cách mà dữ liệu cần thiết có thể được tìm kiếm ngay lập tức.*

## 2. Interface Iterable, Collection -> List, Set, Queue.
**Iterator Interface của Collections trong Java cho phép chúng ta truy cập các phần tử của các tập hợp và được sử dụng để duyệt qua các phần tử trong tập hợp như *Map*, *List* hoặc *Set*. Nó giúp dễ dàng truy xuất các phần tử của một tập hợp và thực hiện các thao tác trên mỗi phần tử. Nó có một Interface con là ListIterator.**

Iterator Interface cung cấp 4 phương thức có thể được sử dụng để thực hiện các hoạt động khác nhau trên các phần tử của tập hợp:
-  **hasNext()**: Trả về true nếu tồn tại một phần tử trong tập hợp.
-  **next()**: Trả về phần tử tiếp theo của tập hợp.
-  **remove()**: Loại bỏ phần tử cuối cùng được trả về bởi next().
-  **forEachRemaining()**: Thực hiện hành động được chỉ định cho từng phần tử còn lại của tập hợp.
-  
### Các phương thức của interface Collection trong java

- **public boolean add(Object element)**:	Được sử dụng để chèn một phần tử vào collection.
- **public boolean addAll(Collection c)**:	Được sử dụng để chèn các phần tử collection được chỉ định vào collection gọi phương thức này.
- **public boolean remove(Object element)**:	Được sử dụng để xóa phần tử từ collection.
- **public boolean removeAll(Collection c)**:	Được sử dụng để xóa tất cả các phần tử của collection được chỉ định từ collection gọi phương thức này.
- **public boolean retainAll(Collection c)**:	Được sử dụng để xóa tất cả các thành phần từ collection gọi phương thức này ngoại trừ collection được chỉ định.
- **public int size()**:	Trả lại tổng số các phần tử trong collection.
- **public void clear()**:	Loại bỏ tổng số của phần tử khỏi collection.
- **public boolean contains(Object element)**:	Được sử dụng để tìm kiếm phần tử.
- **public boolean containsAll(Collection c)**:	ược sử dụng để tìm kiếm collection được chỉ định trong collection.
- **public Iterator iterator()**:	Trả về một iterator.
- **public Object[] toArray()**:	Chuyển đổi collection thành mảng (array).
- **public boolean isEmpty()**:	Kiểm tra nếu collection trống.
- **public boolean equals(Object element)**: So sánh 2 collection.
- **public int hashCode()**: Trả về số hashcode của collection.

### Collection trong Java

**- Set:** là một collection không thể chứa 2 giá trị trùng lặp. Set được sử dụng để biểu diễn các bộ, chẳng hạn như bộ tú lu khơ, thời khóa biểu của học sinh, các tiến trình đang chạy trên máy tính...
**- List:** là một collection có thứ tự (đôi khi còn được gọi là một chuỗi). List có thể chứa các phần tử trùng lặp. Thường có quyền kiểm soát chính xác vị trí các phần tử được chèn vào và có thể truy cập chúng bằng chỉ số (vị trí của chúng).
**- Queue (hàng đợi):** là một collection được sử dụng để chứa nhiều phần tử trước khi xử lý. Bên cạnh các thao tác cơ bản của collection, Queue cung cấp các thao tác bổ sung như chèn, lấy ra và kiểm tra. Queue có nguyên tắc sử dụng là FIFO (first-in, first-out - vào trước, ra trước)

## 3. Interface Map, SortedMap -> HashMap, TreeMap.
Map trong Java là một interface thuộc Java Collections Framework, đại diện cho một cấu trúc dữ liệu dạng map, cho phép lưu trữ và truy cập dữ liệu dưới dạng các cặp key-value (khóa – giá trị). Trong Java, *java.util.Map* là interface cơ bản mà các lớp triển khai map phải tuân theo. Các cặp key-value trong map giúp tổ chức và quản lý dữ liệu theo cách hiệu quả và dễ dàng.

**SortedMap** là một interface trong collection framework. Nó là một interface thừa kế từ Map interface có đầy đủ các chức năng mà Map định nghĩa, ngoài ra các phần tử trong SortedMap sẽ được sắp xếp theo thứ tự của key, mà một trong những implementation điển hình của nó là TreeMap.
SortedMap là một interface vì thế chúng ta không thể khởi tạo trực tiếp mà phải *thông qua một implementation* của nó, trong phần này mình sẽ sử dụng TreeMap.

Đặc điểm chính của SortedMap là nó sắp xếp thứ tự các key theo thứ tự tự nhiên của chúng hoặc một bộ triển khai so sánh các key được chỉ định. Vì vậy, hãy cân nhắc sử dụng TreeMap khi bạn muốn có một Map đáp ứng các tiêu chí sau:
- Key hoặc value đều không được NULL.
- Các key được sắp xếp theo thứ tự tự nhiên hoặc theo một bộ so sánh được chỉ định cụ thể.

```Java
import java.util.Iterator; 
import java.util.Map; 
import java.util.Set; 
import java.util.SortedMap; 
import java.util.TreeMap; 
  
public class SortedMapExample { 
    public static void main(String[] args) 
    { 
        SortedMap<Integer, String> sm = new TreeMap<Integer, String>(); 

        //Phương thức put(Key, Value) để thêm phần tử vào Map
        sm.put(new Integer(2), "practice"); 
        sm.put(new Integer(3), "quiz"); 
        sm.put(new Integer(4), "contribute"); 

        //Phương thức put(Key, Value) để cập nhật Value cho Key đã có trong Map
        sm.put(new Integer(4), "code"); 
        sm.put(new Integer(1), "deftblog"); 

        //Phương thức remove(Key) xóa phần tử có Key trong Map
        sm.remove(3);


        //Một vài cách Duyệt SortedMap

        //Duyệt xuôi cách 1:
        for(int key : sm.keySet())
        {
            String value = (String)sm.get(key);
            System.out.println("Key: " + key + "  value: " + value);
        }

        //Duyệt xuôi cách 2:
        for(Map.Entry<Integer, String> entry : sm.entrySet())
        {
            int key = entry.getKey();
            String value = entry.getValue();
            System.out.println("Key: " + key + "  value: " + value);
        }
    } 
}
```
Output:
```Java
    Key: 1 value: deftblog
    Key: 2 value: practice
    Key: 4 value: code
```

### HashMap và TreeMap

**HashMap** là một lớp triển khai của giao diện Map trong Java. Nó sử dụng bảng băm để lưu trữ dữ liệu, cho phép thao tác nhanh chóng với các phần tử của nó. Lưu ý rằng, khi sử dụng Hashmap thì thứ tự các phần thử sẽ không được đảm bảo. Ngoài ra, nó cho phép sử dụng cả key và value là null.

**LinkedHashMap** kế thừa HashMap và triển khai giao diện Map. Nó duy trì thứ tự của các phần tử được thêm vào dựa trên thời điểm chúng được thêm. Nói cách khác, các phần tử được truy cập theo thứ tự chúng được thêm vào. Ngoài ra, LinkedHashmap cho phép sử dụng key và value là null.

**TreeMap** là một lớp triển khai của giao diện Map và được xây dựng dựa trên cây đỏ đen (Red-Black Tree). Nó duy trì thứ tự của các phần tử dựa trên khóa (key) của chúng, nghĩa là các phần tử được sắp xếp theo khóa. Khác với hashmap và linkedhashmap, Treemap chỉ cho phép sử dụng value là null.

## Sort
Interface Comparable<T> cung cấp một phương thức để sắp xếp list object là int compare(T o1, T o2). Việc chúng ta chỉ là implement interface này.

```Java
public class Student implements Comparator<Student> {
    // Các method và field như ở trên
    @Override
    public int compare(Student o1, Student o2) {
        return o1.getAge() - o2.getAge();
    }
}
```


Và gọi java.util.Collections.sort để sắp xếp.
```Java
List<Student> students = new ArrayList<>();
students.add(new Student("Jonh", 17));
students.add(new Student("Peter", 19));
students.add(new Student("Henry", 18));
java.util.Collections.sort(students, new Student());
students.forEach(e -> System.out.println(e));
```
Kết quả:
```Java
Student{name='Jonh', age=17}
Student{name='Henry', age=18}
Student{name='Peter', age=19}
```
Sử dụng **anonymous comparator** để so sánh Thay vì implement trực tiếp từ interface Comparator<T>, chúng ta có thể sử dụng anonymous comparator như sau:
```Java
List<Student> students = new ArrayList<>();
students.add(new Student("Jonh", 17));
students.add(new Student("Peter", 19));
students.add(new Student("Henry", 18));
Collections.sort(students, new Comparator<Student>() {
    @Override
    public int compare(Student o1, Student o2) {
        return o1.getAge() - o2.getAge();
    }
});

students.forEach(e -> System.out.println(e));
```

Vẫn sử dụng class Student ở trên, nhưng chúng ta sẽ implements interface ```Comparable<Student>``` và override lại method ```compareTo(Student o)```
```Java
@Override
public int compareTo(Student o) {
    return this.getAge() - o.getAge();
}
```
