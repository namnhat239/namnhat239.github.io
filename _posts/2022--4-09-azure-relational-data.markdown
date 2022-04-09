---
layout: post
title:  Explore fundamental relational data concepts
date:   2022-04-09
image:  relational.png
tags:   Azure Data-Analysis
---

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