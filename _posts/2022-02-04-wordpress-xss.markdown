---
layout: post
title:  Wordpress Stored XSS CVE-2022-21662
date:   2022-04-02
image:  wp-2022-21662.png
tags:   analyze, wordpress
---

* TOC
{:toc}

# Note

Lỗi Stored XSS nằm trong tính năng thêm “slug” của wordpress post. Đoạn script sau khi được chèn vào thành công có thể thực thi ở cả phía giao diện của admin. Người dùng chỉ cần có quyền “author” là có thể thực thi lỗi này do chỉ cần thực hiện ở chức năng chỉnh sửa bài viết.

Phiên bản ảnh hưởng: Wordpress <= 5.8.2

# Analysis

## 1. Wordpress slug

WordPress Slug là đường dẫn đưa đến các bài viết trên WordPress. Trên WordPress, khi người dùng tạo một bài viết mới, WordPress Slug sẽ được tự động tạo ra dựa trên thiết lập trong phần cấu hình tạo đường dẫn Permalinks.

Người dùng có thể dễ dàng thay đổi Slug của 1 bài post trong WordPress bằng cách sử dụng chức năng Quick edit trong Post để tùy chỉnh.

## 2. Some things about this bug

Wordpress thường sử dụng tiêu đề của bài post để tạo ra slug. Ví dụ: với url là <http://localhost/wordpress/hello-world/> thì sẽ dẫn tới bài post có tiêu đề là  Hello World. Khi lưu một bài viết, Wordpress sẽ thực hiện chuyển đổi tiêu đề (title) của bài viết thành slug. Việc này được thực hiện trong hàm `wp_insert_post()` (wp-includes/post.php).

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture1.png)

Ở đây biến $post_name được sử dụng để lưu trữ giá trị cho slug.
Hàm `sanitize_title()` được sử dụng để chuyển 1 chuỗi sang slug, theo như mô tả của Wordpress:

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture2.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture3.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture4.png)

Tiếp tục luồng chương trình sẽ gọi tới hàm `wp_unique_post_slug()` (wp-includes/post.php) để kiểm tra xem slug đã tạo có bị trùng hay không, nếu có thì tiếp tục xử lý

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture5.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture6.png)

Ở hàm `wp_unique_post_slug()`, nếu giá trị slug bị trùng sẽ gọi tới hàm `_truncate_post_slug()`(wp-includes/post.php) để thực hiện truncate.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture7.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture8.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture9.png)

Ở hàm này nếu như chiều dài của slug lớn hơn chiều dài quy định, sẽ thực hiện `url_decode()` slug truyền vào, nếu hai giá trị là như nhau thì thực hiện cắt chuỗi tới chiều dài quy định, nếu không ta thấy giá trị của slug lúc này được encode lại bằng hàm `utf8_uri_encode()` (wp-includes/formatting.php) của wordpress: 

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture10.png)

Ở đây nếu giả sử ta đưa vào là một đoạn mã javascript đã được urlencode có dạng:

```
%22%2F%3E%3Cscript%3Ealert%281%29%3B%3C%2Fscript%3EAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

Thì sau khi giá trị này được decode sẽ không thỏa `điều kiện if` nên sẽ được encode một lần nữa bằng hàm `utf8_uri_encode()`, tuy nhiên hàm này chỉ thực hiện encode các kí tự Unicode, nên với ví dụ trên kết quả gọi hàm `utf8_uri_encode(‘”/><script>alert(1);</script>….’,200)` vẫn trả về giá trị đoạn mã ban đầu.

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture11.png)

Như vậy có thể tóm lại quá trình slug được xử lý gồm các bước:

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture12.png)


Như vậy để có thể tạo được payload từ  truncate_post_slug() cần phải tạo được 2 slug trùng nhau:

- Tạo 2 bài post khác nhau Test vàTest1.
- Tạo 1 sug cho post 1 với payload XSS đã được encode + chuỗi ký tự random (>=200)
- Tiếp tục tạo slug cho post 2 giống với slug post 1.

Nguyên nhân cần 200 ký tự trở lên vì mặc định hàm truncate_post_slug() thực hiện kiểm tra nếu chiều dài slug trên chiều dài quy định (mặc định là 200) thì mới thực hiện decode_url() payload đã truyền vào.

## 3. Fix

Bản vá lỗi (Wordpress 5.8.3) bổ sung tính năng encode các ký tự ascii và urlencode ở hàm `utf8_uri_encode()`

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture13.png)

![](https://raw.githubusercontent.com/namnhat239/namnhat239.github.io/main/images/wp_xss/Picture14.png)
