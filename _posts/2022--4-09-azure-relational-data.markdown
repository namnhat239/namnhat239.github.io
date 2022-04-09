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