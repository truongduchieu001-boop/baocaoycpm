# BÁO CÁO YÊU CẦU PHẦN MỀM
## Web Bán Quần Áo Online - Chức Năng Đăng Ký Tài Khoản

---

## Mục Lục
1. [Tổng Quan](#tổng-quan)
2. [User Story & INVEST](#user-story--invest)
3. [Thin Vertical Slice](#thin-vertical-slice)
4. [Kịch Bản BDD](#kịch-bản-bdd)
5. [Acceptance Criteria](#acceptance-criteria)
6. [Quy Tắc Nghiệp Vụ](#quy-tắc-nghiệp-vụ)

---

## Tổng Quan

**Người thực hiện:** Trương Đức Hiếu  
**Chủ đề:** Web bán quần áo online  
**Actor:** Guest (Khách hàng chưa đăng nhập / chưa có tài khoản)

Chức năng Đăng ký tài khoản cho phép khách truy cập website tạo tài khoản thành viên mới để sử dụng các dịch vụ như mua hàng, theo dõi đơn hàng, quản lý thông tin cá nhân.

---

## User Story & INVEST

### User Story 
**Là một khách hàng mới, tôi muốn đăng ký tài khoản để có thể mua hàng trên website**

### Đánh giá Tiêu Chí INVEST

| Tiêu Chí | Đánh Giá | Giải Thích |
|---------|---------|-----------|
| **I - Independent (Độc lập)** | ✅ | US1 không phụ thuộc vào các user story khác |
| **N - Negotiable (Có thể thảo luận)** | ✅ | Có thể thảo luận chi tiết các trường dữ liệu |
| **V - Valuable (Có giá trị)** | ✅ | Mang lại giá trị trực tiếp cho khách hàng |
| **E - Estimable (Có thể ước lượng)** | ✅ | Có thể ước lượng được trong khoảng 3-5 ngày |
| **S - Small (Nhỏ gọn)** | ✅ | Có thể hoàn thành trong 1 sprint (2 tuần) |
| **T - Testable (Có thể kiểm thử)** | ✅ | Có acceptance criteria rõ ràng |

---

## Thin Vertical Slice

Chức năng đăng ký được chia thành 3 lát cắt ngang hoàn chỉnh:

### Lát Cắt 1: Giao Diện Frontend (UI Layer)
- Hiển thị form đăng ký với các trường: Họ tên, Email, Số điện thoại, Mật khẩu
- Validate dữ liệu phía client (real-time validation)
- Hiển thị thông báo lỗi/thành công
- Nút "Đăng ký" và "Hủy"

### Lát Cắt 2: Logic Backend (Business Logic Layer)
- Nhận dữ liệu từ frontend qua API endpoint `/api/auth/register`
- Validate lại dữ liệu phía server
- Kiểm tra email đã tồn tại chưa
- Mã hóa (hash) mật khẩu
- Tạo record user mới

### Lát Cắt 3: Database & Security (Data Layer)
- Lưu user vào bảng `users` trong database
- Áp dụng mã hóa mật khẩu (bcrypt)
- Gửi email xác nhận đến người dùng
- Ghi log hoạt động

---
 ## Kịch Bản BDD

### Scenario 1: Đăng Ký Thành Công (Happy Path)

Feature: Đăng Ký Tài Khoản
  
  
  Scenario : Khách hàng đăng ký tài khoản thành công
   
    Given: Khách hàng chưa có tài khoản
    And: Khách hàng đang ở trang đăng ký
    And: Form đăng ký được hiển thị đầy đủ
    
    When: Khách hàng nhập họ tên: "Nguyễn Văn A"
    And: Khách hàng nhập email: "vana@example.com"
    And: Khách hàng nhập số điện thoại: "0987654321"
    And: Khách hàng nhập mật khẩu: "SecurePass123"
    And: Khách hàng nhấn nút "Đăng Ký"
    
    Then: Hệ thống kiểm tra thông tin hợp lệ
    And: Tài khoản được tạo thành công
    And: Email xác nhận được gửi tới "vana@example.com"
    And: Khách hàng thấy thông báo "Đăng ký thành công! Vui lòng kiểm tra email."
    And: Khách hàng được chuyển hướng tới trang đăng nhập
 Scenario 2: Thiếu Thông Tin (Unhappy Path)  
  
   
   Scenario: Khách hàng bỏ trống email
   
    Given: Khách hàng ở trang đăng ký
    
    When: Khách hàng bỏ trống trường email
    And: Khách hàng nhấn nút "Đăng Ký"
    
    Then: Hệ thống hiển thị thông báo lỗi: "Email không được để trống"
    And: Form đăng ký vẫn được giữ nguyên
    And: Khách hàng có thể nhập lại email

Scenario 3: Email Sai Định Dạng (Unhappy Path)

 
 Scenario: Khách hàng nhập email sai định dạng
   
    Given: Khách hàng ở trang đăng ký
    
    When: Khách hàng nhập email: "vana.example.com" (không có @)
    And: Khách hàng nhấn nút "Đăng Ký"
    
    Then: Hệ thống hiển thị thông báo lỗi: "Email không đúng định dạng"
    And: Form đăng ký vẫn được giữ nguyên

 Scenario 4: Email Đã Tồn Tại (Unhappy Path)
  
   
   Scenario: Khách hàng nhập email đã được đăng ký
   
    Given: Khách hàng ở trang đăng ký
    And: Email "vana@example.com" đã tồn tại trong hệ thống
    
    When: Khách hàng nhập email: "vana@example.com"
    And: Khách hàng nhấn nút "Đăng Ký"
    
    Then: Hệ thống kiểm tra và phát hiện email trùng
    And: Hệ thống hiển thị thông báo lỗi: "Email này đã được sử dụng"
    And: Form đăng ký vẫn được giữ nguyên

 Scenario 5: Mật Khẩu Quá Ngắn (Unhappy Path)
 
  
  Scenario: Khách hàng nhập mật khẩu quá ngắn
   
    Given: Khách hàng ở trang đăng ký
    
    When: Khách hàng nhập mật khẩu: "123456" (6 ký tự)
    And: Khách hàng nhấn nút "Đăng Ký"
    
    Then: Hệ thống kiểm tra độ dài mật khẩu
    And: Hệ thống hiển thị thông báo lỗi: "Mật khẩu phải tối thiểu 8 ký tự"
    And: Form đăng ký vẫn được giữ nguyên

  ## Acceptance Criteria
     Mã AC	   Tiêu Chí Chấp Nhận

  
        AC01	Người dùng phải nhập đầy đủ: Họ tên, Email, Số điện thoại, Mật khẩu
        AC02	Email phải đúng định dạng: [username]@[domain].[extension]
        AC03	Mỗi email chỉ được đăng ký một tài khoản duy nhất
        AC04	Mật khẩu tối thiểu 8 ký tự (yêu cầu hoa, thường, số, ký tự đặc biệt)
        AC05	Số điện thoại phải là số hợp lệ (10-11 chữ số)
        AC06	Sau khi đăng ký thành công phải hiển thị thông báo rõ ràng
        AC07	Email xác nhận phải được gửi tới người dùng
        AC08	Tài khoản mới phải được lưu vào database
        AC09	Mật khẩu phải được mã hóa (hash) trước lưu
        AC10	Khách hàng được chuyển hướng tới trang đăng nhập sau khi thành công
    

 ## Quy Tắc Nghiệp Vụ


Quy Tắc 1: Email Duy Nhất
   
    Nội dung: Hệ thống không cho phép hai tài khoản dùng chung một email
    Mục đích: Bảo vệ tính duy nhất của tài khoản, phòng chống gian lận
    Thực hiện: Kiểm tra email trong database trước khi tạo account mới

Quy Tắc 2: Mật Khẩu Mạnh
    
      Nội dung: Mật khẩu phải chứa ít nhất 8 ký tự: chữ hoa, chữ thường, số, ký tự đặc biệt
      Mục đích: Bảo vệ tài khoản khỏi tấn công brute-force
      Thực hiện: Validate mật khẩu trên server trước lưu vào database
Quy Tắc 3: Bảo Mật Dữ Liệu
      
      Nội dung: Mật khẩu phải được mã hóa (hash) trước khi lưu cơ sở dữ liệu
      Mục đích: Bảo vệ thông tin nhạy cảm của người dùng
      Phương pháp: Sử dụng thuật toán bcrypt hoặc PBKDF2
Quy Tắc 4: Xác Thực Email
      
      Nội dung: Sau khi đăng ký thành công phải gửi email xác nhận
      Mục đích: Cung cấp phản hồi rõ ràng cho người dùng, xác minh email hợp lệ
      Thực hiện: Gửi email qua Email Service (SendGrid, Mailgun, v.v.)
Quy Tắc 5: Xác Thực Dữ Liệu
      
      Họ tên: Không được chứa ký tự đặc biệt, độ dài 2-100 ký tự
      Số điện thoại: Chỉ chứa số (0-9) và dấu + cho số quốc tế
      Email: Định dạng chuẩn RFC 5322
      Mục đích: Đảm bảo chất lượng dữ liệu trong hệ thống
