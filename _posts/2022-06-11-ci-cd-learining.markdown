---
layout: post
title:  CI/CD with Github action and SonarQube
date:   2022-04-02
<<<<<<< HAD
image:  cicd.png
=======
>>>>>>> 6aed9904e8c61dcaf443fa195ad59b4db6bd8471
tags:   sonar github action ci/cd
---

* TOC
{:toc}

<h1>CI/CD Github Actions & Sonarqube</h1>

## I. What is CD/CD?
"Nôm na"
- CI: Continuous Integration.<br>
- CD: Continioud Delivery<br>
--> quá trình tích hợp và triển khai nhanh và liên tục.<br/>
--> CI/CD là quá trình tự động thực hiện các quá trình build, test, release, deploy khi có các trigger như commit/merge code lên một branch định sẵn hoặc có thể là tự động chạy theo một lịch cố định.

## II. Github Actions
Github actions được sinh ra để hỗ trợ việc tự động hóa các tác vụ trong vòng đời của một phần mềm. Git actions hoạt động theo hướng sự kiện, nghĩa là nó sẽ thực hiện một loạt commands đã được định nghĩa sẵn khi có một sự kiện được xảy ra. Ví dụ như, bạn có thể cấu hình để mỗi khi có người tạo một mergers request lên một repository nào đó hệ thống sẽ tự động run commands để run các unit test case của bạn.

Cấu hình Github Actions `Workflow` được kích hoạt khi có 1 event xảy ra trong repo Github như: Pull request lên branch, tạo issue. Một `workflow` thì có thể có 1 hoặc nhiều job chạy theo tuần tự hoặc song song. Mỗi job sẽ chạy trong 1 máy ảo riêng của nó, hay trong 1 container mà có 1 hoặc nhiều bước các tập lệnh do người dùng định nghĩa hoặc chạy 1 action. 
Thành phần Actions:
### 2.1 Workflows
1 Workflows là một process đc cấu hình tự động để chạy một hoặc nhiều jobs. Chúng ta sử dụng 1 file yaml trong repo để diễn giải cho 1 workflow, và nó sẽ chạy khi có 1 sự kiện xảy ra trong repo đó, hoặc theo một lịch trình, hoặc có thể chạy "bằng cơm".

Workflow sẽ được đặt trong thư mục .github/workflows của 1 repo, và 1 repo thì có thể có nhiều workflows, một cái thì sẽ thực hiện một số công việc khác nhau. Ví dụ: bạn có thể có 1 Workflow để build và test các pull requests, một workflow khác để deloy ứng dụng mỗi khi tạo ra 1 bản release, và 1 workflow xử lý khi có ai đó tạo ra 1 issue.

### 2.2 Events
Events là một hoạt động đặc biệt trong 1 repo để trigger cho workflow run. Ví dụ, bạn có thể cấu hình để workflow bắt đầu khi có một người nó đó push code hoặc tạo merger request lên branch develop, tạo issue. Bạn cũng có thể trigger 1 workflow chạy theo 1 lịch trình, thông qua [REST API](https://docs.github.com/en/rest/repos/repos#create-a-repository-dispatch-event) hay "bằng cơm".

Danh sách các events có thể tham khảo tại [đây](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)

### 2.3 Jobs
Một jobs là một chuỗi các bước *(steps)* trong 1 workflow của 1 runner. Mỗi *steps* này là 1 đoạn shell script sẽ được thực thi hay một *action*. Vì mỗi bước được chạy trong cùng 1 runner, nên chúng có thể share data cho nhau từ bước này tới bước khác. Bạn có thể cấu hình 1 job chạy độc lập với các job khác; mặc định các jobs sẽ chạy song song với nhau.

For more: [Using jobs](https://docs.github.com/en/actions/using-jobs)

### 2.4 Actions
Một *action* là môt ứng dụng custom cho nền tảng Github Actions dùng để thực hiện một nhiệm vụ phức tạp và có tính lặp lại thường xuyên. Sử dụng action giúp giảm khối lượng code mà bạn đã viết trong file workflow. 1 Action có thể giúp giúp bạn pull một git repo từ github, setup nhanh gọn các chuỗi công cụ cần để bạn build môi trường hay setup authen với nhà cung cấp cloud.

Hiện tại github Marketplace cũng cung cấp rất nhiều actions có sẵn tại [đây](https://github.com/marketplace?type=actions) hoặc bạn có thể tự tạo.

### 2.4 Runners
1 Runner là 1 server dùng để chạy workflows khi mà chúng đc trigger. Mỗi runner có thể chạy 1 job độc lập trong 1 lần. GitHub cung cấp các môi trường runner gồm Ubuntu Linux, Microsoft Windows, macOS để chạy các workflows. Một runner luôn sẵn sàng lắng nghe các jobs, run một job tại một thời điểm, report process, logs và trả kết quả về cho GitHub. Nếu bạn cần một HĐH khác hay cần những cấu hình phần cứng đặc biệt, bạn cũng có thể tự host một cái runner riêng cho mình theo mô tả [sau](https://docs.github.com/en/actions/hosting-your-own-runners)
