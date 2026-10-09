# Lab 2: Thiết Kế Giao Diện XML & ViewBinding

Dự án bài tập **Lab 2** môn Lập trình Di động Android bằng ngôn ngữ Kotlin.

---

## 👤 Thông tin sinh viên

- **Họ và tên:** Đỗ Minh Khoa
- **Mã số sinh viên (MSSV):** 2500114713
- **Lớp / Trường:** VLSC

![Demo Lab 2](lab2.png)

---

## 🚀 Nội dung thực hành trong Lab 2
Dự án tập trung vào việc thiết kế giao diện linh hoạt (responsive) và xử lý sự kiện với ViewBinding:

1. **Thiết kế giao diện bằng ConstraintLayout**:
   - Sử dụng `ConstraintLayout` phẳng (không lồng ghép Layout) để tối ưu hiệu năng cho màn hình Đăng nhập và Hồ sơ.
   - Kết hợp `Guideline` và `DimensionRatio` (tỉ lệ 1:1) để căn chỉnh Avatar, chia đều các thành phần (Chains) giúp giao diện hiển thị tốt trên mọi kích thước màn hình (điện thoại nhỏ, lớn và khi xoay ngang).

2. **Áp dụng ViewBinding**:
   - Khai báo và kích hoạt `viewBinding` trong tệp `build.gradle.kts`.
   - Sử dụng các lớp tự sinh (`ActivityLoginBinding`, `ActivityProfileBinding`) để tương tác an toàn với các View mà không cần sử dụng `findViewById()`.

3. **Kiểm tra tính hợp lệ dữ liệu (Validation)**:
   - Xử lý các điều kiện dữ liệu đầu vào:
     - Dữ liệu bị bỏ trống (hiển thị `Toast`).
     - Định dạng email không hợp lệ (kiểm tra bằng `Patterns.EMAIL_ADDRESS`).
     - Mật khẩu quá ngắn (gắn cảnh báo `error` ngay trên ô `EditText`).

4. **Điều hướng và Truyền dữ liệu (Intent)**:
   - Điều hướng (chuyển màn hình) từ `LoginActivity` sang `ProfileActivity` sau khi xác thực thành công.
   - Gói và truyền dữ liệu (`EXTRA_EMAIL`) qua `Intent` để hiển thị trên màn hình Profile, kết hợp cấu hình `AndroidManifest.xml` chính xác cho các `Activity`.

---

## 📁 Cấu trúc dự án

```text
lab2_layout_viewbinding/
├── src/
│   ├── main/
│   │   ├── java/vn/edu/vlsc/vneduvlsclab2/
│   │   │   ├── LoginActivity.kt         # Xử lý logic đăng nhập (Kiểm tra dữ liệu)
│   │   │   └── ProfileActivity.kt       # Xử lý logic hồ sơ người dùng (Nhận Intent)
│   │   ├── res/
│   │   │   ├── layout/
│   │   │   │   ├── activity_login.xml   # Cấu trúc giao diện Đăng nhập
│   │   │   │   └── activity_profile.xml # Cấu trúc giao diện Hồ sơ (Profile)
│   │   │   └── values/
│   │   │       └── strings.xml          # Quản lý chuỗi đa ngôn ngữ (không Hardcode)
│   │   └── AndroidManifest.xml          # Nơi đăng ký Activity chính (Launcher)
│   └── test/
└── build.gradle.kts                     # Cấu hình Gradle (ViewBinding, SDK versions)
```

---

## 🛠️ Yêu cầu môi trường & Cách chạy

- **Android Studio:** Jellyfish / Koala / Ladybug hoặc mới hơn.
- **JDK:** OpenJDK 11 / 17 trở lên.
- **Android SDK:** Compile SDK 34-37, Min SDK 24.

### Các bước chạy dự án:
1. Mở dự án trong **Android Studio**.
2. Chờ Gradle hoàn tất quá trình Sync (`Gradle Sync`).
3. Chọn thiết bị giả lập (Emulator) hoặc thiết bị thật kết nối qua ADB.
4. Chọn đúng module `lab2_layout_viewbinding` trên thanh công cụ.
5. Nhấn **Run** (`Shift + F10` hoặc nút ▶️) để khởi chạy ứng dụng.
6. **Kiểm thử 4 kịch bản**:
   - Bấm nút đăng nhập khi để trống dữ liệu.
   - Nhập email sai định dạng (vd: `abc`).
   - Nhập mật khẩu dưới 6 ký tự.
   - Nhập thông tin chuẩn và bấm Đăng nhập (chuyển qua giao diện xem Hồ sơ).