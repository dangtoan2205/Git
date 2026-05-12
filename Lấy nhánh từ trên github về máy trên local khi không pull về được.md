Hướng dẫn xử lý trường hợp clone code về máy nhưng không thấy code của nhánh cần dùng
----

**Mô tả vấn đề**

Sau khi clone repository từ GitHub về máy:
- Repository có nhiều branch trên GitHub
- Nhưng local chỉ hiển thị branch `main`
- Khi mở project trong VS Code không thấy source code của nhánh cần làm việc

**Nguyên nhân:**
- Git chỉ clone branch mặc định (`main`)
- Các branch khác mới chỉ tồn tại dưới dạng remote branch
- Chưa được checkout về local

## Bước 1: Clone lại repository từ GitHub
```
git clone https://github.com/<username>/<repository>.git
```

> Ví dụ:
```
git clone https://github.com/dangtoan2205/qlts-new.git
```

> Di chuyển vào thư mục project:
```
cd qlts-new
```

## Bước 2: Kiểm tra toàn bộ branch hiện có
```
git branch -a
```

> Kết quả ví dụ
```
PS D:\qlts-new> git branch -a
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/dev
  remotes/origin/fea-monitor
  remotes/origin/fea-role
  remotes/origin/main
  remotes/origin/staging
  remotes/origin/teams-intergration
```

> Giải thích

Đã lấy được toàn bộ danh sách branch hiện có trên GitHub.

> Tuy nhiên:
- main là branch local hiện tại
- Các branch dạng:
```
remotes/origin/*
```

mới chỉ là remote branch trên GitHub

Chưa tồn tại trên local.

## Bước 3: Checkout branch cần dùng về local

**Ví dụ checkout branch fea-role**
```
git checkout -b fea-role origin/fea-role
```

**Ý nghĩa**
| Thành phần        | Ý nghĩa                             |
| ----------------- | ----------------------------------- |
| `-b fea-role`     | Tạo branch local mới tên `fea-role` |
| `origin/fea-role` | Lấy dữ liệu từ branch trên GitHub   |

**Kết quả**
```
PS D:\qlts-new> git checkout -b fea-role origin/fea-role
branch 'fea-role' set up to track 'origin/fea-role'.
Switched to a new branch 'fea-role'
```

**Giải thích**
- Đã tạo branch local fea-role
- Đã liên kết với branch origin/fea-role trên GitHub
- Đã chuyển sang branch mới thành công
- Source code của branch sẽ tự động xuất hiện trong VS Code

## Bước 4: Kiểm tra branch local hiện tại
```
git branch
```

**Kết quả**
```
PS D:\qlts-new> git branch
* fea-role
  main
```

**Giải thích**

Hiện tại local đã có:
- fea-role
- main

Dấu `*` thể hiện branch đang sử dụng hiện tại.

**Sau này khi muốn chuyển branch**

> Ví dụ chuyển sang branch `dev`
```
git checkout dev
```

Hoặc:
```
git switch dev
```

## Workflow chuẩn khuyến nghị
**Kiểm tra toàn bộ branch**
```
git branch -a
````

**Checkout branch lần đầu từ remote**
```
git checkout -b <branch-name> origin/<branch-name>
```

**Ví dụ:**
```
git checkout -b staging origin/staging
```

**Pull code mới nhất**
```
git pull
```

## Lưu ý quan trọng

Git không tự tạo toàn bộ branch local khi clone repository.

Sau khi clone:
- Chỉ có branch mặc định (main)
- Các branch khác cần checkout thủ công lần đầu tiên từ remote branch về local.
