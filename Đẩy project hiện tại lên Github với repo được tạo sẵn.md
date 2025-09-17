1️⃣ Khởi tạo Git trong thư mục dự án

Mở terminal tại `E:\qlts` và chạy:

```bash
git init
```

Lệnh này sẽ tạo ra một thư mục ẩn .git bên trong E:\qlts.

2️⃣ Thêm tất cả file vào vùng staging

```bash
git add .
```

3️⃣ Tạo commit đầu tiên

```bash
git commit -m "First commit"
```

4️⃣ Kết nối với GitHub remote

Vì bạn đã tạo repo trên GitHub (https://github.com/dangtoan2205/qlts.git), hãy chạy:

```bash
git remote add origin https://github.com/dangtoan2205/qlts.git
```

5️⃣ Đặt branch chính là `main`

```bash
git branch -M main
```

6️⃣ Đẩy code lên GitHub

```bash
git push -u origin main
```

✅ Sau khi xong, reload trang GitHub bạn sẽ thấy toàn bộ source đã được đẩy lên.
Nếu bạn đã từng lỡ chạy git remote add origin trước khi init và Git báo lỗi, không sao, chỉ cần chạy lại sau khi git init là được.
