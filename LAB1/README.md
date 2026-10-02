# BÁO CÁO BÀI THỰC HÀNH LAB 1: BẮT GÓI TIN TELNET - SSH
**Môn học:** Thực hành An toàn Hệ thống thông tin  

---

## 1. THÔNG TIN SINH VIÊN
* **Họ và tên:** Hoàng Trọng Dũng
* **Mã số sinh viên (MSSV):** 1150080129

---

## 2. NỘI DUNG ĐÃ THỰC HIỆN
* **Mô phỏng mạng Client - Server:**
  * Dựng máy ảo Windows Server 2008 chạy trên nền tảng ảo hóa QEMU/KVM qua Virt-Manager.
  * Sử dụng máy Host Arch Linux đóng vai trò đồng thời là Client và Attacker (Wireshark capture).
  * Kết nối thông qua card mạng bridge ảo `virbr0` với dải mạng `192.168.122.0/24`.
* **Cấu hình dịch vụ trên Server:**
  * Bật tính năng Telnet Server (TCP 23) và cấp quyền cho user cá nhân trong nhóm `TelnetClients`.
  * Cài đặt OpenSSH v9.4p1 qua Cygwin Time Machine và kích hoạt dịch vụ `cygsshd` (TCP 22).
* **Phân tích lưu lượng mạng bằng Wireshark:**
  * Thực hiện phiên Telnet, trích xuất TCP Stream chứng minh username, password và các lệnh quản trị bị truyền ở dạng văn bản rõ (cleartext).
  * Thực nghiệm đổi mật khẩu dài/phức tạp trên Telnet chứng minh không gia tăng tính an toàn cho kênh truyền.
  * Thực hiện phiên OpenSSH, trích xuất TCP Stream đối sánh và chứng minh toàn bộ payload đã được mã hóa an toàn.

---

## 3. KẾT QUẢ THỰC HIỆN
* Hoàn thành 100% kịch bản thực nghiệm Telnet và SSH.
* Quay video quá trình thực hành, upload YouTube ở chế độ công khai/không công khai.
* Soạn thảo báo cáo giải quyết đầy đủ 11 câu hỏi phân tích an toàn thông tin theo yêu cầu đề bài.

---

## 4. CÁC LƯU Ý KỸ THUẬT ĐỂ CHẠY LẠI BÀI LÀM
* **Môi trường ảo hóa KVM:** Card mạng mặc định của máy ảo được nối qua bridge `virbr0`. Để bắt gói tin toàn diện từ máy Host, Wireshark phải lắng nghe trực tiếp trên interface `virbr0`.
* **Xử lý Windows Firewall:** Windows Firewall trên máy ảo Windows Server 2008 cần được tắt hoặc mở port 22, 23 để tránh hiện tượng treo kết nối SYN packet.
* **Cài đặt Cygwin OpenSSH trên Windows Server 2008:** Do Cygwin bản mới nhất đã dừng hỗ trợ nhân Windows NT 6.0/6.1, quá trình cài đặt bắt buộc phải sử dụng Cygwin Time Machine với các tham số tương thích:
  ```cmd
  setup-x86_64.exe --allow-unsupported-windows --no-verify --site [http://ctm.crouchingtigerhiddenfruitbat.org/pub/cygwin/circa/64bit/2024/01/30/231215](http://ctm.crouchingtigerhiddenfruitbat.org/pub/cygwin/circa/64bit/2024/01/30/231215)
