# Tìm hiểu về SPARK PROPERTIES, SPARK RDD VÀ SPARK DATAFRAME

## Phần 1: Tìm hiểu về Spark Properties
### *I. Đôi nét về Spark Properties*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Thuộc tính Spark – Spark Properties kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được cài đặt trực tiếp trên SparkConf được chuyển đến SparkContext của bạn. SparkConf cho phép định cấu hình một số thuộc tính chung (<i>ví dụ:</i> URL chính và tên ứng dụng), cũng như các cặp key-value thông qua phương thức set().

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; <b>Ví dụ:</b> Khởi tạo một ứng dụng với 2 luồng:
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106387193-3ade5800-640b-11eb-8a58-2ae06da3b29b.JPG"width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Trong đó, <i>local[2]</i> cho biết tối thiểu có 2 luồng đang chạy song song, giúp phát hiện lỗi chỉ tồn tại khi chạy trong bối cảnh phân tán.
</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Các thuộc tính chỉ định một số khoảng thời gian với một đơn vị thời gian. Các định dạng sau được Spark chấp nhận:
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106387420-2d759d80-640c-11eb-8a57-3fb4b1855699.JPG"width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Các định dạng thuộc tính kích thước byte có trong Spark”
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106387429-3f574080-640c-11eb-83e2-e618851af5d8.JPG"width="50%"/>


### *II. Tải động với Spark Properties (Dynamically loading Spark Properties)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Trong một sô trường hợp, ta có thể tránh việc thiết lập cứng cho các cấu hình mặc định trong một SparkConf.
</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;<b>Ví dụ:</b>Nếu muốn chạy cùng một ứng dụng với các bản gốc khác nhau hoặc số lượng bộ nhớ khác nhau thì chỉ cần dùng <i>SparkConf()</i> mà Spark cung cấp, cho phép tạo một SparkConf trống.
</p>
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106387576-ef2cae00-640c-11eb-8eaa-a207dbab3291.JPG" width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Sau đó, chỉ việc cung cấp các giá trị cấu hình trong lúc chạy Spark:
</p>
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106387567-eb992700-640c-11eb-8f11-e9a7aea9ab6d.JPG" width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Trong đó, công <i>spark-submit</i> cụ và trình bao Spark hỗ trợ hai cách để tải cấu hình động. Đầu tiên là các tùy chọn dòng lệnh, chẳng hạn như <i>--master</i>, như được hiển thị ở trên. spark-submit có thể chấp nhận bất kỳ thuộc tính Spark nào bằng cách sử dụng <i>--conf/-c</i> cờ, nhưng sử dụng cờ đặc biệt cho các thuộc tính đóng một vai trò trong việc khởi chạy ứng dụng Spark. Đang chạy <i>./bin/spark-submit –help</i> sẽ hiển thị toàn bộ danh sách các tùy chọn này.


### *III. Các thuộc tính của Spark*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Các thuộc tính của Spark chủ yếu được chia thành hai loại:
</p>
<ul align="justify">
  <li><em><i>Liên quan đến triển khai:</i></em> <b>spark.driver.memory</b>, <b>spark.executor.instances</b>. Loại thuộc tính này có thể không bị ảnh hưởng khi thiết lập theo chương trình <b>SparkConf</b> trong thời gian chạy hoặc hành vi tùy thuộc vào trình quản lý cụm và chế độ triển khai đã chọn trước. Do đó nên đặt thông qua file cấu trúc hoặc tùy chọn dòng lệnh <b>spark-submit</b>.</li>
  <li><em><i>Liên quan đến kiểm soát thời gian chạy Spark:</i></em><b> spark.task.maxFailures</b>.</li>
</ul>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Apache Spark cung cấp môt bộ giao diện người dùng trẻn website: <i>http://localhost:4040</i> (Job, Stages, Tasks, Strorage, Environment, Executors và SQL). Để có thể xem các thược tính của Spark, mọi người vào thẻ Environment. Ngoài ra, có thể xác định giá trị mặc định thông qua <i>spark-defaults.conf</i>. Các thuộc tính mặc định có sẵn trong Spark đều có giá trị mặc định hợp lý.
</p>

#### *1. Một vài thuộc tính ứng dụng - Application Properties*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106388128-a62a2900-640f-11eb-8129-f0aa20113ab6.JPG" width="50%"/>
  
#### *2. Một vài thuộc tính xáo trộn - Shuffle Behavior*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106388129-a75b5600-640f-11eb-9145-80950465c940.JPG" width="50%"/>
  
#### *3. Giao diện người dùng Spark - Spark UI*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106388131-a7f3ec80-640f-11eb-8024-106d198c3bf3.JPG" width="50%"/>

#### *4. Nén và tuần tự hóa (Compression and Serialization)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;spark.rdd.compress - Có nén các phân vùng tuần tự</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;<b>Ví dụ:</b> StorageLevel.MEMORY_ONLY_SERtrong Java và Scala hoặc StorageLevel.MEMORY_ONLY trong Python). Có thể tiết kiệm không gian đáng kể với chi phí tăng thêm thời gian CPU. Nén sẽ sử dụng tới thuộc tính spark.io.compression.codec. Ngoài ra còn có:</p>
<ul align="justify">
  <li><em>spark.serializer</em></li>
  <li><em>spark.serializer.objectStreamReset</em></li>
  <li><em>spark.kryoserializer.buffer</em></li>
  <li><em>spark.kryo.registrator</em></li>
  <li><em>spark.kryo.referenceTracking, ...</em></li>
</ul>

### *IV. Các thuộc tính khác*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Ngoài các loại thuộc tính trên Spark còn hỗ trợ nhiều loại thuộc tính khác nhau:</p>
<ul align="justify">
  <li><em>Môi trường thực thi (Runtime Environment)</em></li>
  <li><em>Quản lý bộ nhớ (Memory Management)</em></li>
  <li><em>Hành vi thực thi (Execution Behavior)</em></li>
  <li><em>Chỉ số thực thi (Executor Metrics)</em></li>
  <li><em>Kết nối mạng (Networking)</em></li>
  <li><em>Lập lịch (Scheduling)</em></li>
  <li><em>Chế độ thực thi rào cản (Barrier Execution Mode)</em></li>
  <li><em>Phân bố động (Dynamic Allocation)</em></li>
  <li><em>Cấu hình Thread (Thread Configurations)</em></li>
  <li><em>Bảo mật (Security)</em></li>
</ul>

## Phần 2: Tìm hiểu về Spark RDD
### *I. Tổng quát về Resilient Distributed Datasets – RDD*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;RDD (Resilient Distributed Datasets) được định nghĩa trong Spark Core. Nó đại diện cho một collection các item đã được phân tán trên các cluster, và có thể xử lý phân tán. PySpark sử dụng PySpark RDDs và nó chỉ là 1 object của Python nên khi bạn viết code RDD transformations trên Java thực ra khi run, những transformations đó được ánh xạ lên object PythonRDD trên Java.</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Bên cạnh đó, RDD còn được hiểu là cấu trúc dữ liệu nền tảng của Spark, được sử dụng để phát triển Spark từ khi dự án này mới được ra đời. Resilient ở đây có thể hiểu là khả năng khôi phục dữ liệu khi dữ liệu xảy ra lỗi hoặc bị mất dữ liệu trong quá trình sử dụng. Distributed có nghĩa là các phần tử và các đối tượng (objects) trong Spark là không thể thay đổi (immutable) và được phân tán ra nhiều nodes khác nhau trong một cluster. Chính thuộc tính này của RDD cho phép Spark có thể thực hiện các thuật toán và tiến hành xử lý một cách song song, qua đó giúp tăng tốc độ và hiệu suất của hệ thống.</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;RDDs có thể chứa bất kỳ kiểu dữ liệu nào của Python, Java, hoặc đối tượng Scala, bao gồm các kiểu dữ liệu do người dùng định nghĩa. Thông thường, RDD chỉ cho phép đọc, phân mục tập hợp của các bản ghi. RDDs có thể được tạo ra qua điều khiển xác định trên dữ liệu trong bộ nhớ hoặc RDDs, RDD là một tập hợp có khả năng chịu lỗi mỗi thành phần có thể được tính toán song song.</p>

### *II.	Các đặc điểm của Spark RDD*
#### *1. Tính toán trong bộ nhớ*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Spark RDD cung cấp khả năng tính toán trong bộ nhớ. Nó lưu trữ các kết quả trung gian trong bộ nhớ phân tán (RAM) thay vì lưu trữ ổn định (đĩa).</p>

#### *2. Lazy Evaluations*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Tất cả các phép biến đổi trong Apache Spark đều được gọi là lười biếng (lazy), ở chỗ chúng không tính toán ngay kết quả của chúng. Thay vào đó, nó chỉ nhớ các phép biến đổi được áp dụng cho một số tập dữ liệu cơ sở.
</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Spark tính toán các phép biến đổi khi một hành động yêu cầu kết quả cho driver của chương trình.
</p>

#### *3. Khả năng chịu lỗi*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;RDD có khả năng chịu lỗi vì chúng theo dõi thông tin dòng dữ liệu để tự động xây dựng lại dữ liệu bị mất khi bị lỗi. Nó xây dựng lại dữ liệu bị mất khi lỗi bằng cách sử dụng dòng (lineage), mỗi RDD nhớ cách nó được tạo ra từ các tập dữ liệu khác (bằng các phép biến đổi như map, join hoặc GroupBy) để tạo lại chính nó.</p>

#### *4. Tính bất biến*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Dữ liệu an toàn để chia sẻ trên các process. Ngoài ra, nó cũng có thể được tạo hoặc truy xuất bất cứ lúc nào giúp dễ dàng lưu vào bộ nhớ đệm, chia sẻ và nhân rộng. Vì vậy, chúng ta có thể sử dụng nó để đạt được sự thống nhất trong tính toán.</p>

#### *5. Phân vùng*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Phân vùng là đơn vị cơ bản của tính song song trong Spark RDD. Mỗi phân vùng là một phân chia dữ liệu hợp lý mà có thể thay đổi được. Ta có thể tạo một phân vùng thông qua một số biến đổi trên các phân vùng hiện có</p>

#### *6. Sự bền bỉ (Persistence)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Người dùng có thể cho biết họ sẽ sử dụng lại những RDD nào và chọn hướng lưu trữ cho họ (ví dụ: lưu trữ trong bộ nhớ hoặc trên Đĩa).</p>

#### *7. Hoạt động chi tiết thô (Coarse-grained Operations)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Nó áp dụng cho tất cả các phần tử trong bộ dữ liệu thông qua map hoặc fiter hoặc group theo hoạt động.</p>

#### *8. Vị trí – độ dính (Location – Stickiness)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;RDD có khả năng xác định ưu tiên vị trí để tính toán các phân vùng. Tùy chọn vị trí đề cập đến thông tin về vị trí của RDD. DAGScheduler đặt các phân vùng theo cách sao cho tác vụ gần với dữ liệu nhất có thể. Do đó, tốc độ tính toán có thể tăng.</p>

### *III.	Các hoạt động và cách áp dụng các hoạt động trên RDD*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; RDD trong Apache Spark hỗ trợ hai loại hoạt động: </p>
<ul align="justify">
  <li>Transformation</li>
  <li>Actions</li>
</ul>

#### *1.	Transformation*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Spark RDD Transformations là các hàm sử dụng một RDD làm đầu vào và tạo ra một hoặc nhiều RDD làm đầu ra. Chúng ta không thay đổi RDD đầu vào (vì RDD là bất biến và do đó người ta không thể thay đổi nó), nhưng luôn tạo ra một hoặc nhiều RDD mới bằng cách áp dụng các tính toán mà nó đại diện.</p>

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Các phép biến đổi là các hoạt động lười biếng trên RDD trong Apache Spark. Nó tạo ra một hoặc nhiều RDD mới, thực thi khi một Action xảy ra. Do đó, Transformation tạo ra một tập dữ liệu mới từ tập dữ liệu hiện có.</p>

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Một số phép biến đổi nhất định có thể được pipelined, đây là một phương pháp tối ưu hóa mà Spark sử dụng để cải thiện hiệu suất của các phép tính. Có hai loại phép biến hình: phép biến hình hẹp (narrow transformation), phép biến hình rộng(wide transformation).</p>

<ul align="justify">
  <li>
    <em>Narrow Transfoemation</em>
    <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384100-0020f380-63fc-11eb-8aaf-46334b3cc225.png" width="70%"/></p>
    <p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Đây là kết quả của ánh xạ, bộ lọc và sao cho dữ liệu chỉ từ một phân vùng duy nhất, tức là nó tự cung cấp. Một RDD đầu ra có các phân vùng với các bản ghi bắt nguồn từ một phân vùng duy nhất trong RDD mẹ. Chỉ một tập hợp con giới hạn của các phân vùng được sử dụng để tính toán kết quả.</p>
    <p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Spark nhóm các phép biến hình thu hẹp dưới dạng một giai đoạn được gọi là pipelining.</p>
  </li>
  <li><em>Wide Transformation</em>
  <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384257-6dcd1f80-63fc-11eb-998b-d65486a5ce8f.png" width="70%"/></p>
    <p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Là kết quả của các hàm như groupByKey() và ReduceByKey(). Dữ liệu cần thiết để tính các bản ghi trong một phân vùng có thể nằm trong nhiều phân vùng của RDD mẹ. Các phép biến đổi rộng còn được gọi là phép biến đổi trộn (shuffle transformations) vì chúng có thể có hoặc không phụ thuộc vào một lần trộn.</p>
  </li>
</ul>

 <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384436-69edcd00-63fd-11eb-89c6-ee6991049dee.PNG" width="90%"/></p>
 <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384439-6eb28100-63fd-11eb-9f6d-9aaebe5d8435.PNG" width="90%"/></p>
 <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384441-7114db00-63fd-11eb-9c77-38dadae2775e.PNG" width="90%"/></p>
 <p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384444-74a86200-63fd-11eb-99ff-7f762fd71bdc.PNG" width="90%"/></p>
 
#### *2.	Action*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Action trong Spark trả về kết quả cuối cùng của các tính toán RDD. Nó kích hoạt thực thi bằng cách sử dụng đồ thị dòng để tải dữ liệu vào RDD ban đầu, thực hiện tất cả các phép biến đổi trung gian và trả về kết quả cuối cùng cho chương trình Driver hoặc ghi nó ra hệ thống tệp. Đồ thị tuyến tính là đồ thị phụ thuộc của tất cả các RDD song song của RDD.</p>

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Các Actions là các hoạt động RDD tạo ra các giá trị không phải RDD. Chúng hiện thực hóa một giá trị trong chương trình Spark. Actions là một trong những cách để gửi kết quả từ người thực thi đến driver. First(), take(), Reduce(), collect(), count() là một số Action trong Spark.</p>

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Sử dụng các phép biến đổi (Transformations), người ta có thể tạo RDD từ biến hiện có. Nhưng khi chúng ta muốn làm việc với tập dữ liệu thực tế, tại thời điểm đó chúng ta sử dụng Action. Khi Hành động xảy ra, nó không tạo ra RDD mới, không giống như sự chuyển đổi. Do đó, Actions là các hoạt động RDD không cung cấp giá trị RDD. Actions lưu trữ giá trị của nó đối với driver hoặc hệ thống lưu trữ bên ngoài. Nó đưa sự lười biếng (lazy) của RDD vào chuyển động.</p>

<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384649-89392a00-63fe-11eb-83f7-7fe96941eb2d.PNG" width="90%"/></p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106384654-8e967480-63fe-11eb-97c9-4947eb7272a0.PNG" width="90%"/></p>

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; <b><em>Lưu ý</em></b>: việc sửa đổi các biến khác với Accumulators bên ngoài foreach () có thể dẫn đến hành vi không xác định. Xem phần Tìm hiểu về việc đóng cửa để biết thêm chi tiết.</p>

### *IV.	Một số code minh họa các hoạt động*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Để áp dụng bất kỳ thao tác nào trong PySpark, trước tiên chúng ta cần tạo một PySpark RDD . Khối mã sau có chi tiết về Lớp RDD của PySpark:</p>

```python
      class pyspark.RDD (
         jrdd, 
         ctx, 
         jrdd_deserializer = AutoBatchedSerializer(PickleSerializer())
      )
```

<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Cách chạy một vài thao tác cơ bản bằng PySpark. Đoạn mã sau trong tệp Python tạo ra các từ RDD, lưu trữ một tập hợp các từ được đề cập.</p>

```python
      words = sc.parallelize (
         ["scala", 
         "java", 
         "hadoop", 
         "spark", 
         "akka",
         "spark vs hadoop", 
         "pyspark",
         "pyspark and spark"]
      )
```

#### *1.	Count()*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Hàm count() cho biết số phần tử có trong RDD</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385220-b9ce9300-6401-11eb-8dcf-1b7df587ecc1.png" width="70%"/></p>

#### *2.	Collect()*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Trả về tất cả các phần tử ở trong RDD</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385223-bdfab080-6401-11eb-97d4-fceac9879758.png" width="80%"/></p>

#### *3.	foreach(f)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Chỉ trả về những phần tử đáp ứng điều kiện của hàm bên trong foreach. Trong ví dụ sau, chúng tôi gọi một hàm in trong foreach, hàm này in tất cả các phần tử trong RDD</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385225-c0f5a100-6401-11eb-86dc-bc6f1ad13a15.png" width="70%"/></p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385226-c357fb00-6401-11eb-9a65-1eb810ddf73a.png" width="70%"/></p>

#### *4.	filler(f)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Một RDD mới được trả về chứa các phần tử, đáp ứng chức năng bên trong bộ lọc. Trong ví dụ sau, chúng tôi lọc ra các chuỗi chứa "spark".</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385396-bee01200-6402-11eb-8c3d-8e355424f42d.png" width="70%"/></p>

#### *5.	map(f, securePartitioning = False)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Một RDD mới được trả về bằng cách áp dụng một hàm cho mỗi phần tử trong RDD. Trong ví dụ sau, chúng tôi tạo một cặp giá trị khóa và ánh xạ mọi chuỗi với giá trị 1.</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385399-c1db0280-6402-11eb-8449-a79567483a47.png" width="90%"/></p>

#### *6.	reduce(f)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Sau khi thực hiện thao tác nhị phân giao hoán và kết hợp được chỉ định, phần tử trong RDD được trả về. Trong ví dụ sau, chúng tôi đang nhập gói thêm từ toán tử và áp dụng nó trên 'num' để thực hiện một thao tác thêm đơn giản.</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385402-c43d5c80-6402-11eb-9d68-2bf977e5fe21.png" width="70%"/></p>


#### *7.	join(other, numPartitions = none)*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Trả về RDD với một cặp phần tử với các khóa phù hợp và tất cả các giá trị cho khóa cụ thể đó. Trong ví dụ sau, có hai cặp phần tử trong hai RDD khác nhau. Sau khi kết hợp hai RDD này, chúng ta nhận được một RDD với các phần tử có khóa phù hợp và giá trị của chúng.</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385407-c7384d00-6402-11eb-8a96-c9e2fc558ed1.png" width="70%"/></p>


#### *8.	cache()*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; Duy trì RDD này với mức lưu trữ mặc định (MEMORY_ONLY). Bạn cũng có thể kiểm tra xem RDD có được lưu vào bộ nhớ đệm hay không.</p>
<p align="center"><img src ="https://user-images.githubusercontent.com/77878466/106385426-d3bca580-6402-11eb-96b7-4ed16c58d7c3.png" width="70%"/></p>

## Phần 3: Tìm hiểu về Spark DataFrame
### *I. Tổng quát về Spark DataFrame*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106388918-2bfba380-6413-11eb-9933-48c3bd73df3b.jpg"width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp; DataFrame là một API bậc cao hơn RDD được Spark giới thiệu vào năm 2013 (từ Apache Spark 1.3). Tương tự như RDD, dữ liệu trong DataFrame cũng được quản lý theo kiểu phân tán và không thể thay đổi (immutable distributed). Tuy nhiên dữ liệu này được sắp sếp theo các cột, tương tự như trong Relation Database. DataFrame được phát triển để giúp người dùng có thể dễ dàng thực hiện các thao tác xử lý dữ liệu cũng như làm tăng đáng kể hiệu quả sử lý của hệ thống.

### *II.	Lợi ích mà DataFrame mang lại*
#### *1. Xử lý dữ liệu có cấu trúc và bán cấu trúc*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;DataFrames được thiết kế để xử lý một tập hợp lớn dữ liệu có cấu trúc cũng như bán cấu trúc. Các quan sát trong Spark DataFrame được tổ chức dưới các cột được đặt tên, giúp Apache Spark hiểu được lược đồ của Dataframe. Điều này giúp Spark tối ưu hóa kế hoạch thực thi trên các truy vấn này. Nó cũng có thể xử lý hàng petabyte dữ liệu.</p>

#### *2. Slicing và Dicing*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;API DataFrames thường hỗ trợ các phương pháp phức tạp để cắt và phân loại dữ liệu. Nó bao gồm các hoạt động như "selecting" hàng, cột và ô theo tên hoặc theo số, lọc ra các hàng, v.v. Dữ liệu thống kê thường rất lộn xộn và chứa nhiều giá trị bị thiếu và không chính xác cũng như vi phạm phạm vi. Vì vậy, một tính năng cực kỳ quan trọng của DataFrames là quản lý rõ ràng dữ liệu bị thiếu.</p>

#### *3. Hỗ trợ nhiều ngôn ngữ*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Hỗ trợ API cho các ngôn ngữ khác nhau như Python, R, Scala, Java, giúp những người có nền tảng lập trình khác nhau sử dụng dễ dàng hơn.</p>

#### *4. Nguồn dữ liệu*
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;DataFrames có hỗ trợ cho nhiều định dạng và nguồn dữ liệu, chúng ta sẽ xem xét vấn đề này sau trong hướng dẫn Pyspark DataFrames này. Họ có thể lấy dữ liệu từ nhiều nguồn khác nhau.</p>

### *III.	Các tính năng của DataFrame và nguồn dữ liệu PySpark*
#### *1. Các tính năng*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106389070-04590b00-6414-11eb-8f54-35b0267ed50d.jpg"width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;DataFrame được phân phối trong tự nhiên, làm cho nó trở thành một cấu trúc dữ liệu có khả năng chịu lỗi và có tính khả dụng cao.</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Đánh giá lười biếng là một chiến lược đánh giá giữ việc đánh giá một biểu thức cho đến khi giá trị của nó là cần thiết. Nó tránh đánh giá lặp lại. Đánh giá lười biếng trong Spark có nghĩa là quá trình thực thi sẽ không bắt đầu cho đến khi một hành động được kích hoạt. Trong Spark, bức tranh về sự lười biếng xuất hiện khi các phép biến đổi Spark xảy ra.</p>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;DataFrame là bất biến trong tự nhiên. Bởi bất biến, ý tôi là nó là một đối tượng có trạng thái không thể sửa đổi sau khi nó được tạo. Nhưng chúng ta có thể biến đổi các giá trị của nó bằng cách áp dụng một phép biến đổi nhất định, như trong RDD.</p>


#### *2. Nguồn dữ liệu PySpark*
<p align="center"> <img src ="https://user-images.githubusercontent.com/74041962/106389071-058a3800-6414-11eb-9030-89b9b20b34f9.jpg"width="50%"/>
<p align="justify"> &nbsp;&nbsp;&nbsp;&nbsp;Dữ liệu có thể được tải vào thông qua tệp CSV, JSON, XML hoặc tệp Parquet. Nó cũng có thể được tạo bằng cách sử dụng RDD hiện có và thông qua bất kỳ cơ sở dữ liệu nào khác, như Hive hoặc Cassandra. Nó cũng có thể lấy dữ liệu từ HDFS hoặc hệ thống tệp cục bộ.</p>


## Tài liệu tham khảo
&nbsp;&nbsp;&nbsp;&nbsp; 1.	https://spark.apache.org/docs/latest/configuration.html

&nbsp;&nbsp;&nbsp;&nbsp; 2.	https://docs.cloudera.com/runtime/7.2.6/running-spark-applications/topics/spark-configure-properties-spark-defaults-conf.html

&nbsp;&nbsp;&nbsp;&nbsp; 3.	https://sparkbyexamples.com/pyspark-tutorial/

&nbsp;&nbsp;&nbsp;&nbsp; 4.	http://itechseeker.com/tutorials/apache-spark/lap-trinh-spark-voi-scala/spark-sql-dataset-va-dataframes/

&nbsp;&nbsp;&nbsp;&nbsp; 5.	https://dzone.com/articles/pyspark-dataframe-tutorial-introduction-to-datafra

&nbsp;&nbsp;&nbsp;&nbsp; 6.	https://www.tutorialspoint.com/pyspark/pyspark_rdd.htm
