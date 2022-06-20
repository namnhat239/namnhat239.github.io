---
layout: post
title:  CI/CD with Github action and SonarQube
date:   2022-04-02
image:  cicd.png
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

## III. SonarQube
### 3.1 Unit test?
Đọc [here](https://topdev.vn/blog/unit-test-la-gi/)
### 3.2 Code Coverage?
- Độ phủ của Unit Test.
Read [here](https://viblo.asia/p/gioi-thieu-khai-niem-test-coverage-c0c1c2-ORNZqgyq50n)
### 3.2 SonarQube?

Nói nôm na SonaQube được dùng để phân tích code.

<quote>SonarQube là một open source platform, được phát triển bởi SonarSource dành cho việc kiểm tra liên tục chất lượng code (code quality), review code một cách tự động để phát hiện ra các bugs, code smell, lỗ hổng bảo mật cho 25+ ngôn ngữ lập trình khác nhau. SonarQube hỗ trợ báo cáo duplicated code, coding standards, unit tests, code coverage, code complexity, comments, bugs, and security vulnerabilities. Việc đánh giá này sẽ dựa trên các rules theo mặc định của nó hoặc do người dùng đặt. Tập hợp nhiều rules sẽ tạo thành 1 Quality Profiles. Danh sách các rule mặc định của SonarQube cho các ngôn ngữ có thể tìm thấy ở [đây](https://rules.sonarsource.com/)</quote> 

Một số thứ mà SonarQube cung cấp cho người dùng gồm:

- [**SonarLine**](https://www.sonarlint.org/): là một IDE extensions hỗ trợ cho việc phát hiện và fix các vấn đề về secu và code quatity một cách nhanh chóng.
- [**Quality Gates**](https://docs.sonarqube.org/latest/user-guide/quality-gates/): thực thi các policy về chất lượng code trong tổ chức bằng cách trả lời cho 1 câu hỏi duy nhất: Dự án của bạn đã sẵn sàng để release chưa?
- [**Clean as You Code**](https://docs.sonarqube.org/latest/user-guide/clean-as-you-code/): cung cấp cách tiếp cận mới tới code quality giúp loại bỏ hướng tiếp cận truyền thống. Là 1 develop, bạn sẽ tập trung vào việc duy trì các tiêu chuẩn cao và chịu trách nhiệm cho các mã nguồn mới mà bạn đang làm việc.
- [**Issue**](https://docs.sonarqube.org/latest/user-guide/issues/): nôm na là Sonarqube sẽ tạo ra 1 issue khi có 1 vấn đề vi phạm các rule: vulnerability, bug, code smell.
- [**Security Hotspots**](https://docs.sonarqube.org/latest/user-guide/security-hotspots/): Tìm các đoạn mã nhạy cảm có khả năng bị lỗi bảo mật cần xem xét lại ->> công việc audit tập trung vào tính năng này.


