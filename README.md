# QUẢN LÝ HỆ THỐNG THÔNG TIN ĐỊA ĐIỂM DU LỊCH
- Tác giả: Vi Tuấn Đạt
- MSSV: K215480106088
- Lớp: K57KMT
- Ngày làm: 2024-06-13
## Chức Năng Cơ Bản
### 1. Quản lý
1.1.Quản Lý Địa Điểm Du Lịch
- Thêm địa điểm du lịch: Cho phép thêm mới một địa điểm du lịch vào cơ sở dữ liệu
- Sửa thông tin địa điểm du lịch: Cho phép chỉnh sửa thông tin của một địa điểm du lịch đã tồn tại
- Xóa địa điểm du lịch: Cho phép xóa một địa điểm du lịch khỏi cơ sở dữ liệu
- Xem danh sách địa điểm du lịch: Hiển thị danh sách tất cả các địa điểm du lịch

1.2. Quản Lý Khách Sạn 
- Thêm khách sạn: Cho phép thêm mới một khách sạn vào cơ sở dữ liệu
- Sửa thông tin khách sạn: Cho phép chỉnh sửa thông tin của một khách sạn đã tồn tại
- Xóa khách sạn: Cho phép xóa một khách sạn khỏi cơ sở dữ liệu
- Xem danh sách khách sạn: Hiển thị danh sách tất cả các khách sạn

1.3. Quản Lý Nhà Hàng
- Thêm nhà hàng: Cho phép thêm mới một nhà hàng vào cơ sở dữ liệu
- Sửa thông tin nhà hàng: Cho phép chỉnh sửa thông tin của một nhà hàng đã tồn tại
- Xóa nhà hàng: Cho phép xóa một nhà hàng khỏi cơ sở dữ liệu
- Xem danh sách nhà hàng: Hiển thị danh sách tất cả các nhà hàng

1.4. Quản Lý Đánh Giá
- Thêm đánh giá: Cho phép thêm mới một đánh giá từ khách hàng về địa điểm du lịch
- Sửa thông tin đánh giá: Cho phép chỉnh sửa thông tin của một đánh giá đã tồn tại
- Xóa đánh giá: Cho phép xóa một đánh giá khỏi cơ sở dữ liệu
- Xem danh sách đánh giá: Hiển thị danh sách tất cả các đánh giá

1.5. Quản Lý Khách Hàng
- Thêm khách hàng: Cho phép thêm mới một khách hàng vào cơ sở dữ liệu
- Sửa thông tin khách hàng: Cho phép chỉnh sửa thông tin của một khách hàng đã tồn tại
- Xóa khách hàng: Cho phép xóa một khách hàng khỏi cơ sở dữ liệu.
- Xem danh sách khách hàng: Hiển thị danh sách tất cả các khách hàng

### 2. Chức Năng Truy Vấn
- Tìm kiếm địa điểm du lịch theo tên hoặc loại hình du lịch
- Tìm kiếm khách sạn hoặc nhà hàng theo địa điểm du lịch
- Xem chi tiết đánh giá của một địa điểm du lịch cụ thể
- Xem chi tiết thông tin khách hàng
### 3. Chức Năng Nâng Cao
3.1. Trigger
- Cập nhật tổng số sao và số lượng đánh giá: Tự động cập nhật tổng số sao và số lượng đánh giá của một địa điểm du lịch khi có đánh giá mới được thêm vào hoặc khi một đánh giá bị xóa hoặc chỉnh sửa.

3.2. Cursor
- Duyệt qua các địa điểm du lịch: Tạo thủ tục lưu trữ để duyệt qua các địa điểm du lịch và thực hiện các tính toán tổng hợp như số lượng khách sạn hoặc nhà hàng tại mỗi địa điểm.

3.3. Báo Cáo và Thống Kê
- Báo cáo địa điểm du lịch phổ biến: Tạo báo cáo hiển thị các địa điểm du lịch phổ biến dựa trên số lượng đánh giá và điểm số trung bình.
## Thiết kế chương trình trong SQL
### 1. Tạo các bảng
Bảng KhachHang (Phải tạo đầu tiên để các bảng khác tham chiếu tới)
- ID🔑: Khóa chính được sử dụng để xác định mỗi khách hàng một cách duy nhất, tự tăng.
- TenKhachHang: Tên khách hàng được đặt là NOT NULL để đảm bảo mỗi khách hàng được lưu trữ đều có thông tin tên. Điều này cực kỳ quan trọng để có thể phân biệt và quản lý các khách hàng.
- Email: Email của khách hàng.
- SoDienThoai: Số điện thoại của khách hàng.
![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/4bccf9e6-bc3c-42e9-b17c-32b969ba51b6)
  
Bảng DiaDiemDuLich
- ID🔑: Khóa chính, tự tăng.
- TenDiaDiem: Tên địa điểm du lịch là thông tin cần thiết và được đánh dấu là NOT NULL để đảm bảo tính chính xác và đầy đủ của dữ liệu.
- MoTa: Mô tả về địa điểm.
- DiaChi: Địa chỉ địa điểm.
- LoaiHinhDuLich: Loại hình du lịch (nghỉ dưỡng, tham quan, ...).
![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/bf0754f9-8ea6-4529-86b4-751b0b60bcb9)

Bảng KhachSan
- ID🔑: Khóa chính, tự tăng.
- TenKhachSan: Tên khách sạn được đánh dấu là NOT NULL để đảm bảo tính duy nhất của dữ liệu.
- DiaChi: Địa chỉ khách sạn.
- SoSao: Số sao của khách sạn.
- DiaDiemID🔑: Là khóa ngoại (FOREIGN KEY) tham chiếu đến ID của bảng DiaDiemDuLich. Điều này thiết lập mối quan hệ giữa các bảng và cho phép truy cập thông tin về địa điểm du lịch liên quan tới từng khách sạn và nhà hàng.
![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/fa99a22a-75aa-4c9e-9272-5639b64e98d6)

Bảng NhaHang
- ID🔑: Khóa chính, tự tăng.
- TenNhaHang: Tên nhà hàng được đánh dấu là NOT NULL để đảm bảo tính duy nhất của dữ liệu.
- DiaChi: Địa chỉ nhà hàng.
- LoaiHinhAmThuc: Loại hình ẩm thực (Âu, Á, Hải sản, ...).
- DiaDiemID🔑:  Là khóa ngoại (FOREIGN KEY) tham chiếu đến ID của bảng DiaDiemDuLich. Điều này thiết lập mối quan hệ giữa các bảng và cho phép truy cập thông tin về địa điểm du lịch liên quan tới từng khách sạn và nhà hàng.
![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/0e1d530f-2396-4cc1-b8d1-89e7147d47da)

Bảng DanhGia
- ID🔑: Khóa chính, tự tăng.
- KhachHangID🔑: Là khóa ngoại (FOREIGN KEY) tham chiếu đến ID của bảng KhachHang. Điều này thiết lập mối quan hệ giữa bảng DanhGia.
- DiaDiemID🔑: Là khóa ngoại (FOREIGN KEY) tham chiếu đến ID của bảng DiaDiemDuLich. Điều này thiết lập mối quan hệ giữa các bảng và cho phép truy cập thông tin về địa điểm du lịch liên quan tới từng khách sạn và nhà hàng.
- SoSao: Số sao đánh giá.
- BinhLuan: Bình luận của khách hàng.
![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/37720870-2e99-43db-935c-ab8077953198)

Sơ đồ thực thể liên kết

###. Thiết lập chức năng
