# BAOCAO_DANG_KY_TAI_KHOAN_v2

## User Story
Là một người dùng, tôi muốn có thể đăng ký tài khoản một cách dễ dàng, để tôi có thể truy cập các tính năng của ứng dụng.

## INVEST criteria
1. **Độc lập**: Người dùng có thể đăng ký tài khoản mà không cần phải thực hiện bất kỳ hành động nào khác trước đó.
2. **Có thể thảo luận**: Các yêu cầu có thể được thảo luận và thay đổi trong quá trình phát triển ứng dụng.
3. **Có giá trị**: Chức năng này mang lại giá trị cho người dùng vì họ có thể truy cập vào ứng dụng.
4. **Có thể ước lượng**: Các tính năng có thể được ước lượng thời gian phát triển.
5. **Nhỏ gọn**: Người dùng có thể hoàn thành việc đăng ký trong một vài bước đơn giản.
6. **Có thể kiểm thử**: Các tính năng có thể được kiểm thử dễ dàng để đảm bảo hoạt động đúng.

## Thin Vertical Slice
1. **Frontend**: Giao diện thân thiện với người dùng để nhập thông tin.
2. **Backend**: Xử lý lưu trữ dữ liệu người dùng vào cơ sở dữ liệu.
3. **Database & Security**: Cơ sở dữ liệu bảo mật thông tin người dùng.

## BDD scenarios
1. **Happy Path**:  
   - **Given**: Người dùng ở trang đăng ký tài khoản.  
   - **When**: Người dùng nhập thông tin hợp lệ và nhấn nút "Đăng ký".  
   - **Then**: Tài khoản được tạo thành công và người dùng được chuyển hướng đến trang chính.

2. **Unhappy Path 1**:  
   - **Given**: Người dùng ở trang đăng ký tài khoản.  
   - **When**: Người dùng không nhập địa chỉ email và nhấn nút "Đăng ký".  
   - **Then**: Hiển thị thông báo lỗi yêu cầu địa chỉ email.

3. **Unhappy Path 2**:  
   - **Given**: Người dùng ở trang đăng ký tài khoản.  
   - **When**: Người dùng nhập một mật khẩu yếu và nhấn nút "Đăng ký".  
   - **Then**: Hiển thị thông báo lỗi mật khẩu không đáp ứng yêu cầu.

4. **Unhappy Path 3**:  
   - **Given**: Người dùng ở trang đăng ký tài khoản.  
   - **When**: Người dùng nhập một địa chỉ email đã tồn tại và nhấn nút "Đăng ký".  
   - **Then**: Hiển thị thông báo lỗi địa chỉ email đã được sử dụng.

5. **Unhappy Path 4**:  
   - **Given**: Người dùng ở trang đăng ký tài khoản.  
   - **When**: Người dùng không đồng ý với các điều khoản và nhấn nút "Đăng ký".  
   - **Then**: Hiển thị thông báo lỗi cho biết cần đồng ý với các điều khoản để tiếp tục.

## Acceptance Criteria
1. Người dùng có thể nhập địa chỉ email.
2. Người dùng có thể nhập mật khẩu.
3. Mật khẩu phải chứa ít nhất 8 ký tự.
4. Người dùng nhận được thông báo lỗi khi nhập thông tin không hợp lệ.
5. Tài khoản mới được tạo và có thể đăng nhập ngay lập tức.
6. Có một liên kết để quay lại trang chính.
7. Người dùng nhận được thông báo xác nhận qua email.
8. Các trường thông tin không được để trống.
9. Thời gian phản hồi của hệ thống không vượt quá 2 giây.
10. Giao diện phải thân thiện với cả thiết bị di động và máy tính.

## Business Rules
1. Người dùng chỉ có thể tạo một tài khoản duy nhất.
2. Địa chỉ email phải duy nhất trong hệ thống.
3. Mật khẩu không được giống với địa chỉ email.
4. Thông tin người dùng phải được bảo mật hoàn toàn.
5. Người dùng chỉ có thể đăng nhập sau khi xác nhận email.

## Conclusion
Chức năng đăng ký tài khoản là một phần quan trọng trong ứng dụng, giúp người dùng truy cập vào các tính năng cần thiết. Đảm bảo rằng mọi thông số và quy trình được thực hiện đúng cách để tạo ra trải nghiệm tốt nhất cho người dùng.