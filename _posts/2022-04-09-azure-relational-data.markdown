---
layout: post
title:  Explore fundamental relational data concepts
date:   2022-04-09
image:  relational.png
tags:   Azure Data-Analysis
---

* TOC
{:toc}

# Note

Các hệ thống ơ sở dữ liệu quan hệ là một cách phổ biến để lưu trữ và quản lý dữ liệu giao dịch và phân tích trong các tổ chức ở nhiều quy mô trên thế giới.

Thông qua module này, chúng ta sẽ đi tìm hiểu:

- Các đặc trưng của CSDL quan hệ.
- Định nghĩa chuẩn hoá - normalization.
- Định nghĩa về các loại câu lệnh SQL.
- Định nghĩa về các đối tượng phổ biến CSDL quan hệ.

# Chương 1: Dữ liệu quan hệ

Trong cơ sở dữ liệu quan hệ, bạn lập mô hình tập hợp các thực thể từ thế giới thực dưới dạng bảng. Một thực thể có thể là bất cứ thứ gì mà bạn muốn để ghi lại thông tin; thông thường là các đối tượng hay các sự kiện quan trọng. Ví dụ về hệ thống bán lẻ: bạn có thể tạo các bảng cho khách hàng, sản phẩm, đơn hàng và các mục hàng trong đơn đặt hàng. Một bảng thì chứa các hàng, một hàng thì đại diện cho một phiên bản của thực thể. Trong kịch bản bán lẻ này, mỗi hàng trong bảng khách hàng chứa dữ liệu về 1 khách hàng, mỗi hàng trong bảng sản phẩm thì định nghĩa về 1 sản phẩm, mỗi hàng trong bảng đơn hàng đại diện cho mỗi đơn hàng được tạo bởi khách hàng và mỗi hàng trong dòng bảng mặt hàng đại diện cho một sản phẩm đã được bao gồm trong một đơn đặt hàng.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/relational_db/1.png)

Các bảng quan hệ là một định dạng cho dữ liệu có cấu trúc và mỗi hàng trong 1 bảng có cùng tên các cột, qua một số trường hợp, không phải tất cả các cột đều cần có giá trị, ví dụ, một bảng khách hàng có thể bao gồm một cột `MiddleName` có thể rỗng (NULL) cho các hàng đại diện cho khách hàng không có tên đệm hoặc không biết tên đệm.

Mỗi cột lưu dữ liệu trong 1 định dạng dữ liệu đặc biệt. Ví dụ, một cột `Email` trong bảng `Customer` có thể được định nghĩa để lưu dữ liệu dạng text (với chiều dài cố định hay tuỳ ý). một cột `Price` trong bảng `Product` có thể định nghĩa để lưu dữ liệu dạng số thập phân, trong khi cột `Quantity` trong bảng `Order` có thể bị giới hạn ở các giá trị số nguyên, và cột `OrderDate` trong cùng bảng `Order` có thể được định nghĩa để lưu dữ liệu ở dạng ngày/giờ. Các kiểu dữ liệu có sẵn mà bạn dùng để định nghĩa 1 bảng sẽ dựa trên hệ thống CSDL mà bạn đang dùng; mặc dù có những chuẩn dữ liệu tiêu chuẩn được định nghĩa bởi Viên Tiêu chuẩn Hoa Kỳ (ANSI) được hỗ trợ bởi hầu hết các hệ thống cơ sở dữ liệu.

# Chương 2: Understand normalization

`Normalization` là một thuật ngữ dùng bởi các chuyên gia CSDL cho quá trình thiết kế các lược đồ nhằm giảm thiểu sự trùng lặp dữ liệu và đảm bảo tính toàn vẹn dữ liệu.

Mặc dù có nhiều quy tắc phức tạp xác định quá trình tái cấu trúc dữ liệu thành nhiều cấp độ (hoặc hình thức) chuẩn hóa khác nhau, một định nghĩa đơn giản cho các mục đích thực tế là:

1. Tách từng thực thể vào bảng riêng của nó.

2. Tách rời từng thuộc tính vào cột riêng. 

3. Xác định duy nhất từng cá thế thực thể (hàng) bằng cách dùng khoá chính.

4. Sử dụng khoá ngoại để kết nối các thực thể có liên quan.

Để hiểu rõ hơn về quy tấc cốt lõi của việc chuẩn hoá, giả sử bảng sau đại diện cho bảng tính mà một công ty sử dụng để theo dõi doanh số bán hàng của mình.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/relational_db/2.png)

Quan sát thấy rằng chi tiết về khách hàng và sản phẩm bị trùng lặp cho mỗi sản phẩm được bán; và tên khách hàng, địa chỉ, sản phẩm, và giá được gộ chung trên cùng một bảng tính.

Bây giờ chúng ta cùng quan sát việc chuẩn hoá sẽ thay đổi cách mà dữ liệu được lưu như thế nào:

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/relational_db/3.png)

Mỗi thực thể được đại diện trong dữ liệu (khách hàng, sản phẩm, đơn hàng bán hàng và mục hàng) được lưu trữ trong bảng riêng của nó và mỗi thuộc tính rời rạc của các thực thể đó nằm trong cột riêng của nó.

Việc ghi lại từng thể hiện của một thực thể dưới dạng một hàng trong một bảng dành riêng cho thực thể sẽ loại bỏ sự trùng lặp dữ liệu. Ví dụ: để thay đổi địa chỉ của khách hàng, bạn chỉ cần sửa đổi giá trị trong một hàng.

Việc phân tách các thuộc tính thành các cột riêng lẻ đảm bảo rằng mỗi giá trị được giới hạn ở một kiểu dữ liệu thích hợp - ví dụ: giá sản phẩm phải là giá trị thập phân, trong khi số lượng mục hàng phải là số nguyên. Ngoài ra, việc tạo các cột riêng lẻ cung cấp mức độ chi tiết trong dữ liệu rất hữu ích để truy vấn - ví dụ: bạn có thể dễ dàng lọc khách hàng thành những người sống ở một thành phố cụ thể.

Các thể hiện của mỗi thực thể được xác định duy nhất bởi một ID hoặc giá trị khóa khác, được gọi là khóa chính; và khi một thực thể tham chiếu đến một thực thể khác (ví dụ: một đơn đặt hàng có một khách hàng được liên kết), khi đó khóa chính của thực thể liên quan được lưu trữ dưới dạng khóa ngoại. Bạn có thể tra cứu địa chỉ của khách hàng (chỉ được lưu trữ một lần) cho mỗi bản ghi trong bảng `Order` bằng cách tham chiếu bản ghi tương ứng trong bảng `Customer`. Thông thường, hệ thống quản lý cơ sở dữ liệu quan hệ (RDBMS) có thể thực thi tính toàn vẹn tham chiếu để đảm bảo rằng giá trị được nhập vào trường khóa ngoại có khóa chính tương ứng hiện có trong bảng liên quan - ví dụ: ngăn chặn đơn đặt hàng cho khách hàng không tồn tại.

Trong một số trường hợp, một khóa (chính hoặc ngoại) có thể được định nghĩa là một khóa tổng hợp dựa trên sự kết hợp duy nhất của nhiều cột. Ví dụ: bảng `LineItems` trong ví dụ trên sử dụng sự kết hợp duy nhất của `OrderNo` và `ItemNo` để xác định một mục hàng từ một đơn đặt hàng riêng lẻ.

# Chương 3: SQL

SQL - Structured Query Language, là ngôn ngữ dùng để giao tiếp với CSDL quan hệ. Nó là ngôn ngữ tiêu chuẩn cho các hệ quản trị CSDL quan hệ. Các câu lệnh SQL dùng để thực hiện các nhiệm vụ như cập nhật dữ liệu trong CSDL, lấy dữ liệu từ CSDL, Một vài hệ quản trị CSDL phổ biến dùng SQL như: MSSQL, MySQL, PostgreSQL và Oracle.

> * SQL được tiêu chuẩn hoá ban đầu bởi Viện tiêu chuẩn Hoa Kỳ (ANSI) vào năm 1986 và Tiêu chuẩn hoá quốc tế (ISO) năm 1987. Kể từ đó, tiêu chuẩn này đã được mở rộng nhiều lần do các nhà cung cấp cơ sở dữ liệu quan hệ đã thêm các tính năng mới vào hệ thống của họ. Ngoài ra, hầu hết các nhà cung cấp cơ sở dữ liệu đã thêm các phần mở rộng độc quyền của riêng họ mà không phải là một phần của tiêu chuẩn, điều này đã dẫn đến nhiều loại phương ngữ của SQL.

Bạn có thể sử dụng các câu lệnh SQL như SELECT, INSERT, UPDATE, DELETE, CREATE và DROP để thực hiện hầu hết mọi thứ bạn cần làm với cơ sở dữ liệu. Mặc dù các câu lệnh SQL này là một phần của tiêu chuẩn SQL, nhiều hệ quản trị cơ sở dữ liệu cũng có các phần mở rộng độc quyền bổ sung của riêng chúng để xử lý các chi tiết cụ thể của hệ quản trị cơ sở dữ liệu đó. Các phần mở rộng này cung cấp chức năng không có trong SQL thông thường và bao gồm các lĩnh vực như quản lý bảo mật và khả năng lập trình. Ví dụ: Microsoft SQL Server và dịch vụ cơ sở dữ liệu Azure dựa trên bộ máy cơ sở dữ liệu SQL Server, nó sử dụng Transact-SQL. Việc thêm vào các phần mở rộng này bao gồm các phần mở rộng độc quyền để viết các stored procedures và triggers (mã ứng dụng có thể được lưu trữ trong cơ sở dữ liệu) và quản lý tài khoản người dùng. PostgreSQL và MySQL cũng có các phiên bản riêng của các tính năng này.

Một số phương ngữ phổ biến của SQL bao gồm:

- Transact-SQL (T-SQL). Một phiên bản của SQL được dùng bởi Microsoft SQL Server và Azure SQL services.

- pgSQL. Đây là phương ngữ, với các phần mở rộng được triển khai trong PostgreSQL.

- PL/SQL. Đây là phương ngữ được sử dụng bởi Oracle. PL/SQL là viết tắt của `Procedural Language/SQL`.

Người dùng có kế hoạch làm việc cụ thể với một hệ thống cơ sở dữ liệu duy nhất nên tìm hiểu sự phức tạp của phương ngữ và nền tảng SQL ưa thích của họ.

> * Các ví dụ mã SQL trong mô-đun này dựa trên phương ngữ Transact-SQL, trừ khi được chỉ định khác. Cú pháp cho các phương ngữ khác nói chung là tương tự, nhưng có thể khác nhau ở một số chi tiết.

## Các loại lệnh SQL:

Các câu lệnh SQL được nhóm thành ba nhóm logic chính:

- Ngôn ngữ định nghĩa dữ liệu (DDL).

- Ngôn ngữ điều khiển dữ liệu (DCL).

- Ngôn ngữ thao tác dữ liệu (DML).

## Ngôn ngữ định nghĩa dữ liệu DDL: 

DDL được dùng đề tạo, chỉnh sửa và xoá các bảng và các đối tượng khác trng một CSDL (bảng, stored procedures, view,...)

Những lệnh DDL phổ biển gồm:

| Statement      | Description                                                |
| -------------- | ---------------------------------------------------------- |
| CREATE         | Tạo một đối tượng mới trong CSDL, như bảng, view ...       |
| ALTER          | Thay đổi cấu trúc đối tượng. Ví dụ, thêm cột vào bảng      |
| DROP           | Xoá đối tượng khỏi CSDL                                    |
| RENAME         | Đổi tên một đối tượng đã tồn tại                           |

Ví dụ về lệnh tạo table

```sql
CREATE TABLE Product
(
    ID INT PRIMARY KEY,
    Name VARCHAR(20) NOT NULL,
    Price DECIMAL NULL
);
```

> * Các cột được đánh dấu là NOT NULL được gọi là cột bắt buộc. Nếu bạn bỏ qua mệnh đề NOT NULL, bạn có thể tạo các hàng không chứa giá trị trong cột. Một cột trống trong một hàng được cho là có giá trị NULL.

Các kiểu dữ liệu có sẵn cho các cột trong bảng sẽ khác nhau giữa các hệ thống quản lý cơ sở dữ liệu. Tuy nhiên, hầu hết các hệ quản trị cơ sở dữ liệu đều hỗ trợ các kiểu số như INT (một số nguyên hoặc số nguyên), DECIMAL (một số thập phân) và các kiểu chuỗi như VARCHAR (VARCHAR là viết tắt của dữ liệu ký tự có độ dài thay đổi). Để biết thêm thông tin, hãy xem tài liệu cho hệ thống quản lý cơ sở dữ liệu mà bạn chọn.

## Ngôn ngữ điều khiển dữ liệu DCL:

Người quản trị cơ sở dữ liệu thường sử dụng các câu lệnh DCL để quản lý quyền truy cập vào các đối tượng trong cơ sở dữ liệu bằng cách cấp, từ chối hoặc thu hồi quyền cho người dùng hoặc nhóm cụ thể.

Có 3 câu lệnh DCL chính là

| Statement      | Description                                                |
| -------------- | ---------------------------------------------------------- |
| GRANT          | Cấp phép cho một hành động cụ thể                          |
| DENY           | Chặn quyền cho một hành động cụ thể                        |
| REVOKE         | Xoá một quyền đã cấp trước đó                              |

Ví dụ câu lệnh cho phép `user1` đọc, thêm, chỉnh sửa dữ liệu trong bảng `Product`:

```sql
GRANT SELECT, INSERT, UPDATE
ON Product
TO user1;
```
## Ngôn ngữ thao tác dữ liệu DML:

Bạn sử dụng các câu lệnh DML để thao tác các hàng trong bảng. Các câu lệnh này cho phép bạn truy xuất (truy vấn) dữ liệu, chèn các hàng mới hoặc sửa đổi các hàng hiện có. Bạn cũng có thể xóa các hàng nếu bạn không cần chúng nữa.

Có 4 câu lệnh DML chính là

| Statement      | Description                                                |
| -------------- | ---------------------------------------------------------- |
| SELECT         | Đọc các hàng từ bảng                                       |
| INSERT         | Thêm hàng mới vào bảng                                     |
| UPDATE         | Sửa dữ liệu trong hàng đã tồn tại                          |
| DELETE         | Xoá hàng                                                   |

Dạng cơ bản của câu lệnh INSERT sẽ chèn từng hàng một. Theo mặc định, các câu lệnh SELECT, UPDATE và DELETE được áp dụng cho mọi hàng trong bảng. Bạn thường áp dụng mệnh đề WHERE với các câu lệnh này để xác định tiêu chí; chỉ những hàng phù hợp với các tiêu chí này sẽ được chọn, cập nhật hoặc xóa.

Về các ví dụ các bạn có thể xem tại: [Query with SQL](https://docs.microsoft.com/en-us/learn/modules/explore-relational-data-offerings/4-query-with-sql)

Chủ đề này mô tả một số câu lệnh và cú pháp SQL cơ bản để giúp bạn hiểu cách SQL được sử dụng để làm việc với các đối tượng trong cơ sở dữ liệu. Nếu bạn muốn tìm hiểu thêm về cách truy vấn dữ liệu bằng SQL, hãy xem lại đường dẫn học tập [Bắt đầu truy vấn với Transact-SQL](https://docs.microsoft.com/en-us/learn/paths/get-started-querying-with-transact-sql/)

# Chương 4: Describe database objects

Bên cạnh các bảng, CSDL quan hệ cũng có thể chứa các dạng cấu trúc khác giúp tối ưu hoá việc tổ chức dữ liệu, Trong phần này, bạn sẽ tìm hiểu chi tiết hơn về ba trong số các cấu trúc này:  views, stored procedures, and indexes.

## 1. View là gì?

1 View được xem là một bảng ảo dựa trên kết quả của câu lệnh SELECT. Bạn có thể coi 1 view như một cửa sổ trên các hàng được chỉ định trong một hoặc nhiều bảng bên dưới. Ví dụ: bạn có thể tạo view trên bảng `Order` và `Customer` để truy xuất dữ liệu đơn hàng và khách hàng để cung cấp một đối tượng giúp dễ dàng xác định địa chỉ giao hàng cho các đơn hàng:

```sql
CREATE VIEW Deliveries
AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.CustomerID = c.ID;
```
Bạn có thể truy vấn view và lọc dữ liệu theo cách giống như một bảng. Truy vấn sau đây tìm thông tin chi tiết về các đơn đặt hàng cho những khách hàng sống ở Seattle:

```sql
SELECT OrderNo, OrderDate, LastName, Address
FROM Deliveries
WHERE City = 'Seattle';
```

## 2. Stored Procedure là gì?

1 Stored Procedure xác định các câu lệnh SQL có thể được chạy trên lệnh. Các stored procedure có thể dùng để đóng gói các chương trình mang tính logic trong CSDL cho các hành động mà ứng dụng cần thực hiện khi làm việc với dữ liệu.

Bạn có thể định nghĩa 1 stored procedure được lưu trữ với các tham số để tạo ra một giải pháp linh hoạt cho các hành động phổ biến có thể cần được áp dụng cho dữ liệu dựa trên một khóa hoặc tiêu chí cụ thể. Ví dụ: stored procedure được lưu trữ sau đây có thể được tạo ra để thay đổi tên của sản phẩm dựa trên ID sản phẩm được chỉ định.

```sql
CREATE PROCEDURE RenameProduct
	@ProductID INT,
	@NewName VARCHAR(20)
AS
UPDATE Product
SET Name = @NewName
WHERE ID = @ProductID;
```

Khi một sản phẩm cần được đổi tên, bạn có thể thực hiện stored procedure đã lưu trữ, cung cấp ID của sản phẩm và tên mới sẽ được gán:

```sql
EXEC RenameProduct 201, 'Spanner';
```

## 3. Index là gì?

Indexing giúp bạn tìm kiếm dữ liệu trong 1 bảng. Hãy nghĩ về một chỉ mục trên một bảng giống như một mục lục ở cuối một cuốn sách. Mục lục sách chứa một tập hợp các tài liệu tham khảo đã được sắp xếp, với các trang mà mỗi tài liệu tham khảo xuất hiện trên đó. Khi bạn muốn tìm tham chiếu đến một mục trong sách, bạn tra cứu nó thông qua mục lục. Bạn có thể sử dụng số trang trong chỉ mục để chuyển trực tiếp đến các trang chính xác trong sách. Nếu không có chỉ mục, bạn có thể phải đọc toàn bộ cuốn sách để tìm tài liệu tham khảo mà bạn đang tìm kiếm.

Khi bạn tạo chỉ mục trong cơ sở dữ liệu, bạn chỉ định một cột từ bảng và chỉ mục chứa bản sao của dữ liệu này theo thứ tự được sắp xếp, với các con trỏ đến các hàng tương ứng trong bảng. Khi người dùng chạy một truy vấn chỉ định cột này trong mệnh đề WHERE, hệ thống quản lý cơ sở dữ liệu có thể sử dụng chỉ mục này để tìm nạp dữ liệu nhanh hơn so với việc nó phải quét qua toàn bộ bảng từng hàng.

Ví dụ: bạn có thể sử dụng mã sau để tạo chỉ mục trên cột `Name` của bảng `Product`:

```sql
CREATE INDEX idx_ProductName
ON Product(Name);
```

Chỉ mục tạo một cấu trúc cây mà trình tối ưu hóa truy vấn của hệ thống cơ sở dữ liệu có thể sử dụng để nhanh chóng tìm thấy các hàng trong bảng `Product` dựa trên một `Name` được chỉ định.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/relational_db/4.png)

Đối với một bảng chứa ít hàng, việc sử dụng chỉ mục có lẽ không hiệu quả hơn việc chỉ đọc toàn bộ bảng và tìm các hàng được truy vấn yêu cầu (trong trường hợp đó, trình tối ưu hóa truy vấn sẽ bỏ qua chỉ mục). Tuy nhiên, khi một bảng có nhiều hàng, các chỉ mục có thể cải thiện đáng kể hiệu suất của các truy vấn.

Bạn có thể tạo nhiều chỉ mục trên một bảng. Vì vậy, nếu bạn cũng muốn tìm sản phẩm dựa trên giá, việc tạo một chỉ mục khác trên cột `Price` trong bảng `Product` có thể hữu ích. Tuy nhiên việc lưu trữ các chỉ mục cũng sẽ tốn bộ nhớ. Chỉ mục sử dụng không gian lưu trữ và mỗi khi bạn chèn, cập nhật hoặc xóa dữ liệu trong bảng, chỉ mục cho bảng đó phải được duy trì. Công việc bổ sung này có thể làm chậm các hoạt động chèn, cập nhật và xóa. Bạn phải cân bằng giữa việc có các chỉ mục giúp tăng tốc truy vấn của bạn so với thời gian thực hiện các thao tác khác.