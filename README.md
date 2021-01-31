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
  
## Phần 3: Tài liệu tham khảo
&nbsp;&nbsp;&nbsp;&nbsp; 1.	https://spark.apache.org/docs/latest/configuration.html

&nbsp;&nbsp;&nbsp;&nbsp; 2.	https://docs.cloudera.com/runtime/7.2.6/running-spark-applications/topics/spark-configure-properties-spark-defaults-conf.html

&nbsp;&nbsp;&nbsp;&nbsp; 3.	https://sparkbyexamples.com/pyspark-tutorial/

&nbsp;&nbsp;&nbsp;&nbsp; 4.	http://itechseeker.com/tutorials/apache-spark/lap-trinh-spark-voi-scala/spark-sql-dataset-va-dataframes/

&nbsp;&nbsp;&nbsp;&nbsp; 5.	https://dzone.com/articles/pyspark-dataframe-tutorial-introduction-to-datafra

&nbsp;&nbsp;&nbsp;&nbsp; 6.	https://www.tutorialspoint.com/pyspark/pyspark_rdd.htm
