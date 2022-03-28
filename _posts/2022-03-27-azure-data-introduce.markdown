---
layout: post
title:  Microsoft Azure Data Fundamentals - Explore core data concept
date:   2022-03-27
image:  azure_1.png
tags:   Azure, Data-Analysis
---

* TOC
{:toc}

# Tựa

Hello cả nhà, hôm nay thì mình cũng mò mẫm tự học về Data Analysis, sau một hồi tìm hiểu thì thấy a Microsoft có khá nhiều tài liệu hay ho từ cơ bản cho những người mới tìm hiểu, đi từ những khái niệm cơ bản nhất về dữ liệu. Bản thân mình cũng có một chút hứng thú về mảng này nên cũng ngồi đọc về nó. Các tài liệu này thì các bạn có thể tìm tại <https://docs.microsoft.com/en-us/learn/>. Sau khi đọc qua thì một phần vì muốn ghi chép lại cũng như rèn thêm khả năng dịch thuật nên mình quyết định sẽ đi "Vietsub" lại một số cái docs. Bạn đọc nếu cảm thấy có sai sót về các thông tin, thuật ngữ... về tài liệu thì rất mong mọi người có thể góp ý, sửa sai cho mình :D.

Ghi chép mình viết hôm nay bao gồm các khái niệm cơ bản vè dữ liệu, được dịch lại từ document <https://docs.microsoft.com/en-us/learn/paths/azure-data-fundamentals-explore-core-data-concepts/>, nó bao gồm những khái niệm, phân loại lưu trữ dữ liệu cũng như các kỹ thuật xử lý dữ liệu.

# Chương I: Giới thiệu

Trong vài thập kỷ qua, lượng dữ liệu được tạo ra bởi các hệ thống, ứng dụng và thiết bị đã tăng lên đáng kể. Dữ liệu ở khắp mọi nơi, trong vô số cấu trúc và định dạng. Giờ đây việc thu thập dữ liệu trở nên dễ dàng hơn, chi phí cho việc lưu trữ dữ liệu cũng rẻ hơn. Các giải pháp dữ liệu (Data solutions) bao gồm các công nghệ và platforms có thể giúp tạo thuận lợi cho việc thu thập, phân tích và lưu trữ thông tin có giá trị. Mọi doanh nghiệp đều muốn tăng doanh thu của mình và tạo ra lợi nhuận lớn hơn. Trong thị trường cạnh tranh này, thì dữ liệu được xem là một tài sản quý giá. Khi dữ liệu được phân tích một cách đúng đắn, nó sẽ sẽ cung cấp vô số thông tin hưu ích và giúp ích cho các quyết định kinh doanh quan trọng.

Khả năng nắm bắt, lưu trữ và phân tích dữ liệu là các yêu cầu cốt lõi đối với mọi tổ chức trên thế giới. Trong tài liệu này, chúng ta sẽ tìm hiểu về các tuỳ chọn để biểu diễn và lưu trữ dữ liệu, và cũng như các công việc điển hình liên quan đến lĩnh vực này. Thông qua đó, chúng ta có thể xây dựng được nền tảng để tìm hiểu về các kỹ thuật và dịch vụ được sử dụng để làm việc với dữ liệu.

Tài liệu này bao gồm:

- Xác định các định dạng dữ liệu phổ biến.
- Các tuỳ chọn lưu dữ liệu trong files.
- Các tuỳ chọn lưu dữ liệu trong Database.
- Đặc điểm các giải pháp xử lý dữ liệu giao dịch.
- Đặc điểm của các giải pháp xử lý dữ liệu phân tích.

# Chương II: Các định dạng dữ liệu

Dữ liệu là một tập hợp các dữ kiện như các số, mô tả và từ những quan sát được sử dụng để thu thập lại thông tin. Các cấu trúc dữ liệu là cách mà các dữ liệu thường được tổ chức đại diện cho các thực thể quan trọng với một tổ chức như: khách hàng, sản phẩm, đơn đặt hàng,... Mỗi thực thể thường có một hoặc nhiều thuộc tính hoặc đặc điểm (ví dụ: khách hàng có thể có tên, địa chỉ, số điện thoại, v.v.).

Dữ liệu có thể phân loại thành các loại sau: Structured data - dữ liệu có cấu trúc; semi-structured; và unstructured.

## Structured data - Dữ liệu có cấu trúc

Dữ liệu có cấu trúc là dữ liệu tuân theo một lược đồ cố định, vì vậy tất cả dữ liệu đều có các trường hoặc thuộc tính giống nhau. Thông thường nhất, lược đồ cho các thực thể dữ liệu có cấu trúc là dạng bảng, điều này cũng có nghĩa là dữ liệu được biểu thị trong một hoặc nhiều bảng, các bảng này chứa các dòng để đại diện cho từng trường hợp cụ thể của mỗi thực thể dữ liệu, và các cột thì đại diện cho thuộc tính của thực thể. Ví dụ dưới đây chỉ ra cách biểu diễn dạng bảng cho thực thể khách hàng và sản phẩm.

![Data table](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/structed_data.png)

Dữ liệu có cấu trúc thường được lưu trong cơ sở dữ liệu, trong đó các bảng có thể tham chiếu lần nhau thông qua các khoá trong mô hình quan hệ.

## Semi-structured data - Dữ liệu bán cấu trúc

Dữ liệu bán cấu trúc là thông tin có một số cấu trúc, nhưng cho phép một số biến thể giữa các cá thể thực thể. Ví dụ: trong khi hầu hết khách hàng có thể có một địa chỉ email, một số có thể có nhiều địa chỉ email và một số có thể không có.

Một trong những định dạng phổ biến của loại dữ liệu này có thể nói đến là `JSON` (JavaScript Object Notation). Ví dụ dưới đây hiển thị một cặp dữ liệu JSON chứa thông tin khách hàng. Bạn thấy mỗi khách hàng sẽ có địa chỉ và thông tin liên hệ, nhưng sẽ có một số trường khác nhau giữa 2 khách hàng:

Customer 1

```json
{
  "firstName": "Joe",
  "lastName": "Jones",
  "address":
  {
    "streetAddress": "1 Main St.",
    "city": "New York",
    "state": "NY",
    "postalCode": "10099"
  },
  "contact":
  [
    {
      "type": "home",
      "number": "555 123-1234"
    },
    {
      "type": "email",
      "address": "joe@litware.com"
    }
  ]
}
```

Customer 2

```json
{
  "firstName": "Samir",
  "lastName": "Nadoy",
  "address":
  {
    "streetAddress": "123 Elm Pl.",
    "unit": "500",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98999"
  },
  "contact":
  [
    {
      "type": "email",
      "address": "samir@northwind.com"
    }
  ]
}
```

## Unstructured data - Dữ liệu không cấu trúc

Không phải tất cả các dữ liệu đều có cấu trúc hay bán cấu trúc. Ví dụ như với các tài liệu, hình ảnh, âm thanh, video và các file binary có thể sẽ không có các cấu trúc đặc biệt. Các loại dữ liệu đó được phân thành `Dữ liệu không cấu trúc`.

Vi dụ về dữ liệu không có cấu trúc

![Data table](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/unstructed_data.png)

## Lưu trữ dữ liệu

Các tổ chức thường lưu trữ dữ liệu ở định dạng có cấu trúc, bán cấu trúc hoặc không có cấu trúc để ghi lại thông tin chi tiết về các thực thể (ví dụ: khách hàng và sản phẩm), các sự kiện cụ thể (chẳng hạn như giao dịch mua bán) hoặc thông tin khác dưới dạng tài liệu, hình ảnh và các định dạng khác. Dữ liệu được lưu trữ sau đó có thể được truy xuất để phân tích và báo cáo sau này.

Có hai loại lưu trữ dữ liệu phổ biến được sử dụng phổ biến:

- Files

- Databases

Chúng ta sẽ khám phá cả hai kiểu lưu trữ dữ liệu này ở phần dưới.
