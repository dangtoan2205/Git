📘 HƯỚNG DẪN GITHUB: MAIN (PRODUCTION) + DEV (DEVELOPMENT) + KHÓA MAIN
---

🎯 MỤC TIÊU
- `main` = production (nhánh chính)
- `dev` = môi trường phát triển
- Không được push trực tiếp vào `main`
- Chỉ được merge vào `main` thông qua **Pull Request**


## 1️⃣ TẠO REPOSITORY TRÊN GITHUB
1. Truy cập GitHub
2. Bấm **New repository**
3. Nhập tên repo (ví dụ: `request-page`)
4. Chọn **Public/Private**
5. Bấm Create repository

👉 Copy URL repo (HTTPS):

```
https://github.com/<username>/<repo>.git
```

## 2️⃣ GẮN GIT VÀO PROJECT LOCAL
```
cd E:\request-page
```

**Nếu chưa có git**
```
git init
```

**Thêm remote**
```
git remote add origin https://github.com/<username>/<repo>.git
```

**Nếu đã có remote**
```
git remote -v
```

## 3️⃣ TẠO NHÁNH MAIN VÀ PUSH LÊN GITHUB (nếu chưa có nhánh main)
```
git branch -M main
git add .
git commit -m "Initial project"
git push -u origin main
```

## 4️⃣ TẠO NHÁNH DEV
```
git checkout -b dev
git push -u origin dev
```

👉 Sau bước này GitHub sẽ có:
- main
- dev

## 5️⃣ ĐỔI DEFAULT BRANCH = MAIN

Vào GitHub:

Settings → Branches → Default branch → chọn `main`

**6️⃣ KHÓA NHÁNH MAIN (QUAN TRỌNG NHẤT)**

Vào:

Settings → Rules → Rulesets → Add branch ruleset

**Cấu hình**

**Ruleset name**
```
protect-main
```

**Enforcement status**
```
Active
```

**Target branches**

Chọn:
```
Include by pattern
```
Nhập:
```
main
```

**Bypass list**

👉 Để trống

## 7️⃣ CẤU HÌNH RULES

**Bật các mục sau**

✔ Require a pull request before merging 

✔ Restrict updates 

✔ Restrict deletions 

✔ Block force pushes

## 8️⃣ CẤU HÌNH PULL REQUEST

- Required approvals: `0`

👉 Repo cá nhân không cần reviewer

## 9️⃣ HOÀN TẤT

Bấm:
```
Create
```

## 🔟 WORKFLOW LÀM VIỆC

**Làm việc trên dev**
```
git checkout dev
```

**Code xong**
```
git add .
git commit -m "update"
git push origin dev
```

**Tạo Pull Request**

GitHub → Pull requests → New pull request

- base: main
- compare: dev

**Merge**

👉 Merge PR → code vào main

---
**⚠️ NGUYÊN TẮC QUAN TRỌNG**

❌ Không push trực tiếp vào main

❌ Không force push main

✔ Luôn qua Pull Request


