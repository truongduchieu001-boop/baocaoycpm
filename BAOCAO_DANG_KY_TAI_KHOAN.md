# BÁO CÁO YÊU CẦU PHẦN MỀM
## Web Bán Quần Áo Online - Chức Năng Đăng Ký Tài Khoản

---

## Mục Lục
1. [Tổng Quan](#tổng-quan)
2. [Phân Tích Chức Năng Đăng Ký Tài Khoản](#phân-tích-chức-năng-đăng-ký-tài-khoản)
   - 2.1. Danh Sách User Stories
   - 2.2. Đặc Tả Chức Năng
   - 2.3. Scenario
   - 2.4. Happy Path
   - 2.5. Unhappy Path
   - 2.6. Acceptance Criteria
   - 2.7. Acceptance Test
3. [Luồng Quy Tắc Nghiệp Vụ](#luồng-quy-tắc-nghiệp-vụ)
4. [Kết Luận](#kết-luận)

---

## Tổng Quan

**Người thực hiện:** Trương Đức Hiếu  
**Chủ đề:** Web bán quần áo online  
**Actor:** Guest (Khách hàng chưa đăng nhập / chưa có tài khoản)  

Chức năng Đăng ký tài khoản cho phép khách truy cập website tạo tài khoản thành viên mới để sử dụng các dịch vụ như mua hàng, theo dõi đơn hàng, quản lý thông tin cá nhân và nhận ưu đãi từ hệ thống.

**Tầm quan trọng:** Đây là chức năng quan trọng giúp chuyển đổi Guest thành khách hàng chính thức của website, góp phần tăng cơ sở khách hàng và nâng cao tỷ lệ chuyển đổi (conversion rate).

---

## Phân Tích Chức Năng Đăng Ký Tài Khoản

### 2.1. Danh Sách User Stories

| ID | User Story |
|---|---|
| US1 | Là một Guest, tôi muốn đăng ký tài khoản để có thể mua hàng trên website. |
| US2 | Là một Guest, tôi muốn đăng ký nhanh bằng email và mật khẩu để tiết kiệm thời gian. |
| US3 | Là một Guest, tôi muốn nhận thông báo sau khi đăng ký thành công để biết tài khoản đã được tạo. |

---

### 2.2. Đặc Tả Chức Năng

| Thông Tin | Chi Tiết |
|---|---|
| **Tên chức năng** | Đăng ký tài khoản |
| **Actor** | Guest |
| **Mô tả** | Guest nhập thông tin cá nhân để tạo tài khoản mới trên hệ thống. |
| **Điều kiện trước** | Người dùng chưa có tài khoản. |
| **Điều kiện sau** | Tài khoản mới được tạo thành công và lưu vào cơ sở dữ liệu. |

---

### 2.3. Scenario (Kịch Bản Kèm Hoàn Cảnh)

Một khách hàng mới tên **Vy** truy cập website bán quần áo online và muốn mua áo khoác đang giảm giá. Để thực hiện thanh toán và nhận ưu đãi thành viên, Vy chọn chức năng đăng ký tài khoản mới.

---

### 2.4. Happy Path (Kịch Bản Thành Công)

1. Guest truy cập website.
2. Chọn nút **Đăng ký**.
3. Hệ thống hiển thị form đăng ký.
4. Guest nhập họ tên, email, số điện thoại, mật khẩu.
5. Nhấn nút **Tạo tài khoản**.
6. Hệ thống kiểm tra thông tin hợp lệ.
7. Tạo tài khoản thành công.
8. Hiển thị thông báo đăng ký thành công.

---

### 2.5. Unhappy Path (Kịch Bản Lỗi)

#### Trường Hợp 1: Thiếu Thông Tin
- Guest bỏ trống họ tên hoặc email.
- Hệ thống báo lỗi yêu cầu nhập đầy đủ.

#### Trường Hợp 2: Email Sai Định Dạng
- Guest nhập email không hợp lệ.
- Hệ thống báo lỗi email không đúng định dạng.

#### Trường Hợp 3: Email Đã Tồn Tại
- Guest nhập email đã đăng ký trước đó.
- Hệ thống báo email đã được sử dụng.

#### Trường Hợp 4: Mật Khẩu Quá Ngắn
- Guest nhập mật khẩu dưới 6 ký tự.
- Hệ thống báo mật khẩu không hợp lệ.

---

### 2.6. Acceptance Criteria (Tiêu Chí Chấp Nhận)

| Mã AC | Tiêu Chí Chấp Nhận |
|---|---|
| AC01 | Người dùng phải nhập đầy đủ họ tên, email và mật khẩu. |
| AC02 | Email phải đúng định dạng. |
| AC03 | Mỗi email chỉ được đăng ký một tài khoản. |
| AC04 | Mật khẩu tối thiểu 6 ký tự. |
| AC05 | Sau khi đăng ký thành công phải hiển thị thông báo. |
| AC06 | Tài khoản mới phải được lưu vào hệ thống. |

---

### 2.7. Acceptance Test (Kiểm Thử Chấp Nhận)

| Test Case | Dữ Liệu Nhập | Kết Qu�� Mong Đợi | Trạng Thái |
|---|---|---|---|
| TC01 | Bỏ trống email | Báo lỗi bắt buộc nhập email | ✓ |
| TC02 | Nhập email sai định dạng (vd: abc@) | Báo lỗi email không hợp lệ | ✓ |
| TC03 | Nhập email đã tồn tại | Báo lỗi email đã được sử dụng | ✓ |
| TC04 | Nhập mật khẩu 4 ký tự | Báo lỗi mật khẩu quá ngắn | ✓ |
| TC05 | Nhập đúng toàn bộ thông tin | Đăng ký thành công | ✓ |

---

## Luồng Quy Tắc Nghiệp Vụ

### Business Rules

#### Quy Tắc 1: Trùng Email
- Hệ thống không cho phép hai tài khoản dùng chung một email.
- **Mục đích:** Bảo vệ tính duy nhất của tài khoản và phòng chống gian lận.

#### Quy Tắc 2: Bảo Mật Mật Khẩu
- Mật khẩu phải được mã hóa (hash) trước khi lưu cơ sở dữ liệu.
- **Mục đích:** Bảo vệ thông tin nhạy cảm của người dùng.
- **Phương pháp:** Sử dụng thuật toán mã hóa mạnh (bcrypt, PBKDF2, v.v.)

#### Quy Tắc 3: Xác Thực Dữ Liệu
- Email phải đúng cấu trúc: `[username]@[domain].[extension]`
- Số điện thoại chỉ chứa số (và dấu + cho số quốc tế).
- Họ tên không được chứa ký tự đặc biệt.
- **Mục đích:** Đảm bảo chất lượng dữ liệu trong hệ thống.

#### Quy Tắc 4: Thông Báo
- Sau khi đăng ký thành công phải gửi thông báo hoặc chuyển sang trang đăng nhập.
- Email xác nhận có thể được gửi cho người dùng.
- **Mục đích:** Cung cấp phản hồi rõ ràng cho người dùng và xác minh email hợp lệ.

---

## Kết Luận

Chức năng **Đăng ký tài khoản** là một tính năng thiết yếu cho website bán quần áo online. Việc thiết kế chi tiết với các test case và acceptance criteria rõ ràng sẽ giúp đảm bảo chất lượng phần mềm và cải thiện trải nghiệm người dùng.

