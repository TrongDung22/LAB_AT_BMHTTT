# BÁO CÁO THỰC HÀNH - AN TOÀN HỆ THỐNG THÔNG TIN

* **Họ và tên:** Hoàng Trọng Dũng
* **MSSV:** 1150080129
* **Bài thực hành:** LAB 4 - Khảo sát và đánh giá bề mặt mạng bằng Nmap

---

### 1. Môi trường thực nghiệm
* **Máy quét:** Kali Linux (IP: `192.168.56.47`)
* **Máy đích:** Metasploitable 2 (IP: `192.168.56.90`)
* **Mạng:** Host-Only Network (`192.168.56.0/24`)

### 2. Cách dựng môi trường
* Thiết lập 2 máy ảo cùng chung card mạng Host-Only trong VirtualBox.
* Cấu hình IP tĩnh/DHCP cùng dải `192.168.56.0/24`, kiểm tra thông mạng bằng `ping`.

### 3. Các tác vụ đã thực hiện
* Host discovery (`-sn`), TCP scan (`-sT`, `-sS`, `-sA`, `-sF`, `-sX`, `-sN`), UDP scan (`-sU`).
* Nhận diện dịch vụ (`-sV`), hệ điều hành (`-O`), quét tổng hợp (`-A`).
* Khai thác kịch bản NSE: `smb-os-discovery`, `smb-vuln-ms17-010`.
* Xuất báo cáo đa định dạng (`-oN`, `-oX`, `-oG`, `xsltproc` tạo HTML).
* Thực nghiệm Hardening: Tắt dịch vụ FTP (`xinetd stop`), thu hẹp cổng 21 từ `open` về `closed`.

### 4. Kết quả đánh giá
* **Trạng thái:** **PASS** (100% các kịch bản quét và hardening thực hiện thành công).

### 5. Vấn đề & Khắc phục
* **Vấn đề:** Quét toàn bộ cổng UDP tốn nhiều thời gian.
* **Khắc phục:** Giới hạn kiểm tra 20 cổng phổ biến bằng tham số `--top-ports 20` theo hướng dẫn.
