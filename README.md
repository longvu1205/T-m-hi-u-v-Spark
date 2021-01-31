# Tìm hiểu về SPARK PROPERTIES, SPARK RDD VÀ SPARK DATAFRAME

## Phần 1: Tìm hiểu về Spark Properties
### *I. Đôi nét về Spark Properties*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Thuộc tính Spark – Spark Properties kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được cài đặt trực tiếp trên SparkConf được chuyển đến SparkContext của bạn. SparkConf cho phép định cấu hình một số thuộc tính chung (ví dụ: URL chính và tên ứng dụng), cũng như các cặp key-value thông qua phương thức set().

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; <b>Ví dụ:</b> Khởi tạo một ứng dụng với 2 luồng:
<p align="center"> <img src ="https://user-images.githubusercontent.com/77878466/105628034-fe3fb900-5e6c-11eb-91d4-637f6b2b5845.png"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Trong đó, local[2] cho biết tối thiểu có 2 luồng đang chạy song song, giúp phát hiện lỗi chỉ tồn tại khi chạy trong bối cảnh phân tán.
 </p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Các thuộc tính chỉ định một số khoảng thời gian với một đơn vị thời gian. Các định dạng sau được Spark chấp nhận:



#### *II. Cấu tạo của Spark*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Nhìn chung thì cấu tạo của Apache Spark gồm có 5 thành phần chính: Spark Core, Spark Streaming, Spark SQL, MLlib và GraphX, với thành phần trung tâm của Spark là Spark Core. Spark có thể chạy trên nhiều loại Cluster Managers như Hadoop YARN, Apache Mesos hoặc trên chính cluster manager được cung cấp bởi Spark được gọi là Standalone</p>

<p align="center"> <img src ="https://user-images.githubusercontent.com/77878466/105628034-fe3fb900-5e6c-11eb-91d4-637f6b2b5845.png" width="50%"/>
<p align="center"> <em>Thành phần của Spark</em> </p>

<ul align="justify">
  <li><b>Spark Core:</b> Là nền tảng cho các thành phần còn lại và các thành phần này muốn khởi chạy được thì đều phải thông qua Spark Core do Spark Core đảm nhận vai trò thực hiện công việc tính toán và xử lý trong bộ nhớ (In-memory computing) đồng thời nó cũng tham chiếu các dữ liệu được lưu trữ tại các hệ thống lưu trữ bên ngoài. Spark Core cung cấp những chức năng cơ bản nhất của Spark như lập lịch cho các tác vụ, quản lý bộ nhớ, fault recovery, tương tác với các hệ thống lưu trữ…Đặc biệt, Spark Core cung cấp API để định nghĩa RDD (Resilient Distributed DataSet) là tập hợp của các item được phân tán trên các node của cluster và có thể được xử lý song song.</li></br>

  <li><b>Spark SQL:</b> cho phép truy vấn dữ liệu cấu trúc qua các câu lệnh SQL. Spark SQL có thể thao tác với nhiều nguồn dữ liệu như Hive tables, Parquet, và JSON. Bên cạnh đó, Spark SQL cung cấp một kiểu data abstraction mới (SchemaRDD) nhằm hỗ trợ cho cả kiểu dữ liệu có cấu trúc (structured data) và dữ liệu nửa cấu trúc (semi-structured data). Spark SQL còn hỗ trợ DSL (Domain-specific language) để thực hiện các thao tác trên DataFrames bằng ngôn ngữ Scala, Java hoặc Python và nó cũng hỗ trợ cả ngôn ngữ SQL với giao diện command-line và ODBC/JDBC server.</li></br>
  
  <li><b>Spark Streaming:</b> được sử dụng để thực hiện việc phân tích stream bằng việc coi stream là các mini-batches và thực hiệc kỹ thuật RDD transformation đối với các dữ liệu mini-batches này. Qua đó cho phép các đoạn code được viết cho xử lý batch có thể được tận dụng lại vào trong việc xử lý stream, làm cho việc phát triển lambda architecture được dễ dàng hơn. Tuy nhiên điều này lại tạo ra độ trễ trong xử lý dữ liệu (độ trễ chính bằng mini-batch duration) và do đó nhiều chuyên gia cho rằng Spark Streaming không thực sự là công cụ xử lý streaming giống như Storm hoặc Flink.</li></br>
  
  <li><b>MLlib (Machine Learning Library):</b> Cung cấp rất nhiều thuật toán của học máy như: classification, regression, clustering, collaborative filtering...là một nền tảng học máy phân tán bên trên Spark do kiến trúc phân tán dựa trên bộ nhớ</li></br>
  
  <li><b>GraphX:</b> là nền tảng xử lý đồ thị dựa trên Spark. Nó cung cấp các Api để diễn tảcác tính toán trong đồ thị bằng cách sử dụng Pregel Api.</li></br>
</ul>

#### *III. Lợi ích nổi bật mà Spark mang lại*
<ul align="justify">
  <li><em>Xử lý dữ liệu</em>: Spark xử lý dữ liệu theo lô và thời gian thực</li>
  <li><em>Tính tương thích</em>: Có thể tích hợp với tất cả các nguồn dữ liệu và định dạng tệp được hỗ trợ bởi cụm Hadoop.</li>
  <li><em>Hỗ trợ ngôn ngữ</em>: hỗ trợ Java, Scala, Python và R.</li></br><li style="list-style-type: none">
      <p align="center"> <img src ="https://user-images.githubusercontent.com/77878466/105629301-c89ece00-5e74-11eb-853c-79337c833eda.png"/>
      <p align="center"> <em>Cơ cấu các ngôn ngữ Spark hỗ trợ (2014-2015)</em> </p></li>
    
  <li><em>Phân tích thời gian thực</em>: Apache Spark có thể xử lý dữ liệu thời gian thực tức là dữ liệu đến từ các luồng sự kiện thời gian thực với tốc độ hàng triệu sự kiện mỗi giây. Bên cạnh đó, Spark còn được sử dụng để xử lý phát hiện gian lận trong khi thực hiện các giao dịch ngân hàng. Đó là bởi vì, tất cả các khoản thanh toán trực tuyến được thực hiện trong thời gian thực và chúng ta cần ngừng giao dịch gian lận trong khi quá trình thanh toán đang diễn ra.</li>
  <li><em>Quản lý bộ nhớ</em>: Spark giải quyết các vấn đề vấn đề xung quanh định nghĩa Resilient Distributed Datasets (RDDs). RDDs hỗ trợ hai kiểu thao tác thao tác: transformations và action. Thao tác chuyển đổi(tranformation) tạo ra dataset từ dữ liệu có sẵn. Thao tác actions trả về giá trị cho chương trình điều khiển (driver program) sau khi thực hiện tính toán trên dataset.</li> 
</ul>

### B. MapReduce
#### *I. Đôi nét về MapReduce*

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; MapReduce là mô hình được thiết kế độc quyền bởi Google, nó có khả năng lập trình xử lý các tập dữ liệu lớn song song và phân tán thuật toán trên 1 cụm máy tính. MapReduce trở thành một trong những thành ngữ tổng quát hóa trong thời gian gần đây. MapReduce sẽ bao gồm 2 thủ tục là một thủ tục Map() và 1 thủ tục Reduce(). Thủ tục Map() bao gồm lọc (filter) và phân loại (sort) trên dữ liệu khi thủ tục khi thủ tục Reduce() thực hiện quá trình tổng hợp dữ liệu. Đây là mô hình dựa vào các khái niệm biển đối của bản đồ và reduce những chức năng lập trình theo hướng chức năng. Thư viện của thủ tục Map() và Reduce() sẽ được viết bằng nhiều loại ngôn ngữ khác nhau. Thủ tục được cài đặt miễn phí và được sử dụng phổ biến nhất là là Apache Hadoop.</p>

#### *II. Mô hình MapReduce*

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; MapReduce có 2 hàm chính là Map() và Reduce(), đây là 2 hàm đã được định nghĩa bởi người dùng và nó cũng chính là 2 giai đoạn liên tiếp trong quá trình xử lý dữ liệu của MapReduce.</p>

<ul align="justify">
  <li><b>Hàm Map():</b>  có nhiệm vụ nhận Input cho các cặp giá trị/khóa và output chính là tập những cặp giá trị/khóa trung gian. Sau đó, chỉ cần ghi xuống đĩa cứng và tiến hành thông báo cho các hàm Reduce() để trực tiếp nhận dữ liệu. </li>
  <li><b>Hàm Reduce():</b> có nhiệm vụ tiếp nhận từ khóa trung gian và những giá trị tương ứng với lượng từ khóa đó. Sau đó, tiến hành ghép chúng lại để có thể tạo thành một tập khóa khác nhau. Các cặp khóa/giá trị này thường sẽ thông qua một con trỏ vị trí để đưa vào các hàm reduce. Quá trình này sẽ giúp cho lập trình viên quản lý dễ dàng hơn một lượng danh sách cũng như  phân bổ giá trị sao cho  phù hợp nhất với bộ nhớ hệ thống. </li>
  <li><b>Shuffle:</b> là bước  trung gian ở giữa Map và Reduce. Sau khi Map hoàn thành  xong công việc của mình thì Shuffle sẽ làm nhiệm vụ chính là thu thập cũng như tổng hợp từ khóa/giá trị trung gian đã được map sinh ra trước đó rồi chuyển qua cho Reduce tiếp tục xử lý.</li>
</ul>

#### *III. Lợi ích nổi bật mà MapReduce mang lại*
<p align="center"> <img src ="https://user-images.githubusercontent.com/77878466/105630140-d6a31d80-5e79-11eb-9385-54a0a2dabf73.png" width="70%"/>
<p align="center"> <em>Quá trình xử lý bài toán wordcount bằng MapReduce</em> </p>

<ul align="justify">
  <li>Xử lý dễ dàng mọi bài toán có lượng dữ liệu lớn nhờ khả năng tác vụ phân tích và tính toán phức tạp. Nó có thể xử lý nhanh chóng cho ra kết quả dễ dàng chỉ trong khoảng thời gian ngắn.</li>
  <li>Chạy song song trên các máy có sự phân tán  khác nhau. Với khả năng hoạt động độc lập kết hợp  phân tán, xử lý các lỗi kỹ thuật để mang lại nhiều hiệu quả cho toàn hệ thống. </li>
  <li>Thực hiện trên nhiều nguồn ngôn ngữ lập trình khác nhau như: Java, C/ C++, Python, Perl, Ruby,… tương ứng với nó là những thư viện hỗ trợ. </li>
  <li>Mã độc trên internet ngày càng nhiều hơn nên việc xử lý những đoạn mã độc này cũng trở nên rất phức tạp và tốn kém nhiều thời gian. Chính vì vậy, các ứng dụng MapReduce dần hướng đến quan tâm nhiều hơn cho việc phát hiện các mã độc để có thể xử lý chúng. Nhờ vậy, hệ thống mới có thể vận hành trơn tru và được bảo mật nhất.</li>
</ul>

#### *IV. Quá trình MapReduce hoạt động*
##### *1. Nguyên lý hoạt động*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Mapreduce hoạt động dựa vào nguyên tắc chính là “Chia để trị”, cụ thể như sau:</p>

<ul align="justify">
  <li>Phân chia các dữ liệu cần xử lý thành nhiều phần nhỏ trước khi thực hiện. </li>
  <li>Xử lý các vấn đề nhỏ theo phương thức song song trên các máy tính rồi phân tán hoạt động theo hướng độc lập.</li>
  <li>Tiến hành tổng hợp những kết quả thu được để đề ra được kết quả sau cùng. </li>
</ul>

##### *2. Các bước hoạt động*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Để xử lý một quá trình, thông thường mô hình MapReduce sẽ trải qua 5 bước sau:</p>

<ul align="justify">
  <li><em>Bước 1</em>: Tiến hành chuẩn bị các dữ liệu đầu vào để cho Map() có thể xử lý.</li>
  <li><em>Bước 2</em>: Lập trình viên thực thi các mã Map() để xử  lý. </li>
  <li><em>Bước 3</em>: Tiến hành trộn lẫn các dữ liệu được xuất ra bởi Map() vào trong Reduce Processor</li>
  <li><em>Bước 4</em>: Tiến hành thực thi tiếp mã Reduce() để có thể xử lý tiếp các dữ liệu cần thiết.  </li>
  <li><em>Bước 5</em>: Thực hiện tạo các dữ liệu xuất ra cuối cùng. </li>
</ul>

##### *3. Luồng dữ liệu nền tảng*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Gồm có: Input Reader, Map Function, Partition Function, Compare Function, Reduce Function và Output Writer</p>

## Phần 2: Bài toán đếm tần suất xuất hiện của từ có trong file - Word Counting
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; <b>Đề tài:</b> Dùng Spark đọc vào một file văn bản và đếm số từ trên bản, lọc ra k từ có tần suất xuất hiện nhiều nhất.</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Bài làm sẽ được thực hiện trên colab với các dữ liệu trong file .txt tự tạo</p>

&nbsp;&nbsp;&nbsp;&nbsp; [Bài làm được thực hiện ở đây](https://colab.research.google.com/drive/1xa46qtEUoeL6LtzKhvk_QebFgZkEI8yK?usp=sharing)

## Phần 3: Tài liệu tham khảo
&nbsp;&nbsp;&nbsp;&nbsp; 1.	Learning Spark by Matei Zaharia, Patrick Wendell, Andy Konwinski, Holden Karau

&nbsp;&nbsp;&nbsp;&nbsp; 2.	https://www.tutorialspoint.com/apache_spark/apache_spark_introduction.htm

&nbsp;&nbsp;&nbsp;&nbsp; 3.	https://spark.apache.org/

&nbsp;&nbsp;&nbsp;&nbsp; 4.	https://www.mastercode.vn/blog/web-development/apache-spark-la-gi.85

&nbsp;&nbsp;&nbsp;&nbsp; 5.	http://itechseeker.com/

&nbsp;&nbsp;&nbsp;&nbsp; 6. Jeffrey Dean, Sanjay Ghemawat. Mapreduce : Simplified Data Processing on Large Clusters. In OSDI, 2004
