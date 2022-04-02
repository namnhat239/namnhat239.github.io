---
layout: post
title:  Explore data roles and services
date:   2022-03-30
image:  explore-roles-responsibilities-world-of-data.svg
tags:   Azure Data-Analysis
---

* TOC
{:toc}

# Note

Bài dịch tiếp theo trong chuỗi tài liệu tìm hiểu về Data của Microsoft. Link: https://docs.microsoft.com/en-us/learn/modules/explore-roles-responsibilities-world-of-data/

# Giới thiệu

Các chuyên gia data đảm nhận các vai trò riêng biệt trong việc xây dựng và quản lý các giải pháp phần mềm, và đồng thời làm việc với nhiều công nghệ và dịch vụ để làm việc đó.

Mục tiêu của tài liệu gồm:
- Xác định các vai trò nghiệp vụ dữ liệu phổ biến.

- Xác định các dịch vụ cloud được dùng bởi các chuyên gia data.

# Chương I: Khám phá các vai trò công việc trong thế giới data

Có rất nhiều vai trò liên quan đến việc quản lý, kiểm soát và sử dụng dữ liệu. Một vài vai trò thì theo định hướng kinh doanh, một số khác thì thiên về kỹ thuật nhiều hơn, một số lại tập trung vào việc nghiên cứu, một số lại là sự kết hợp của các khía cạnh khác nhau của việc quản lý dữ liệu. Tổ chức của bạn có thể định nghĩa ra nhiều vai trò khác nhau, hoặc cho chúng những cái tên khác nhau, truy nhiên,  những vai trò được mô tả trong phần này sẽ bao gồm các sự phân chia nhiêm vụ và trách nhiệm phổ biến nhất thường thấy.

Ba vai trò chính trong công việc liên quan đến dữ liệu trong hầu hết các tỏ chức gồm có:

- Database administrators: quản lý CSDL, cấp quyền cho người dùng, lưu trữ các bản sao backup và khôi phục khi có sự cố.

- Data engineers: quản lý cơ sở hạ tầng và các quy trình tích hợp dữ liệu trong tổ chức, áp dụng các quy trình làm sạch dữ liệu, xác định các quy tắc quản trị dữ liệu, triển khai các đường truyền luân chuyễn dữ liệu giữa các hệ thống(pipelines)

- Data analysts: khám phá và phân tích dữ liệu để trực quan hoá và các biểu đồ cho phép tổ chức đưa ra viết định sáng suốt.

**Note**

Vai trò công việc được phân loại khác nhau dựa trên nhiệm vụ và trách nhiệm. Trong một vài tổ chức, một cá nhân vẫn có thể thực hiện nhiều vai trò, vì vậy trong vai trò là một database administrator họ vẫn có thể cung cấp CSDL giao dịch và sau đó với vai trò là một engineer, họ có thể tạo một pipeline để chuyển dữ liệu từ CSDL đến data warehouse để xử lý.

## 1.Database Administrator

Một database administrator đảm nhận vai trò cho việc thiết kế, triển khai, bảo trì và các khía cạnh hoạt động của hệ thống CSDL on-premises và cloud. Họ chịu trách nhiệm về tính khả dụng tổng thể cũng như hiệu suất nhất quán và tối ưu CSDL. Họ làm việc với các bên liên quan để thực hiện các chính sách, công cụ, và xử lý các kế hoạch backup và khôi phục sau các thảm hoạ tự nhiên hay lỗi do con người gây ra.

Database administrator cũng chịu trách nhiệm cho việc quản lý tính bảo mật của dữ liệu trong CSDL, cấp các đặc quyền cho dữ liệu, cho phép hay từ chối truy cập của người dùng thích hợp.

## 2.Data Engineer

Một data engineer sẽ phối hợp với các bên liên quan để thiết kế và triển khai các công việc liên quan đến dữ liệu, bao gồm các đường truyền, làm sạch và ác hoạt động chuyển đổi, cũng như lưu trữ dữ liệu cho các luồng việc phân tích. Họ sử dụng một loạt các nền tảng công nghệ, bao gồm CSDL quan hệ và phi quan hệ, lưu trữ files và luồng dữ liệu.

Họ cũng chịu trách nhiệm đảm bảo quyền riêng tư của dữ liệu được duy trì trên cloud và on-premises đến các kho lưu trữ đám mây. Họ đảm nhận việc quản lý và giám sát các pipelines để đảm bảo rằng dữ liệu được tải đi như mong đợi.

Data Analyst

Một Data Analyst cho phép các doanh nghiệp tối đa hóa giá trị của tài sản dữ liệu của họ. Họ chịu trách nhiệm khám phá dữ liệu để xác định xu hướng và mối quan hệ, thiết kế và xây dựng các mô hình phân tích, đồng thời kích hoạt khả năng phân tích nâng cao thông qua các báo cáo và hình ảnh hóa.

Một Data analyst sẽ xử lý dữ liệu thô thành các thông tin thích hợp dữ trên các yêu cầu kinh doanh đã được xác định để cung cấp các thông tin phù hợp.

**Note**
Các vai trò được mô tả ở đây có thể xem là các vai trò chính thường được thấy trong các doanh nghiệp vừa và lớn. Bên cạnh đó, còn có nhiều vai trò liên quan đến dữ liệu không được đề cập đến như data scientist và data architect, và còn nhiều nhiều ngành nghề công nghệ liên quan đến lĩnh việc dữ liệu, bao gồm các nhà phát triển ứng dụng dev và kỹ sư phần mềm.

# Chương II. Các dịch vụ dữ liệu

Microsoft Azure là một nền tảng đám mây cung cấp các ứng dụng và cơ sở hạ tầng CNTT cho một số tổ chức lớn nhất thế giới. Nó bao gồm nhiều dịch vụ giải pháp đám mây, bao gồm các công việc chuyển giao dữ liệu và phân tích chúng.

Một vài dịch vụ đám mây phổ biến dùng cho dữ liệu được mô tả dưới đây:

## 1.Azure SQL

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-sql.png)

Azure SQL là tên chung của một nhóm các giải pháp CSDL quan hệ dữ trên engine CSDL MSSQL. Azure SQL bao gồm:

- CSDL Azure SQL: Một CSDL dạng platform-as-a-service (PaaS) được quản lý bởi Azure.

- Azure SQL Managed Instance: Một phiên bản của SQL Server được duy trì tự động, cho phép cấu hình linh hoạt hơn Azure SQL DB nhưng  có nhiều trách nhiệm quản trị hơn cho chủ sở hữu.

- Azure SQL VM: Một máy ảo cài đặt SQL Server, cho phép cấu hình tối đa với toàn bộ trách nhiệm quản lý.

Các Database administrators thường sẽ cung cấp và quản lý hệ thống CSDL Azure SQL để hỗ trợ các ứng dụng dòng doanh nghiệp (LOB) cần lưu trữ dữ liệu giao dịch.

Các Data engineers có thể sử dụng hệ thống cơ sở dữ liệu Azure SQL làm nguồn vào cho các đường truyền dữ liệu thực hiện các hoạt động trích xuất, chuyển đổi và tải (ETL) để nhập dữ liệu giao dịch vào một hệ thống phân tích.

Các data analysts có thể truy vấn CSDL Azure SQL trực tiếp để tạo các báo cáo, mặc dù trong các tổ chức lớn, dữ liệu thường được kết hợp với dữ liệu từ các nguồn khác trong kho dữ liệu phân tích để hỗ trợ phân tích doanh nghiệp.

## 2.Azure Database for open-source relational databases

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-database.png)

Azure bao gồm các dịch vụ quản lý cho các hệ thống CSDL quan hệ mã nguồn mở, bao gồm:

- Azure Database for MySQL - Một hệ thống quản trị CSDL mã nguồn mở đơn giản thường dùng trong Linux, Apche, MySQL and PHP (LAMP)

- Azure Database for MariaDB: Một hệ thống quản trị CSDL mới hơn, tạo ra bởi các nhà phát triển của MySQL. Engine của nó được viết lại và tối ưu để cải thiện hiệu suất. MariaDB cung cấp khả năng tương thích với Cơ sở dữ liệu Oracle (một hệ thống quản lý cơ sở dữ liệu thương mại phổ biến khác).

- Azure Database for PostgreSQL - CSDL hybrid quan hệ-đối tượng, Bạn có thể lưu trữ dữ liệu trong các bảng quan hệ, nhưng cơ sở dữ liệu PostgreSQL cũng cho phép bạn lưu trữ các kiểu dữ liệu tùy chỉnh, với các thuộc tính phi quan hệ của riêng chúng.

Như với hệ thống Azure SQL DB, cơ sở dữ liệu quan hệ nguồn mở được Database administrators quản lý để hỗ trợ các ứng dụng giao dịch và cung cấp nguồn dữ liệu cho các data engineers xây dựng đường truyền cho các giải pháp phân tích và data analyst tạo báo cáo.

## 3.Azure Cosmos DB

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/cosmos-db.png)

Azure Cosmos DB là hệ thống cơ sở dữ liệu phi quan hệ (NoSQL) quy mô toàn cầu hỗ trợ cho lập trình API, cho phép bạn lưu trữ và quản lý dữ liệu dưới dạng tài liệu JSON, cặp key-value, column-families, and graphs.

Trong một số tổ chức, các phiên bản Cosmos DB có thể được cung cấp và quản lý bởi Database administrator, mặc dù thường các nhà phát triển phần mềm quản lý lưu trữ dữ liệu NoSQL như một phần của kiến trúc ứng dụng tổng thể. Các data engineers thường cần tích hợp các nguồn dữ liệu Cosmos DB vào các giải pháp phân tích doanh nghiệp hỗ trợ việc lập mô hình và báo cáo bởi các nhà data analyst.

## 3.Azure Storage

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-storage.png)

Azure Storage là một dịch vụ chính của Azure cho phép bạn lưu dữ liệu trong:

- Blob containers - khả năng mở rộng, hiệu quả về chi phí cho các tệp nhị phân.

- File shares: chia sẻ file qua mạng như bạn thường thấy trong các mạng doanh nghiệp.

- Tables =- lưu trữ dạng key -value cho các ứng cần đọc và ghi dữ liệu nhanh chóng.

Data engineers dùng Azure Storage để tổ chức các data lakes - lưu trữ dạng blob với không gian phân cấp cho phép các tệp được sắp xếp trong các thư mục trong hệ thống tệp phân tán. 

## 4. Azure Data Factory

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-data-factory.png)

Azure Data Factory là 1 dịch vụ của Azure cho phép người dùng định nghĩa và lên lịch cho các data pipelines thực hiện hoạt động chuyển đổi và truyên dữ liệu. Bạn có thể tích hợp pipelines với các dịch vụ Azure khác, cho phép bạn nhập dữ liệu từ cloud, xử lý dữ liệu bằng cách sử dụng các tính toán dựa trên cloud, và lưu kết quả vào trong các kho lưu trữ dữ liễu khác.

Azure Data Factory được dùng với data engineer để xây dựng các giải pháp ETL để đưa vào kho lưu trữ dữ liệu phân tích với dữ liệu từ các hệ thống giao dịch trong toàn tổ chức. 

## 5.Azure Synapse Analytics

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/Azure-Synapse.png)

Azure Synapse Analytics là một giải pháp phân tích dữ liệu toàn diện, thống nhất, nó cung cung một giao diện dịch vụ độc lâp cho nhiều khả năng phân tích bao gồm:

- Pipelines: cùng dựa trên công nghệ của Azure Data Factory.

- SQL - một SQL DB engine có khả năng co dãn, tối ưu cho các luồng việc của data warehouse.

- Apache Spark: một hệ thống xử lý dữ liệu mã nguồn mở hỗ trợ nhiều ngôn ngữ và APIs, bao gồm Java, Scala, Python, and SQL.

- Azure Synapse Data Explorer: Giải pháp phân tích dữ liệu hiệu suất cao, tối ưu cho các truy vấn thời gian thực cho việc log và truy vấn từ xa, sử dụng Kusto Query Language (KQL).

Các data engineers có thể dùng Azure Synapse Analytics để tạo một giải pháp thống nhất cho việc phân tích dữ liệu bao gồm việc tích hợp các pipelines, data warehouse storage, và data lake storage trong một dịch vụ độc lâp.

Data analysts có thể dùng SQL and Spark pools thông qua một notebooks để khám phá và phân tích dữ liệu, đồng thời tận dụng khả năng tích hợp với các dịch vụ như Azure Machine Learning và Microsoft Power BI để tạo mô hình dữ liệu và trích xuất thông tin chi tiết từ dữ liệu. 

## 6.Azure Databricks

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-databricks.png)

Azure Databricks là phiên bản tích hợp Azure của nền tảng Databricks phổ biến, kết hợp nền tảng xử lý dữ liệu Apache Spark với ngữ nghĩa cơ sở dữ liệu SQL và giao diện quản lý tích hợp cho phép phân tích dữ liệu quy mô lớn.

Data engineers có thể sử dụng kỹ năng Databricks và Spark hiện có để tạo kho dữ liệu phân tích trong Azure Databricks.

Data Analysts có thể dùng native notebook hỗ trợ trong Azure Databricks để truy vấn và trực quan hoá dữ liệu để dễ sử dụng trên giao diện web.

## 7.Azure HDInsight

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/hdinsight.png)

Azure HDInsight là 1 dịch vụ Azure cung cấp các cụm được lưu trữ trên Azure cho các công nghệ xử lý dữ liệu lớn nguồn mở Apache phổ biến, bao gồm:

- Apache Spark: Hệ thống xử lý dữ liệu phân tán hỗ trợ nhiều ngôn ngữ lập trình và APIs, bao gồm Java, Scala, Python, và SQL.

- Apache Hadoop: Một hệ thống phân tán sử dụng MapReduce để xử lý lượng lớn dữ liệu một cách hiệu quả giữa các nodes cluster. Các công việc MapReduce có thể được viết bằng Java hoặc được trừu tượng hóa bởi các interface như Apache Hive - một API dựa trên SQL chạy trên Hadoop. 

-Apache HBase: một hệ thống mã nguồn mở để lưu trữ và truy vấn dữ liệu NoSQL quy mô lớn. 

- Apache Kafka: 1 message broker để xử lý các luồng dữ liệu.

- Apache Storm:1 hệ thống nguồn mở cho xử lý thời gian thực thông qua các topology của spouts and bolts.

Data engineers có thể dùng Azure HDInsight để hỗ trợ các công việc phân tích big data dựa trên nhiều công nghệ mã nguồn mở.

## 8.Azure Stream Analytics

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/stream-analytics.png)

Azure Stream Analytics là một công cụ xử lý luồng theo thời gian thực ghi lại luồng dữ liệu từ đầu vào, áp dụng truy vấn để trích xuất và thao tác dữ liệu từ luồng đầu vào và ghi kết quả vào đầu ra để phân tích hoặc xử lý thêm. 

Data engineers có thể kết hợp Azure Stream Analytics vào các kiến trúc phân tích dữ liệu để thu thập dữ luồng dữ liệu truyền vào để nhập vào kho dữ liệu phân tích hoặc để trực quan hóa theo thời gian thực. 

## 9.Azure Data Explorer

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/azure-data-explorer.png)

Azure Purview cung cấp giải pháp cho khả năng khám phá và quản trị dữ liệu trên toàn doanh nghiệp. Bạn có thể sử dụng Azure Purview để tạo bản đồ dữ liệu của mình và theo dõi dòng dữ liệu trên nhiều nguồn dữ liệu và hệ thống, cho phép bạn tìm thấy dữ liệu đáng tin cậy để phân tích và báo cáo. 

Data engineers có thể sử dụng .zure Purview để thực thi quản trị dữ liệu trong toàn doanh nghiệp và đảm bảo tính toàn vẹn của dữ liệu được sử dụng để hỗ trợ các công việc phân tích.

## 10.Microsoft Power BI

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azue-job/power-bi.png)

Microsoft Power BI là một nền tảng để lập mô hình và báo cáo dữ liệu phân tích mà các nhà phân tích dữ liệu có thể sử dụng để tạo và chia sẻ tương tác với dữ liệu trực quan hoá. Báo cáo Power BI có thể được tạo bằng cách sử dụng ứng dụng Power BI Desktop, báo cáo được xuất bản và phân phối thông qua các báo cáo và ứng dụng dựa trên web trong dịch vụ Power BI, cũng như trong ứng dụng Power BI dành cho thiết bị di động. 

# Summary

Quản lý và làm việc với dữ liệu là một trong những kỹ năng đặc biệt đòi hỏi có sử hiểu biết của nhiều công nghệ khác nhau. Hầu hết các tổ chức xác định vai trò công việc cho các nhiệm vụ khác nhau chịu trách nhiệm quản lý dữ liệu. 

Qua bài viết này, chúng ta đã có thể có được các thông tin về:

- Các vai trò nghiệp vụ dữ liệu phổ biến.

- Các dịch vụ cloud được dùng bởi các chuyên gia dữ liệu.
