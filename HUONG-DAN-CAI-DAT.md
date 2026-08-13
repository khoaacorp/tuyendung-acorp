# HƯỚNG DẪN CÀI WEB TUYỂN DỤNG ACORP CÓ TRANG QUẢN TRỊ

Web này gồm 2 phần: **website** (trang chủ, việc làm, hoạt động...) và **trang quản trị** tại địa chỉ `/admin` để sửa nội dung không cần biết lập trình.

Nguyên lý hoạt động: nội dung web (tin tuyển dụng, bài viết, ảnh, số điện thoại...) nằm trong thư mục `content/` và `images/uploads/`. Trang quản trị sửa các file này thông qua GitHub, Netlify tự cập nhật web sau khoảng 1 phút.

---

## PHẦN 1 — ĐƯA WEB LÊN (làm 1 lần, ~30 phút)

### Bước 1: Tạo tài khoản GitHub và đưa mã nguồn lên

1. Vào **github.com** → đăng ký tài khoản (miễn phí). Ghi nhớ **tên tài khoản**.
2. Bấm nút **+** (góc phải trên) → **New repository**.
   - Repository name: `tuyendung-acorp`
   - Chọn **Private** (riêng tư)
   - Bấm **Create repository**
3. Trong trang kho vừa tạo, bấm **uploading an existing file** (hoặc **Add file → Upload files**).
4. Giải nén file zip này ra, **kéo thả TOÀN BỘ các file và thư mục bên trong** (index.html, thư mục admin, content, images) vào trang upload → bấm **Commit changes**.

### Bước 2: Sửa 1 dòng cấu hình

1. Trong kho GitHub, mở file `admin/config.yml` → bấm biểu tượng **bút chì** (Edit).
2. Tìm dòng: `repo: THAY-TEN-TAI-KHOAN/THAY-TEN-KHO`
3. Sửa thành tên của anh, ví dụ: `repo: khoaacorp/tuyendung-acorp`
4. Bấm **Commit changes**.

### Bước 3: Kết nối Netlify với GitHub

1. Vào **app.netlify.com** → **Add new site** → **Import an existing project** → chọn **GitHub** → cho phép truy cập → chọn kho `tuyendung-acorp`.
2. Các ô cài đặt để nguyên (không cần build command) → bấm **Deploy**.
3. Xong! Web chạy tại địa chỉ `ten-site.netlify.app`. Từ nay mỗi khi nội dung thay đổi trên GitHub, web tự cập nhật.

### Bước 4: Bật đăng nhập cho trang quản trị

Trang quản trị đăng nhập bằng tài khoản GitHub. Cần tạo "chìa khoá" OAuth (1 lần):

1. Vào GitHub → **Settings** (ảnh đại diện góc phải) → **Developer settings** → **OAuth Apps** → **New OAuth App**:
   - Application name: `Quan tri Acorp`
   - Homepage URL: `https://ten-site.netlify.app` (địa chỉ web của anh)
   - Authorization callback URL: `https://api.netlify.com/auth/done`
   - Bấm **Register application** → bấm **Generate a new client secret**
   - Ghi lại 2 mã: **Client ID** và **Client Secret**
2. Vào Netlify → chọn site → **Site configuration** → **Access & security** → mục **OAuth** → **Install provider** → chọn **GitHub** → dán Client ID và Client Secret → Save.

### Bước 5: Vào trang quản trị

Mở `https://ten-site.netlify.app/admin` → bấm **Login with GitHub** → cho phép. Xong!

---

## PHẦN 2 — SỬ DỤNG HẰNG NGÀY

Vào `/admin`, có 3 mục:

- **📋 Tin tuyển dụng**: thêm/sửa/xoá vị trí. Mỗi vị trí có tên, nhãn, địa điểm, lương, mô tả công việc, yêu cầu, quyền lợi (mỗi ý 1 dòng, bấm "Add" để thêm dòng).
- **📰 Bài viết hoạt động**: viết bài mới, tải ảnh lên từ máy tính, mỗi đoạn văn 1 ô. Bài và ảnh tự hiện ra trang chủ.
- **⚙️ Thông tin liên hệ**: đổi số điện thoại, email, địa chỉ, giờ làm việc.

Sau khi bấm **Publish**, chờ khoảng 1 phút để Netlify cập nhật web.

---

## PHẦN 3 — THÊM THÀNH VIÊN QUẢN TRỊ

1. Người đó tự tạo tài khoản GitHub (miễn phí).
2. Anh vào kho GitHub → **Settings** → **Collaborators** → **Add people** → nhập tên tài khoản của họ → gửi lời mời.
3. Họ chấp nhận lời mời qua email → từ đó đăng nhập được vào `/admin` để viết bài.

Muốn thu quyền: vào Collaborators xoá người đó là xong.

---

## GHI CHÚ

- **Form nộp CV** vẫn gửi về email qua FormSubmit (kích hoạt lần đầu theo hướng dẫn cũ).
- **Đổi giao diện** (màu sắc, bố cục): phần này nằm trong index.html, nhắn Claude sửa rồi thay file trên GitHub.
- Nếu vướng ở bước nào, chụp màn hình gửi Claude để được hướng dẫn tiếp.
