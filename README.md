# Bai6_Select
Chủ đề: Câu lệnh Select
Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025

Ghi chú: Giải thích tại sao lại có SQL như vậy.
---------------------------------------------------------------BÀI LÀM---------------------------------------------------------------------
1. Import dữ liệu trong file sv_tnut.sql đưa vào sql server
Tạo database mới :
![image](https://github.com/user-attachments/assets/64f34753-1e7f-415f-b540-da1bc9a1ede4)
Mở file sv_tnut.sql và chạy :
![image](https://github.com/user-attachments/assets/2f8dfd22-93c2-458b-a76b-2b012c74e194)
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
  ```sql
INSERT INTO [dbo].[SV] ([masv], [hodem],[ten],  [ns], [lop], [sdt])
VALUES ('K225480106075', N'Nguyễn Đức Việt', N'Nam', '2004-08-06',  'K58KTP.K01', '0327408619');
```
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
![image](https://github.com/user-attachments/assets/a4683cba-f759-4389-b67f-3e589722fb73)
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
![image](https://github.com/user-attachments/assets/a8f9fc49-1d5a-4e8b-ba1a-e7412d6693b9)
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
![image](https://github.com/user-attachments/assets/89878520-d8ca-44a6-a111-b12a731a04a4)
6. nhập sql để tìm xem có những sv nào trùng tên với em?
![image](https://github.com/user-attachments/assets/95599c5b-3033-4c98-9653-34ef5c9252c9)
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
![image](https://github.com/user-attachments/assets/718e16db-5d78-4fa2-8d7b-14d7e90f0b32)
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
![image](https://github.com/user-attachments/assets/874ddb71-67e2-4b67-b3a5-a2c1984b9af5)
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
![image](https://github.com/user-attachments/assets/88088466-4c8f-4a25-a917-282cdc7f60f4)
-  WHERE lop LIKE '%KMT%'  -- Lọc các sinh viên học lớp có chứa 'KMT' (tức là ngành Kỹ thuật Máy tính)
-  COLLATE Vietnamese_CI_AS: đảm bảo sắp xếp theo chuẩn tiếng Việt có phân biệt dấu đúng thứ tự.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)
![image](https://github.com/user-attachments/assets/7d17f02e-29d0-4552-8255-c797ced61930)
-  Lọc lop LIKE '%KMT%' để lấy SV ngành KMT.
-  Với giới tính, do không có trường gioitinh, có thể dùng danh sách tên thường gặp ở nữ như 'Anh', 'Hương', 'Hạnh', 'Trang', 'Linh', 'Nhung', ... để ước lượng.
-  Vì không có giới tính, việc lọc theo tên nữ là ước lượng và không hoàn toàn chính xác.
-  Khi truy xuất thì nó không chuẩn hóa dấu nên có xuất hiện cả những tên như Dũng ,Thứ ,... những tên nghe là biết con trai
-  Có thể loại trừ những tên nam — ví dụ thêm AND ten NOT IN (...) với danh sách tên nam, cái này thì hơi mất thời gian
-  Nếu có cột gioi tinh, có thể viết đơn giản: WHERE gioitinh = N'Nữ' AND lop LIKE '%KMT%'.
