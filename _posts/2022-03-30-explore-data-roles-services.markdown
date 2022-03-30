---
layout: post
title:  Explore data roles and services
date:   2022-03-30
image:  azure_1.png
tags:   Azure, Data-Analysis
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

Có rất nhiều vai trò liên quan đến việc quản lý, kiểm soát và sử dụng dữ liệu. Một vài vai trò thì theo định hướng kinh doánh, một số khác thì thiên về kỹ thuật nhiều hơn, một số lại tập trung vào việc nghiên cứu, một số lại là sự kết hợp của các khía cạnh khác nhau của việc quản lý dữ liệu. Tổ chức của bạn có thể định nghĩa ra nhiều vai trò khác nhau, hoặc cho chúng những cái tên khác nhau, truy nhiên,  những vai trò được mô tả trong phần này sẽ bao gồm các sự phân chia nhiêm vụ và trách nhiệm phổ biến nhất thường thấy.

Ba vai trò chính trong công việc liên quan đến dữ liệu trong hầu hết các tỏ chức gồm có:

- Database administrators: quản lý CSDL, cấp quyền cho người dùng, lưu trữ các bản sao backup và hồi phục khi có sự cố.

- Data engineers: quản lý cơ sở hạ tầng và các quy trình tích hợp dữ liệu trong tổ chức, áp dụng các quy trình làm sạch dữ liệu, xác định các quy tắc quản trị dữ liệu, triển khai các đường truyền luân chuyễn dữ liệu giữa các hệ thống(pipelines)

- Data analysts: khám phá và phân tích dữ liệu để tạo hình hoá và các biểu đồ cho phép tổ chức đưa ra viết định sáng suốt.

**Note**

Vai trò công việc được phân loại khác nhau dựa trên nhiệm vụ và trách nhiệm. Trong một vài tổ chức, một cá nhân vẫn có thể thực hiện nhiều vai trò, vì vậy trong vai trò là một database administrator họ vẫn có thể cung cấp CSDL giao dịch và sau đó với vai trò là mot65data engineer, họ có thể tạo một pipeline để chuyển dữ liệu từ CSDL đến data warehouse để xử lý.

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

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azure-sql.png)

Azure SQL là tên chung của một nhóm các giải pháp CSDL quan hệ dữ trên engine CSDL MSSQL. Azure SQL bao gồm:

- CSDL Azure SQL: Một CSDL dạng platform-as-a-service (PaaS) được quản lý bởi Azure.

- Azure SQL Managed Instance: Một phiên bản của SQL Server được duy trì tự động, cho phép cấu hình linh hoạt hơn Azure SQL DB nhưng  có nhiều trách nhiệm quản trị hơn cho chủ sở hữu.

- Azure SQL VM: Một máy ảo cài đặt SQL Server, cho phép cấu hình tối đa với toàn bộ trách nhiệm quản lý.

Các Database administrators thường sẽ cung cấp và quản lý hệ thống CSDL Azure SQL để hỗ trợ các ứng dụng dòng doanh nghiệp (LOB) cần lưu trữ dữ liệu giao dịch.

Các Data engineers có thể sử dụng hệ thống cơ sở dữ liệu Azure SQL làm nguồn vào cho các đường truyền dữ liệu thực hiện các hoạt động trích xuất, chuyển đổi và tải (ETL) để nhập dữ liệu giao dịch vào một hệ thống phân tích.

Các data analysts có thể truy vấn CSDL Azure SQL trực tiếp để tạo các báo cáo, mặc dù trong các tổ chức lớn, dữ liệu thường được kết hợp với dữ liệu từ các nguồn khác trong kho dữ liệu phân tích để hỗ trợ phân tích doanh nghiệp.

## 2.Azure Database for open-source relational databases

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/azure-database.png)

Azure bao gồm các dịch vụ quản lý cho các hệ thống CSDL quan hệ mã nguồn mở, bao gồm:

- Azure Database for MySQL - Một hệ thống quản trị CSDL mã nguồn mở đơn giản thường dùng trong Linux, Apche, MySQL and PHP (LAMP)

- Azure Database for MariaDB: Một hệ thống quản trị CSDL mới hơn, tạo ra bởi các nhà phát triển của MySQL. Engine của nó được viết lại và tối ưu để cải thiện hiệu suất. MariaDB cung cấp khả năng tương thích với Cơ sở dữ liệu Oracle (một hệ thống quản lý cơ sở dữ liệu thương mại phổ biến khác).

- Azure Database for PostgreSQL - CSDL hybrid quan hệ-đối tượng, Bạn có thể lưu trữ dữ liệu trong các bảng quan hệ, nhưng cơ sở dữ liệu PostgreSQL cũng cho phép bạn lưu trữ các kiểu dữ liệu tùy chỉnh, với các thuộc tính phi quan hệ của riêng chúng.

Như với hệ thống Azure SQL DB, cơ sở dữ liệu quan hệ nguồn mở được Database administrators quản lý để hỗ trợ các ứng dụng giao dịch và cung cấp nguồn dữ liệu cho các data engineers xây dựng đường truyền cho các giải pháp phân tích và data analyst tạo báo cáo.

## 3.Azure Cosmos DB

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/cosmos-db.png)

Azure Cosmos DB là hệ thống cơ sở dữ liệu phi quan hệ (NoSQL) quy mô toàn cầu hỗ trợ cho lập trình API, cho phép bạn lưu trữ và quản lý dữ liệu dưới dạng tài liệu JSON, cặp key-value, column-families, and graphs.

Trong một số tổ chức, các phiên bản Cosmos DB có thể được cung cấp và quản lý bởi Database administrator, mặc dù thường các nhà phát triển phần mềm quản lý lưu trữ dữ liệu NoSQL như một phần của kiến trúc ứng dụng tổng thể. Các data engineers thường cần tích hợp các nguồn dữ liệu Cosmos DB vào các giải pháp phân tích doanh nghiệp hỗ trợ việc lập mô hình và báo cáo bởi các nhà data analyst.
 