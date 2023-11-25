# Buổi 5:  DEV THÌ KHÔNG CHỈ VIẾT CODE

##  Version control là gì và tại sao cần dùng nó?
- Hệ thống quản lý phiên bản *(Version Control Systems - VCS)* là các công cụ để theo dõi những thay đổi trong mã nguồn (hay các thư mục và tập tin). 
- Hhệ thống giúp lập trình viên có thể lưu trữ nhiều phiên bản khác nhau của một mã nguồn được nhân bản (clone) từ một kho chứa mã nguồn (repository), mỗi thay đổi vào mã nguồn trên local sẽ có thể ủy thác (commit) rồi đưa lên server nơi đặt kho chứa chính.

### Tác dụng của VCS
- Lưu lại lịch sử các version của bất kỳ thay đổi nào của dự án. Giúp xem lại các sự thay đổi hoặc khôi phục (revert) lại sau này.

- Việc chia sẻ code trở nên dễ dàng hơn, lập trình viên có thể để public cho bất kỳ ai, hoặc private chỉ cho một số người có thẩm quyền có thể truy cập và lấy code về.

## 2. Các khái niệm về Git
###  Git
Git là một trong những hệ thống quản lý phiên bản phân tán (Distributed Version Control System – DVCS) phổ biến nhất hiện nay. Git cung cấp cho mỗi lập trình viên kho lưu trữ (repository) riêng chứa toàn bộ lịch sử thay đổi.
#### *Cách hoạt động:
Git coi thông tin được lưu trữ là một tập hợp các snapshot – ảnh chụp toàn bộ nội dung tất cả các file tại thời điểm.
Mỗi khi bạn “commit”, Git sẽ “chụp” và tạo ra một snapshot cùng một tham chiếu tới snapshot đó.
### a) Repository, Branch...
(Gọi tắt là Repo) là nơi chứa tất cả những thông tin cần thiết để duy trì và quản lý các sửa đổi và lịch sử của toàn bộ project.
    - Local Repository: là repo nằm trên chính máy tính của chúng ta, repository này sẽ đồng bộ hóa với remote repository bằng các lệnh của git.
    - Remote Repository: là repo được cài đặt trên server chuyên dụng. Ví dụ: GitHub, GitLab, Bitbucket,...


- Các Branch (nhánh) đại diện cho các phiên bản cụ thể của một kho lưu trữ tách ra từ project chính của bạn.
- Branch cho phép bạn theo dõi các thay đổi thử nghiệm bạn thực hiện đối với kho lưu trữ và có thể hoàn nguyên về các phiên bản cũ hơn. Ví dụ:
```
            A---B---C new_feature
            /
    D---E---F---G master
```
- Commit: Hành động ghi lại sự thay đổi trong repository của bạn. Mỗi commit có commit message để giải thích commit này có sự thay đổi gì.
- Merge: Một lệnh dùng để hợp nhất các chi nhánh độc lập thành một nhánh duy nhất trong Git.
- Push: Hành động đưa nội dung của local_repo lên remote_repo. Push là cách bạn chuyển giao các commit từ local_repo của bạn lên remote_repo. 
Cấu trúc lệnh push cơ bản:  `git push remote_name branch_name `

- Pull: Pull requests thể hiện các đề xuất thay đổi cho nhánh chính.
- Clone: Hành động thực hiện tải một bản sao có sẵn của một remote repository server nào đó (có thể là dự án bạn tham gia). Clone được sử dụng để tạo bản sao cục bộ của kho lưu trữ. 
Cú pháp:  `git clone <:clone git url:>`

Ví dụ: `$ git clone git@github.com:hapo-nghialuu/tutorial.git`

- Fork: Một fork là một bản copy của một repository (Kho chứa source code của bạn trên Github). Fork được sử dụng để tạo bản sao phía máy chủ.

## 3. Pull request
- Khái niệm: Pull request được tạo ra để đưa những file source code của bạn lên 1 host chung nơi mọi người có quyền truy cập sẽ truy cập vào và cùng review, để lại comment trên những file source code đó. 
- Cách tạo pull request trong Github:
    - Bước 1: Fork dự án gốc.
       - Truy cập vào dự án gốc trên GitHub.
       - Nhấn vào nút “Fork” ở góc trên bên phải để sao chép dự án vào tài khoản của bạn.
    - Bước 2: Clone dự án về máy.
    - Bước 3: Tạo nhánh mới
       - Sử dụng lệnh `git checkout -b [tên_nhánh]` để tạo và chuyển đổi sang một nhánh mới.
    - Bước 4: Thực hiện thay đổi.
    - Bước 5: Commit và Push.
       - Sử dụng lệnh `git commit -m "Mô tả commit"` để commit các thay đổi đã thêm.
       - Sử dụng lệnh `git push origin [tên_nhánh]` để đẩy thay đổi lên repository của bạn trên GitHub.
    - Bước 6: Tạo Pull Request.
       - Truy cập vào repository của bạn trên GitHub.
       - Nhấn vào nút “Compare & pull request” bên cạnh tên nhánh của bạn.
       - Điền thông tin cần thiết, mô tả về Pull Request và nhấn “Create Pull Request“.
    - Bước 7: Kiểm tra xử lí và yêu cầu chỉnh sửa.
       - Nhóm quản lý dự án sẽ xem xét và thảo luận về Pull Request của bạn.
       - Nếu cần chỉnh sửa, bạn chỉ cần thêm commit vào nhánh đã tạo và Pull Request sẽ tự động cập nhật.
    - Bước 8: Pull Request được chấp nhận và merge
       - Sau khi Pull Request đạt yêu cầu, nhóm quản lý sẽ chấp nhận và merge vào nhánh chính.
       - Code của bạn đã được hợp nhất vào dự án gốc.

## 4.  UML là gì? Lí do cần vẽ UML
**UML** ( Unified Modeling Language - ngôn ngữ mô hình hóa thống nhất) là một ngôn ngữ mô hình gồm các ký hiệu đồ họa mà các phương pháp hướng đối tượng sử dụng để thiết kế các hệ thống thông tin một cách nhanh chóng.

- **UML** sử dụng một hệ thống ký hiệu thống nhất biểu diễn các Phần tử mô hình (*model elements*). Tập hợp các phần tử mô hình tạo thành các **Sơ đồ UML** (UML diagrams). Có các loại sơ đồ UML chủ yếu sau:

    - *Sơ đồ lớp* (Class Diagram)
    - *Sơ đồ đối tượng* (Object Diagram)
    - *Sơ đồ tình huống sử dụng* (Use Cases Diagram)
    - *Sơ đồ trình tự* (Sequence Diagram)
    - *Sơ đồ cộng tác* (Collaboration Diagram hay là Composite Structure Diagram)
    - *Sơ đồ trạng thái* (State Machine Diagram)
    - *Sơ đồ thành phần* (Component Diagram)
    - *Sơ đồ hoạt động* (Activity Diagram)
    - *Sơ đồ triển khai* (Deployment Diagram)
    - *Sơ đồ gói* (Package Diagram)
    - *Sơ đồ liên lạc* (Communication Diagram)
    - *Sơ đồ tương tác* (Interaction Overview Diagram - UML 2.0)
    - *Sơ đồ phối hợp thời gian* (Timing Diagram - UML 2.0)

- **Lí do cần vẽ UML**:
    - *Hiểu rõ Yêu Cầu*: UML giúp mô tả và hiểu rõ các yêu cầu của hệ thống từ góc độ người quản lý dự án và người sử dụng.
    - *Thiết Kế Hệ Thống*: UML cung cấp các biểu đồ và ký hiệu để thiết kế cấu trúc và cách thức hoạt động của hệ thống.
    - *Giao Tiếp Hiệu Quả*: UML tạo ra một ngôn ngữ chung để mô tả ý tưởng và thiết kế, giúp tăng cường giao tiếp giữa các thành viên trong nhóm phát triển và giữa nhóm phát triển và người quản lý.
    - *Tạo Ra Tài Liệu Hệ Thống*: UML giúp tạo ra tài liệu dự án đồng thời và thực hiện, giúp dễ dàng theo dõi và duy trì hệ thống.
    - *Kiểm Tra và Đánh Giá Thiết Kế*: Các biểu đồ UML, như biểu đồ lớp, biểu đồ tuần tự, và biểu đồ use case, có thể được sử dụng để kiểm tra và đánh giá thiết kế của hệ thống trước khi bắt đầu quá trình phát triển.
    - *Quản Lý Các Yếu Tố Phức Tạp*: UML giúp quản lý sự phức tạp của hệ thống bằng cách tạo ra các mô hình trừu tượng để giảm bớt sự phức tạp và tăng tính rõ ràng.
    - *Phân Chia Công Việc*: UML có thể được sử dụng để phân chia công việc giữa các thành viên trong nhóm phát triển và làm cho mỗi người hiểu rõ vai trò và trách nhiệm của mình.

## 5. Class Diagram, Activity Diagram
### Class Diagram
- Định nghĩa:
    - Class diagram mô tả kiểu của các đối tượng trong hệ thống và các loại quan hệ khác nhau tồn tại giữa chúng.
    - Là một kỹ thuật mô hình hóa tồn tại ở tất cả các phương pháp phát triển hướng đối tượng.
    - Biểu đồ hay dùng nhất trong UML và gần gũi nhất với các lập trình viên.
    - Giúp các lập trình viên trao đổi với nhau và hiểu rõ ý tưởng của nhau.
    - Các thành phần của lớp.
        - Tên class.
        - Thuộc tính.
        - Phương thức.
- ***Relationship trong Class Diagram***

    \-  Association: quan hệ giữa hai lớp với nhau, thể hiện chúng có liên quan với nhau.
    \- Aggregation: Đối tượng tạo từ class A mất thì đối tượng tạo từ class B vẫn tồn tại độc lập. 
    \- Composition: Đối tượng tạo từ class A mất thì đối tượng tạo từ class B sẽ mất.
    \- Inheritance: 1 class kế thừa từ 1 class khác.
- ***Multiplicity trong Class Diagram***

    Sử dụng để thể hiện quan hệ về số lượng giữa các đối tượng được tạo từ các class trong class diagram.

    - 0…1: 0 hoặc 1
    - n : Bắt buộc có n
    - 0…* : 0 hoặc nhiều
    - 1…* : 1 hoặc nhiều
    - m…n: có tối thiểu là m và tối đa là n

### Activity Diagram
- Là một mô hình logic dùng để mô hình hóa các hoạt động trong một quy trình nghiệp vụ.
- Là sơ đồ luồng xử lí của hệ thống, bao gồm luồng đi của dòng dữ liệu, dòng sự kiện.
- ***Các thành phần của Activity Diagram: ***
    - Start
        
        + Khởi tạo một hoạt động.
        + Một activity diagram có thể có nhiều trạng thái Start.
    - Transition:


        Mô tả sự chuyển đổi trạng thái của các hoạt động
    - Activity:


        Mô tả hành vi của đối tượng trong quy trình
    - Branch:

        + Mô tả điều kiện rẽ nhánh
        + Chỉ một dòng điều khiển đi vào
        + Hai hoặc nhiều dòng điều khiển đi ra
        + Chỉ một dòng điều khiển dẫn đến kết quả
        + Mỗi dòng chứa một điều kiện, điều kiện phải liên quan đến điều kiện và loại trừ nhau.
    - Fork:

        + Mô tả một dòng điều khiển được tách ra thực hiện song song
        + Chỉ có một dòng điều khiển đi vào
        + Có hai hoặc nhiều dòng điều khiển đi ra
        + Dùng FORK khi các hoạt động thực hiện không quan tâm thứ tự
    - End: 
         
        + Mô tả trạng thái kết thúc quy trình
        + Một Activity Diagram có thể có một hoặc nhiều trạng thái kết thúc.
