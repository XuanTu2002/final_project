# Fashion Inventory Management System (MVP)

## 1. Giới thiệu

Bản MVP cho hệ thống **Quản lý hàng hóa lĩnh vực thời trang** bao gồm:

* Đăng nhập / Đăng xuất
* Quản lý danh mục hàng hóa
* Quản lý nhập xuất hàng hóa
* Báo cáo & thống kê hàng tồn kho

Ứng dụng được tách biệt thành hai phần:

* **Frontend**: React.js + Material-UI
* **Backend**: Node.js + Express.js + MongoDB (Mongoose)

## 2. Tính năng chính (MVP)

1.  **Đăng nhập / Đăng xuất** (hiện tại đã ổn nên giữ nguyên)
    * Form login với email và mật khẩu
    * Đăng kí tài khoản nếu chưa có với họ và tên, email, mật khẩu, số điện thoại và ảnh
    * Giữ trạng thái đăng nhập trên client (localStorage hoặc React Context)
    * Đơn giản, chưa có JWT, sử dụng session cơ bản hoặc mock API

2.  **Quản lý danh mục hàng hóa**
    * Tạo mới, xem, sửa, xóa danh mục
    * Tìm kiếm danh mục theo tên
    * Mỗi danh mục bao gồm: Tên danh mục, nhà sản xuất, tồn kho, mô tả, tình trạng, thao tác ( sửa và xóa)
    * Nút thêm danh mục bao gồm: Tên, nhà sản xuất và mô tả
    * Nút sửa danh mục bao gồm: Tên, nhà sản xuất và mô tả
    * Ở trên hiện tại đang là: Total Products chuyển thành tổng danh mục, Stores chuyển thành cửa hàng; Top Selling thành Xuất nhiều nhất, Low Stocks thành Hàng tồn kho thấp, Last 7 days: 7 ngày qua, Revenue thành số tiền nhập, Cost: Chi phí, Ordered: Đã đặt, Not in Stock: Hết hàng

3.  **Quản lý nhập xuất hàng hóa**
    * Nhập hàng ( hiện tại đang là logic của Purchase Details). Tạo mới và xem thiếu sửa và xóa
    * Nút tạo mới phiếu nhập gồm các nút sau: Danh mục sản phẩm (một dropdown gồm các danh mục hiện tại đã thêm ở Quản lý danh mục, hai logic này có liên quan). Số lượng nhập (người dùng nhập hoặc có Numeric Stepper từ 1 đến 999), Số tiền nhập trên một đơn vị sản phẩm ( người dùng nhập vào số tiền VND), Tổng số tiền nhập (bằng số lượng nhập nhân số tiền trên một đơn vị), Ngày nhập ( khi người dùng nhấp vào có một datepicker để chọn ngày)
    * Xuất hàng ( hiện tại đang là logic của Sales). Tạo mới và xem thiếu sửa và xóa
    * Nút tạo mới phiếu xuất gồm các nút sau: Danh mục sản phẩm (một dropdown gồm các danh mục hiện tại đã thêm ở Quản lý danh mục, hai logic này có liên quan). Số lượng xuất (người dùng nhập hoặc có Numeric Stepper từ 1 đến 999), Số tiền xuất trên một đơn vị sản phẩm ( người dùng nhập vào số tiền VND), Tổng số tiền xuất (bằng số lượng nhập nhân số tiền trên một đơn vị), Ngày xuất ( khi người dùng nhấp vào có một datepicker để chọn ngày)
    * Cập nhật tồn kho tự động theo phiếu nhập/xuất

4.  **Báo cáo & Thống kê**

    | Card                     | Mô tả                                       |
    | ------------------------ | ------------------------------------------- |
    | **Tổng danh mục** | Số lượng danh mục sản phẩm hiện có          |
    | **Sản phẩm sắp hết hàng**| count các sản phẩm có stock < 5           |
    | **Nhập hàng (tháng)** | Giá trị (VNĐ) nhập hàng trong tháng hiện tại |
    | **Xuất hàng (tháng)** | Giá trị (VNĐ) xuất hàng trong tháng hiện tại |

    * Cards đầu trang
        * Như bảng trên, hiển thị bằng `<Card>` + `<Typography>` của MUI, màu sắc theo type (primary/secondary/success/warning…).
    * Biểu đồ tròn (Pie/Donut): Phân bổ tồn kho theo danh mục
        * Mỗi lát thể hiện tổng tồn kho (hoặc giá trị tồn kho) của một danh mục.
    * Biểu đồ cột: Nhập – Xuất theo tháng
        * Trục X: Tháng (1–12)
        * Trục Y: Giá trị VNĐ
        * Hai series: “Nhập” (màu xanh) và “Xuất” (màu đỏ)

---

## 3. Tech Stack

* **Frontend**:
    * React.js
    * Material-UI (@mui/material, @mui/icons-material)
    * Axios (gọi API)
* **Backend**:
    * Node.js + Express.js
    * MongoDB (Mongoose)
    * express-session (nếu dùng session)
* **Database**:
    * MongoDB Atlas hoặc local MongoDB
    * Mongoose ORM

---