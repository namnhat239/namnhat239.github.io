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

### A.File Storage

Khả năng lưu trữ dữ liệu trong tệp là yếu tố cốt lõi của bất kỳ hệ thống máy tính nào. Các tệp có thể được lưu trữ trong các hệ thống tệp cục bộ trên đĩa cứng của máy tính cá nhân của bạn và trên các phương tiện di động như ổ USB; nhưng trong hầu hết các tổ chức, các tệp dữ liệu quan trọng được lưu trữ tập trung trong một số loại hệ thống lưu trữ tệp dùng chung. Càng ngày, vị trí lưu trữ trung tâm đó càng được lưu trữ trên đám mây, cho phép lưu trữ hiệu quả về chi phí, an toàn và đáng tin cậy cho khối lượng lớn dữ liệu.

Định dạng tệp cụ thể được sử dụng để lưu trữ dữ liệu phụ thuộc vào một số yếu tố, bao gồm:

- Loại dữ liệu đang được lưu trữ (có cấu trúc, bán cấu trúc hoặc không có cấu trúc).

- Các ứng dụng và dịch vụ sẽ cần đọc, ghi và xử lý dữ liệu.

- Con người cần các tệp dữ liệu có thể đọc được hoặc được tối ưu hóa để lưu trữ và xử lý hiệu quả.

Dưới đây là một số tệp phổ biến:

1. Delimited text files

Dữ liệu thường được lưu trữ ở định dạng văn bản thuần túy với các trường phân cách và hàng cụ thể. Định dạng phổ biến nhất cho dữ liệu được phân tách là các giá trị được phân tách bằng dấu phẩy - Comma Separated Values (CSV), trong đó các trường được phân tách bằng dấu phẩy và các hàng được kết thúc bằng một ký tự xuống dòng / dòng mới. Theo tùy chọn, dòng đầu tiên có thể bao gồm tên trường. Các định dạng phổ biến khác bao gồm các giá trị được phân tách bằng tab (TSV) và được phân cách bằng dấu cách (trong đó các tab hoặc dấu cách được sử dụng để phân tách các trường) và dữ liệu có độ rộng cố định trong đó mỗi trường được phân bổ một số ký tự cố định. Văn bản được phân tách là một lựa chọn tốt cho dữ liệu có cấu trúc cần được truy cập bởi một loạt các ứng dụng và dịch vụ ở định dạng con người có thể đọc được.

Ví dụ sau cho thấy dữ liệu khách hàng ở định dạng được phân tách bằng dấu phẩy - CSV

```
FirstName,LastName,Email
Joe,Jones,joe@litware.com
Samir,Nadoy,samir@northwind.com
```

2. JavaScript Object Notation (JSON)

JSON là một định dạng phổ biến trong đó lược đồ tài liệu phân cấp được sử dụng để xác định các thực thể dữ liệu (đối tượng) có nhiều thuộc tính. Mỗi thuộc tính có thể là một đối tượng (hoặc một tập hợp các đối tượng); làm cho JSON trở thành một định dạng linh hoạt tốt cho cả dữ liệu có cấu trúc và bán cấu trúc.

Ví dụ sau cho thấy một tài liệu JSON chứa một tập hợp các khách hàng. Mỗi khách hàng có ba thuộc tính (firstName, lastName và contact) và thuộc tính contact chứa một tập hợp các đối tượng đại diện cho một hoặc nhiều phương thức liên hệ (email hoặc điện thoại). Lưu ý rằng các đối tượng được đặt trong dấu ngoặc nhọn ({..}) và các tập hợp được đặt trong dấu ngoặc vuông ([..]). Các thuộc tính được biểu diễn bằng các cặp tên: giá trị và được phân tách bằng dấu phẩy (,).

```json
{
  "customers":
  [
    {
      "firstName": "Joe",
      "lastName": "Jones",
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
    },
    {
      "firstName": "Samir",
      "lastName": "Nadoy",
      "contact":
      [
        {
          "type": "email",
          "address": "samir@northwind.com"
        }
      ]
    }
  ]
}
```

3. Extensible Markup Language (XML)

XML là một định dạng dữ liệu con người có thể đọc được, phổ biến trong những năm 1990 và 2000. Nó phần lớn đã được thay thế bằng định dạng JSON ít dài dòng hơn, nhưng vẫn có một số hệ thống sử dụng XML để biểu diễn dữ liệu. XML sử dụng các thẻ được đặt trong dấu ngoặc nhọn (<../>) để xác định các phần tử và thuộc tính, như được minh họa trong ví dụ này:

```xml
<Customers>
  <Customer name="Joe" lastName="Jones">
    <ContactDetails>
      <Contact type="home" number="555 123-1234"/>
      <Contact type="email" address="joe@litware.com"/>
    </ContactDetails>
  </Customer>
  <Customer name="Samir" lastName="Nadoy">
    <ContactDetails>
      <Contact type="email" address="samir@northwind.com"/>
    </ContactDetails>
  </Customer>
</Customers>
```

3. Binary Large Object (BLOB)

Tất cả các têp được lưu dữ dưới dạng dữ  liệu nhị phân (1 và 0), nhưng ở các định dạng mà con người có thể đọc được như đã nói ở trên, các byte dữ liệu nhị phân được ánh xạ thành các ký tự có thể in được (thường là thành ASCII hoặc Unicode). Tuy nhiên, một số định dạng tệp, đặc biệt đối với dữ liệu không có cấu trúc, lưu trữ dữ liệu dưới dạng tệp nhị phân thô mà các ứng dụng phải diễn giải và hiển thị. Các loại dữ liệu phổ biến được lưu trữ dưới dạng nhị phân bao gồm hình ảnh, video, âm thanh và các tài liệu dành riêng cho ứng dụng.

Khi làm việc với dữ liệu như thế này, các chuyên gia dữ liệu thường gọi các tệp dữ liệu là BLOB (Binary Large Object).

4. Tối ưu các định dạng tệp tin:

Mặc dù các định dạng mà con người có thể đọc được cho dữ liệu có cấu trúc và bán cấu trúc có thể hữu ích, nhưng chúng thường không được tối ưu hóa cho không gian lưu trữ hoặc quá trình xử lý. Theo thời gian, một số định dạng tệp chuyên biệt cho phép nén, lập chỉ mục, lưu trữ và xử lý hiệu quả đã được phát triển.

Một vài cách tối ưu định dạng file phổ biến gồm có Avro, ORC, và Parquet:

- Avro là một định dạng dựa trên bảng. Nó được tạo bởi Apache. Mỗi bản ghi chứa một tiêu đề mô tả cấu trúc của dữ liệu trong bản ghi. Tiêu đề này được lưu trữ duoi71dang5 JSON. Dữ liệu được lưu trữ dưới dạng binary. Một ứng dụng sử dụng thông tin trong tiêu đề để phân tích cú pháp dữ liệu nhị phân và trích xuất các trường mà nó chứa. Avro là một định dạng tốt để nén dữ liệu và giảm thiểu các yêu cầu về băng thông mạng và lưu trữ.

- ORC (Optimized Row Columnar format) tổ chức dữ liệu thành cột thay vì hàng. Nó được phát triển bởi HortonWorks để tối ưu hoá hoạt động đọc và ghi trong Apache Hive. Tệp ORC chứa các dải dữ liệu - stripe. Mỗi stripe chứa dữ liệu cho cột hoặc tập hợp các hàng. Một stripe sẽ chứa chỉ mục vào các hàng trong stripe, dữ liệu cho mỗi hàng và mợt chân trang chứa thống kê (đếm, tổng, tối đa, tối thiểu, v.v.) cho mỗi cột.

- Parquet là một định dạng dữ liệu cột khác. Nó được tạo ra bởi Cloudera và Twitter. Tệp Parquet chứa các nhóm hàng. Dữ liệu cho mỗi cột được lưu trữ cùng nhau trong cùng một nhóm hàng. Mỗi nhóm hàng chứa một hoặc nhiều phần dữ liệu.  Tệp Parquet bao gồm metadata mô tả tập hợp các hàng được tìm thấy trong mỗi đoạn. Một ứng dụng có thể sử dụng metadata này để nhanh chóng xác định vị trí đúng phân đoạn cho một tập hợp các hàng nhất định và truy xuất dữ liệu trong các cột được chỉ định cho các hàng này. Parquet chuyên lưu trữ và xử lý các kiểu dữ liệu lồng nhau một cách hiệu quả. Nó hỗ trợ các chương trình nén và mã hóa rất hiệu quả.

### B.Databases

Cơ sở dữ liệu được sử dụng để xác định một hệ thống trung tâm mà trong đó dữ liệu có thể được lưu trữ và truy vấn. Một cách đơn giản hơn, hệ thống file mà các file được lưu trữ trên đó cũng được xem là 1 loại CSDL; nhưng khi chúng ta dùng thuật ngữ này trong ngữ cảnh dữ liệu chuyên nghiệp, chúng ta thường muốn nói đến một hệ thống chuyên dụng để quản lý các bản ghi dữ liệu hơn là các tệp. 

1. Relational databases - CSDL quan hệ:

CSDL quan hệ thường dùng để lưu trữ và truy vấn dữ liệu có cấu trúc. Dữ liệu được lưu trữ trong các bảng sẽ đại diện cho các thực thể như khách hàng, sản phẩm, đơn đặt hàng. Mỗi thể hiện của một thực thể sẽ được gán 1 khoá chính (primary key) duy nhất để nhận dạng nó, và có những khoá khác để tham chiếu đến các thực thế trong các bảng khác. Ví dụ: Khoá chính của khách hàng có thể tham chiếu đến bản ghi đơn đặt hàng để chỉ ra khách hàng nào đã đặt hàng. Việc sử dụng các khóa để tham chiếu các thực thể dữ liệu cho phép một cơ sở dữ liệu quan hệ được chuẩn hóa; điều này một phần là nhằm loại bỏ các giá trị trùng lặp, ví dụ thông tin chi tiết về 1 khách hàng thì chỉ được lưu 1 lần, không phải cho mỗi đơn hàng mà khách hàng này đặt. Các bảng được quản lý và truy vấn bằng cách sử dụng Ngôn ngữ truy vấn có cấu trúc Structured Query Language (SQL), dựa trên chuẩn ANSII, vì vậy nó tương tự nhau trên nhiều hệ thống CSDL.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/relational-database.png)

2. Non-relational databases:

Non-relational databases là hệ thống quản lý dữ liệu không áp dụng lược đồ quan hệ cho dữ liệu, CSDL đặc trưng cho dạng này thường được gọi là NoSQL, mặc dù một số vẫn hỗ trợ biến thể của SQL.

Có 4 loại Non-relational databases thường được sử dụng.

- CSDL dạng key - value : trong đó một bản ghi sẽ chứa một key duy nhất và liên kết với một giá trị và có thể lưu ở bất kỳ định dạng nào.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/key-value-store.png)

- Document DB: là một dạng CSDL key-value đặc biệt, trong đó value sẽ là một JSON (hệ thống được tối ưu hóa để phân tích cú pháp và truy vấn).

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/document-store.png)

- CSDL họ cột - Column family databases: lưu trữ dữ liệu thành dạng bảng bao gồm các hàng và cột, nhưng có thể chia các cột thành các nhóm được gọi là họ cột. Mỗi họ cột chứa một tập hợp các cột có liên quan với nhau về mặt logic. 

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/column-family-store.png)

- Graph DB : lưu trữ các thực thể dưới dạng các nodes và các links để xác định mối quan hệ giữa chúng.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/graph.png)

# Chương III: xử lý dữ liệu giao dịch

Một hệ thống xử lý dữ liệu giao dịch là thứ mà hầu hết mọi người xem là chức năng chính của máy tính kinh doanh. Hệ thống giao dịch ghi lại các giao dịch gói gọn các sự kiện cụ thể mà tổ chức muốn theo dõi. Đó có thể là một giao dịch tài chính, ví dụ như hoạt động chuyển tiền giữa các tài khoản trong hệ 1 hệ thống ngân hàng, hay một phần của hệ thống bán lẻ, theo dõi các khoản thanh toán cho hàng hoá hay dịch vụ từ các khách hàng. Hãy coi một giao dịch như một đơn vị công việc nhỏ, rời rạc. 

Các hệ thống giao dịch thường có khối lượng lớn, đôi khi phải xử lý hàng triệu giao dịch trong một ngày. Dữ liệu được xử lý phải có thể được truy cập rất nhanh. Công việc được thực hiện bởi các hệ thống giao dịch thường được gọi là Xử lý giao dịch trực tuyến [(OLTP)](https://viblo.asia/p/oltp-va-olap-co-gi-khac-nhau-maGK786BZj2). 

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/transactional-processing.png)

Các giải pháp OLTP dựa trên một hệ thống CSDL, nơi mà việc lưu trữ dữ liệu tối ưu cho cả hoạt động đọc và ghi để hỗ trợ cho khối lượng các công việc giao dịch, mà ở đó, các bảng ghi dữ liệu được tạo, truy xuất, cập nhật và xoá (thường được gọi là hoạt động CRUD). Các hoạt động này được áp dụng theo giao dịch, theo các để đảm bảo tính toàn vẹn của cũa dữ liệu được lưu trữ trong CSDL. Để thực hiện được điều này, OLTP thực thi các giao dịch hỗ trợ gọi là ACID, thuộc tính này gồm có:

-Atomicity (Tính nguyên tố): mỗi giao dịch sẽ được xem là 1 đơn vị duy nhất mà nó thành công hoàn toàn hoặc thất bại hoàn toàn. Ví dụ: một giao dịch liên quan đến việc chuyển tiền từ một tài khoản và ghi số tiền tương tự vào 1 tài khoản khác, thì giao dịch này phải hoàn thành cả 2 hoạt động trên. Nếu một trong hai không thể hoàn thành thì hoạt động còn lại phải thất bại.

-Consistency (Tính nhất quán): các giao dịch chỉ có thể đưa dữ liệu trong CSDL từ một trạng thái hợp lệ sang trạng thái hợp lệ khác. Tiếp tục ví dụ ở trên, trạng thái hoàn thành của giao dịch phải phản ảnh được việc chuyển tiền từ tài khoản này sang 1 tài khoản khác.

-Isolate (Tính độc lập): Một giao dịch đang thực thi và chưa được xác nhận phải bảo đảm tách biệt khỏi các giao dịch khác. Ví dụ: trong khi giao dịch chuyển tiền từ tài khoản này sang tài khoản khác đang trong quá trình thực hiện, một giao dịch khác thực hiện kiểm tra số dư không thể truy xuất giá trị từ một tài khoản phản ảnh số dư diễn ra trước khi chuyển và giá trị choo một tài khoản khác phản ảnh số dư diễn ra trước khi chuyển

-Durability (Tính bền vững): Khi một giao dịch hoàn thành, nó sẽ duy trì trạng thái hoàn thành. Sau khi giao dịch chuyển khoản hoàn tất, số dư tài khoản được sửa đổi vẫn được duy trì cho nên ngay cả khi hệ thống CSDL bị tắt, giao dịch hoàn thành này vẫn được phản ánh khi hệ thống được bật lại.

Hệ thống OLTP thường được sử dụng để hỗ trợ các ứng dụng trực tiếp xử lý dữ liệu kinh doanh - thường được gọi là ứng dụng dòng doanh nghiệp (LOB). 

# Chương IV: Xử lý dữ liệu phân tích 

Analytical data processing thường sử dụng các hệ thống read-only (hoặc read-mostly) lưu trữ khối lượng lớn các dữ liệu mang tính lịch sử hay các số liệu kinh doanh.Việc xử lý có thể dựa trên 1 bản snapshot dữ liệu tại một điểm thời gian nhất định, hoặc một loạt các snapshot.

Các chi tiết cụ thể cho một hệ thống xử lý phân tích có thể khác nhau giữa các giải pháp, nhưng kiến trúc chung cho các giải pháp phân tích ở quy mô doanh nghiệp thì thường có mô hình như sau:

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/analytical-processing.png)

1. Các files có thể được lưu ở các [data lake](https://vietnix.vn/data-lake-la-gi/) trung tâm để phân tích.

2. Một quá trình extract, transform và load (ETL) thực hiện sao chép dữ liệu từ các files và các CSDL [OLTP](https://viblo.asia/p/oltp-va-olap-co-gi-khac-nhau-maGK786BZj2) vào data warehouse để tối ưu cho hoạt động đọc. Thông thường, các lược đồ của data warehouse thì dựa trên các bảng dữ kiện chứa các số liệu mà bạn muốn phân tích (ví dụ: số tiền hàng), với các bảng thứ nguyên có liên quan đại diện cho các thực thể mà bạn muốn đo lường chúng (ví dụ: khách hàng hoặc sản phẩm).

3. Dữ liệu trong data warehouse có thể được tổng hợp và load vào trong mô hình phân tích trực tuyến (OLAP) hoặc các cube. Các số liệu tổng hợp (số đo) từ các bảng dữ kiện thì được tính toán cho các giao điểm của các thứ nguyên từ bảng thứ nguyên. Ví dụ: doanh thu bán hàng có thể được tính theo ngày, khách hàng và sản phẩm.

4. Dữ liệu trong data lake, data warehouse và các mô hình phân tích có thể được truy xuất cho việc tạo báo cáo, visualizations và dashboards.

- Data lake là một khái niệm phổ biến trong xử lý phân tích dữ liệu hiện đại, nơi phải thu thập và phân tích một khối lượng lớn dữ liệu dựa trên files.

- Data warehouse là một cách thiết lập để lưu trữ dữ liệu trong một lược đồ quan hệ được tối ưu hóa cho các hoạt động đọc - chủ yếu là các truy vấn cho việc tạo báo cáo và hiển thị dữ liệu. Lược đồ data warehouse có thể yêu cầu một số dữ liệu không chuẩn hoá trong nguồn dữ liệu OLTP (đưa vào một số trùng lặp để làm cho các truy vấn thực hiện nhanh hơn).

- Một mô hình OLAP là một kiểu lưu trữ dữ liệu tổng hợp dưới dạng lược đồ quan hệ để tối ưu hoá cho các công việc phân tích. Tổng hợp dữ liệu được dựa trên các thứ nguyên ở các cấp khác nhau, cho phép bạn đi sâu vào / xem chi tiết để xem các tổng hợp ở nhiều cấp phân cấp; ví dụ để xem tổng doanh thu theo khu vực, theo thành phố, hay cho một địa chỉ riêng lẻ. Vì dữ liệu OLAP được tổng hợp trước nên có thể chạy nhanh chóng các truy vấn để trả về các bản tóm tắt mà nó chứa.

Các kiểu người dùng khác nhau có thể thực hiện công việc phân tích dữ liệu ở các giai đoạn khác nhau của toàn bộ kiến ​​trúc tổng thể. Ví dụ:

- Các nhà data scientists thì có thể làm việc trực tiếp với các files trong data lake để khám phá và lập mô hình dữ liệu.

- Data Analysts thì có thể truy vấn các bảng một cách trực tiếp trong data warehouse để tạo ra các báo cáo linh hoạt và visualizations/

- Business thì có thể sử dụng dữ liệu được tổng hợp trước trong mô hình phân tích ở dạng báo cáo hoặc ở trang dashboards.

# TỔNG KẾT

Dữ liệu được xem là cốt lõi của các ứng dụng phần mềm và các giải pháp. Nó có thể được hiển ở nhiều định dạng khác nhau , lưu trong files và trong CSDL, và sử dụng để ghi lại các giao dịch hay hỗ trợ cho việc báo cáo, phân tích.

Qua các khái niệm đã đề cập ở trên, chúng ta đã có thể có các kiến thức căn bản về 

- Xác định các định dạng dữ liệu phổ biến.
- Các tuỳ chọn lưu dữ liệu trong files.
- Các tuỳ chọn lưu dữ liệu trong Database.
- Đặc điểm các giải pháp xử lý dữ liệu giao dịch.
- Đặc điểm của các giải pháp xử lý dữ liệu phân tích.

Bạn đọc có thể tìm kiếm thêm các tài liệu tại trang của a Microsoft : [Azure Data Fundamentals](https://docs.microsoft.com/en-us/learn/certifications/azure-data-fundamentals/)