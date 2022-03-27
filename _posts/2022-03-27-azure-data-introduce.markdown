---
layout: post
title:  Microsoft Azure Data Fundamentals - Explore core data concept
date:   2022-03-27
image:  azure_1.png
tags:   Azure, Data-Analysis
---

# Tựa
Hello cả nhà, hôm nay thì mình cũng mò mẫm tự học về Data Analysis, sau một hồi tìm hiểu thì thấy a Microsoft có khá nhiều tài liệu hay ho từ cơ bản cho những người mới tìm hiểu, đi từ những khái niệm cơ bản nhất về dữ liệu. Bản thân mình cũng có một chút hứng thú về mảng này nên cũng ngồi đọc về nó. Các tài liệu này thì các bạn có thể tìm tại <https://docs.microsoft.com/en-us/learn/>. Sau khi đọc qua thì một phần vì muốn ghi chép lại cũng như rèn thêm khả năng dịch thuật nên mình quyết định sẽ đi "Vietsub" lại một số cái docs. Bạn đọc nếu cảm thấy có sai sót về các thông tin, thuật ngữ... về tài liệu thì rất mong mọi người có thể góp ý, sửa sai cho mình :D. 

Ghi chép mình viết hôm nay bao gồm các khái niệm cơ bản vè dữ liệu, được dịch lại từ document <https://docs.microsoft.com/en-us/learn/paths/azure-data-fundamentals-explore-core-data-concepts/>, nó bao gồm những khái niệm, phân loại lưu trữ dữ liệu cũng như các kỹ thuật xử lý dữ liệu.

# Chương I: Giới thiệu

Trong vài thập kỷ qua, lượng dữ liệu được tạo ra bởi các hệ thống, ứng dụng và thiết bị đã tăng lên đáng kể. Dữ liệu ở khắp mọi nơi, trong vô số cấu trúc và định dạng. Giờ đây việc thu thập dữ liệu trở nên dễ dàng hơn, chi phí cho việc lưu trữ dữ liệu cũng rẻ hơn. Các giải pháp dữ liệu (Data solutions) bao gồm các công nghệ và platforms có thể giúp tạo thuận lợi cho việc thu thập, phân tích và lưu trữ thông tin có giá trị. Mọi doanh nghiệp đều muốn tăng doanh thu của mình và tạo ra lợi nhuận lớn hơn. Trong thị trường cạnh tranh này, thì dữ liệu được xem là một tài sản quý giá. Khi dữ liệu được phân tích một cách đúng đắn, nó sẽ sẽ cung cấp vô số thông tin hưu ích và giúp ích cho các quyết định kinh doanh quan trọng.

Khả năng nắm bắt, lưu trữ và phân tích dữ liệu là các yêu cầu cốt lõi đối với mọi tổ chức trên thế giới. Trong tài liệu này, chúng ta sẽ tìm hiểu về các tuỳ chọn để biểu diễn và lưu trữ dữ liệu, và ũng như các công việc điển hình liên quan đến lĩnh vực này. Thông qua đó, chúng ta có thể xây dựng được nền tảng để tìm hiểu về các kỹ thuật và dịch vụ được sử dụng để làm việc với dữ liệu.

Tài liệu này bao gồm:

- Xác định các định dạng dữ liệu phổ biến.
- Các tuỳ chọn lưu dữ liệu trong files.
- Các tuỳ chọn lưu dữ liệu trong Database.
- Đặc điểm các giải pháp xử lý dữ liệu giao dịch.
- Đặc điểm của các giải pháp xử lý dữ liệu phân tích.