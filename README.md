# Student Second-hand Marketplace

**Nền tảng mua bán đồ cũ dành cho sinh viên** là dự án web giúp sinh viên đăng bán, tìm kiếm và trao đổi đồ dùng đã qua sử dụng trong phạm vi một cộng đồng hoặc khu vực trường học. Các mặt hàng hướng tới gồm giáo trình, xe đạp, đồ điện tử và nội thất phòng trọ.

README này mô tả mục tiêu, phạm vi và kế hoạch phát triển theo [Project Proposal](Ideas/Project_Proposal.docx). Các chức năng và hạ tầng bên dưới là nội dung dự kiến của đề xuất, chưa phải xác nhận đã được triển khai.

## Bối cảnh

Sinh viên thường cần thanh lý đồ dùng khi chuyển trọ, tốt nghiệp hoặc không còn nhu cầu sử dụng, đồng thời có nhu cầu mua đồ với chi phí phù hợp. Việc trao đổi qua các nhóm mạng xã hội còn gặp khó khăn trong tìm kiếm, lọc sản phẩm, đánh giá uy tín và kiểm soát tin rác.

Dự án hướng tới một kênh trao đổi tập trung, đúng đối tượng, có xác thực tài khoản qua email, trò chuyện trực tiếp, đánh giá sau giao dịch và kiểm duyệt nội dung.

## Mục tiêu

Xây dựng nền tảng web giúp sinh viên mua bán đồ cũ nhanh chóng, an toàn và đáng tin cậy. Hệ thống được phát triển lần lượt theo từng module, sau đó tích hợp, kiểm thử và đóng gói để phục vụ demo ổn định và có thể mở rộng về sau.

## Đối tượng sử dụng

| Vai trò | Nhu cầu chính |
| --- | --- |
| Người bán | Đăng tin thanh lý đồ dùng, quản lý tin và trao đổi với người mua. |
| Người mua | Tìm kiếm sản phẩm phù hợp, liên hệ người bán và đánh giá sau giao dịch. |
| Quản trị viên | Xử lý báo cáo vi phạm, kiểm duyệt nội dung và quản lý danh mục. |

## Phạm vi dự án

Hệ thống thuộc mô hình thương mại điện tử C2C (Consumer-to-Consumer), tập trung vào cộng đồng sinh viên trong một trường hoặc khu vực học tập cụ thể.

Nền tảng đóng vai trò kết nối và hỗ trợ giao dịch thông qua tin đăng, tìm kiếm, trò chuyện và đánh giá. **Thanh toán trực tuyến, thanh toán bảo chứng và vận chuyển nằm ngoài phạm vi dự án.**

## Chức năng dự kiến

### Xác thực và quản lý người dùng

- Đăng ký và đăng nhập tài khoản.
- Xác thực qua mã OTP gửi bằng email.
- Xác thực phiên làm việc bằng JWT và refresh token.
- Bảo vệ mật khẩu bằng cơ chế băm mật khẩu phù hợp.

### Quản lý tin đăng

- Tạo, xem, cập nhật và xóa tin đăng sản phẩm.
- Tải lên và thay đổi kích thước ảnh sản phẩm.
- Thay đổi trạng thái tin đăng.
- Phân loại sản phẩm theo danh mục.

### Tìm kiếm và lọc sản phẩm

- Tìm kiếm theo từ khóa.
- Lọc theo danh mục, giá và khu vực.
- Thiết lập chỉ mục dữ liệu để hỗ trợ hiệu năng tìm kiếm.

### Trò chuyện và thông báo

- Trò chuyện thời gian thực giữa người mua và người bán.
- Gửi thông báo liên quan đến hoạt động trên hệ thống.
- Sử dụng WebSocket hoặc thư viện hỗ trợ phù hợp với backend được lựa chọn.

### Đánh giá uy tín và kiểm duyệt

- Đánh giá uy tín sau giao dịch.
- Báo cáo nội dung vi phạm.
- Cung cấp trang quản trị để xử lý báo cáo và quản lý danh mục.

## Kiến trúc dự kiến

Đề xuất định hướng kiến trúc theo mô hình service-oriented với các thành phần:

| Thành phần | Vai trò |
| --- | --- |
| Frontend | Giao diện dành cho người mua, người bán và quản trị viên. |
| Backend API | Xử lý nghiệp vụ, xác thực và cung cấp API cho các module. |
| Cơ sở dữ liệu | Lưu người dùng, tin đăng, danh mục, tin nhắn và đánh giá. |
| Cache và dữ liệu tạm thời | Hỗ trợ lưu OTP có thời hạn và dữ liệu cache. |
| Giao tiếp thời gian thực | Hỗ trợ chat và thông báo. |
| Lưu trữ ảnh | Lưu và phục vụ ảnh sản phẩm. |

Các nhóm dữ liệu chính dự kiến gồm `users`, `listings`, `categories`, `messages` và `ratings`. Quan hệ, thuộc tính và ràng buộc sẽ được xác định trong ERD ở giai đoạn thiết kế.

## Công nghệ được xem xét

Phần giới thiệu công nghệ trong đề xuất đưa ra nhiều lựa chọn để tham khảo; bộ công nghệ cuối cùng sẽ được chốt trong giai đoạn thiết kế.

| Nhóm | Các lựa chọn được nêu trong đề xuất |
| --- | --- |
| Frontend | React / Next.js, Vue 3 / Nuxt, Angular |
| Backend | .NET 8 Web API (C#), Node.js / NestJS, Spring Boot (Java) |
| Cơ sở dữ liệu và nền tảng backend | PostgreSQL, MySQL, MongoDB, Supabase |
| Cache | Redis, Memcached |
| Giao tiếp thời gian thực | WebSocket, SignalR, Socket.IO |
| Đóng gói và điều phối | Docker Compose, Kubernetes |
| CI/CD | GitHub Actions, GitLab CI/CD |

Riêng kế hoạch triển khai trong đề xuất dự kiến dùng **Docker Compose** để đóng gói API, PostgreSQL, Redis và MinIO; **GitHub Actions** cho CI/CD; và **Railway** cho triển khai thử nghiệm. Đây là định hướng triển khai cần được đối chiếu khi chốt thiết kế.

## Yêu cầu phi chức năng

- **Bảo mật:** bảo vệ thông tin đăng nhập, sử dụng JWT và cơ chế bảo vệ mật khẩu phù hợp.
- **Hiệu năng:** hỗ trợ tìm kiếm và lọc hiệu quả, kết hợp chỉ mục dữ liệu.
- **Khả năng mở rộng:** tổ chức các thành phần để có thể phát triển thêm sau giai đoạn đồ án.
- **Khả năng triển khai:** đóng gói hệ thống bằng container và có quy trình build, test tự động.
- **Khả năng bảo trì:** theo dõi lỗi sau triển khai và có quy trình xử lý sự cố.

## Kế hoạch thực hiện

Dự án áp dụng quy trình **Waterfall**, với kế hoạch tổng thể trong **12 tuần (T1–T12)**. Công việc được phân rã theo WBS gồm tên dự án, các mục tiêu và các hoạt động cụ thể.

| Giai đoạn | Công việc chính | Sản phẩm bàn giao |
| --- | --- | --- |
| 1. Phân tích yêu cầu | Khảo sát nhu cầu, xác định actor, yêu cầu chức năng và phi chức năng, giới hạn phạm vi. | Tài liệu SRS; danh sách use case và actor. |
| 2. Thiết kế hệ thống | Thiết kế kiến trúc, ERD, API contract và wireframe. | Sơ đồ kiến trúc; ERD; bản nháp Swagger hoặc Postman collection; wireframe. |
| 3. Xây dựng hệ thống | Phát triển lần lượt các module xác thực, tin đăng, tìm kiếm, chat, đánh giá và kiểm duyệt. | API và giao diện cho các module; trang quản trị. |
| 4. Kiểm thử | Kiểm thử đơn vị, tích hợp, end-to-end với dữ liệu mẫu lớn và UAT với sinh viên. | Bộ kiểm thử chức năng cốt lõi; báo cáo kiểm thử và danh sách lỗi đã sửa. |
| 5. Triển khai và bảo trì | Đóng gói container, thiết lập CI/CD, triển khai thử nghiệm và theo dõi lỗi. | Hệ thống demo; pipeline build/test; kế hoạch bảo trì và xử lý sự cố. |

Phân bổ tiến độ theo từng tuần được trình bày trong Gantt chart của tài liệu đề xuất.

## Kế hoạch kiểm thử

- **Unit test và integration test:** kiểm tra các API chính của từng module.
- **End-to-end test:** kiểm tra luồng sử dụng và khả năng phối hợp giữa các module với dữ liệu mẫu lớn.
- **User Acceptance Testing (UAT):** mời một nhóm sinh viên sử dụng thử để đánh giá mức đáp ứng nhu cầu thực tế.
- Ghi nhận kết quả, sửa lỗi và tổng hợp báo cáo trước khi triển khai.

## Cài đặt và chạy dự án

Đề xuất đặt mục tiêu khởi chạy hệ thống bằng một lệnh Docker Compose sau khi hoàn thành cấu hình các service. README sẽ cần bổ sung yêu cầu môi trường, biến cấu hình, cách khởi tạo dữ liệu và lệnh chạy cụ thể khi có bản triển khai tương ứng.

## Tài liệu dự án

- [Project Proposal](Ideas/Project_Proposal.docx): tài liệu gốc mô tả bối cảnh, mục tiêu, công nghệ tham khảo, kế hoạch và tài liệu tham khảo.
- Các tài liệu dự kiến bổ sung: SRS, use case, sơ đồ kiến trúc, ERD, API design, wireframe, báo cáo kiểm thử và kế hoạch bảo trì.
