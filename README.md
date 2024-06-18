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

![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/a91efec1-cfd9-4152-9930-90d3637f4929)

### 2.Thêm dữ liệu vào các bảng

-- Thêm dữ liệu vào bảng DiaDiemDuLich

INSERT INTO DiaDiemDuLich (TenDiaDiem, MoTa, DiaChi, LoaiHinhDuLich) VALUES

(N'Đà Lạt', N'Thành phố ngàn hoa', N'Lâm Đồng', N'Nghỉ dưỡng'),

(N'Hạ Long', N'Vịnh biển đẹp nhất', N'Quảng Ninh', N'Tham quan');

-- Thêm dữ liệu vào bảng KhachSan

INSERT INTO KhachSan (TenKhachSan, DiaChi, SoSao, DiaDiemID) VALUES

(N'Khách sạn Đà Lạt Palace', N'Số 12, Đường Trần Phú', 5, 1),

(N'Khách sạn Mường Thanh', N'Số 1, Đường Hạ Long', 4, 2);

-- Thêm dữ liệu vào bảng NhaHang

INSERT INTO NhaHang (TenNhaHang, DiaChi, LoaiHinhAmThuc, DiaDiemID) VALUES

(N'Nhà hàng Hoa Đà Lạt', N'Số 15, Đường Phan Bội Châu', N'Âu', 1),

(N'Nhà hàng Biển Vàng', N'Số 3, Đường Bãi Cháy', N'Hải sản', 2);

-- Thêm dữ liệu vào bảng KhachHang

INSERT INTO KhachHang (TenKhachHang, Email, SoDienThoai) VALUES

(N'Nguyễn Văn A', N'vana@gmail.com', N'0901234567'),

(N'Trần Thị B', N'thib@gmail.com', N'0912345678');


-- Thêm dữ liệu vào bảng DanhGia

INSERT INTO DanhGia (KhachHangID, DiaDiemID, SoSao, BinhLuan) VALUES

(1, 1, 5, N'Rất đẹp và thơ mộng!'),

(2, 2, 4, N'Cảnh đẹp nhưng dịch vụ chưa tốt.');

## Thiết lập chức năng
### 1.Chức năng cơ bản
1.1.Chức năng tìm kiếm thông tin

*Lấy danh sách các địa diểm du lịch:

SELECT * FROM DiaDiemDuLich;

*Lấy danh sách các khách sạn:

SELECT * FROM KhachSan WHERE DiaDiemID = (id của địa điểm cần tìm);

*Lấy danh sách các nhà hàng

	SELECT * FROM NhaHang WHERE DiaDiemID = (id của địa điểm cần tìm);
 
*Lấy danh sách đánh giá cho 1 địa điểm:

	SELECT * FROM DanhGia WHERE DiaDiemID = (id của địa điểm cần tìm);
 
*Lấy thông tin chi tiết của 1 khách hàng:

	SELECT * FROM KhachHang WHERE ID = (id của khách hàng);
 
1.2.Chức năng thêm, xóa, sửa

- Địa điểm du lịch

![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/8e0c990c-28c0-4e22-8c57-d2d9096fd8b9)

- Khách sạn

![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/8b328396-f8d0-419d-9dbc-ece655c8f5a2)

- Nhà hàng

![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/f2e64397-acad-4159-b5a8-137177b3ab28)

- Đánh giá

![image](https://github.com/TuanDat23/BTL_HQTCSDL_QuanLyDiaThongTinDiemDuLich/assets/168843736/6b052614-1553-4001-a898-2a2a5c6a221c)

### 2.Chức năng nâng cao
- Tự động cập nhật tổng số sao và số lượng đánh giá của một địa điểm du lịch khi có đánh giá mới

CREATE TRIGGER trg_UpdateReviewStats

ON DanhGia

AFTER INSERT, UPDATE, DELETE

AS

BEGIN

    -- Xử lý cho trường hợp thêm hoặc cập nhật đánh 
    
    IF EXISTS (SELECT * FROM inserted)
    
    BEGIN
    
        DECLARE @DiaDiemID INT;
	
        SELECT @DiaDiemID = DiaDiemID FROM inserted;

        DECLARE @TotalStars INT;
	
        SELECT @TotalStars = SUM(SoSao) FROM DanhGia WHERE DiaDiemID = @DiaDiemID;

        DECLARE @ReviewCount INT;
	
        SELECT @ReviewCount = COUNT(*) FROM DanhGia WHERE DiaDiemID = @DiaDiemID;

        UPDATE DiaDiemDuLich
	
        SET TongSoSao = @TotalStars, SoLuongDanhGia = @ReviewCount
	
        WHERE ID = @DiaDiemID;
	
    END;

    -- Xử lý cho trường hợp xóa đánh giá
    
    IF EXISTS (SELECT * FROM deleted)
    
    BEGIN
    
        DECLARE @DiaDiemIDDel INT;
	
        SELECT @DiaDiemIDDel = DiaDiemID FROM deleted;

        DECLARE @TotalStarsDel INT;
	
        SELECT @TotalStarsDel = SUM(SoSao) FROM DanhGia WHERE DiaDiemID = @DiaDiemIDDel;

        DECLARE @ReviewCountDel INT;
	
        SELECT @ReviewCountDel = COUNT(*) FROM DanhGia WHERE DiaDiemID = @DiaDiemIDDel;

        UPDATE DiaDiemDuLich
	
        SET TongSoSao = @TotalStarsDel, SoLuongDanhGia = @ReviewCountDel
	
        WHERE ID = @DiaDiemIDDel;
	
    END;
    
END;

- Duyệt qua các địa điểm du lịch và in ra tên địa điểm và số lượng khách sạn tại đó

CREATE PROCEDURE ListHotelsPerLocation

AS

BEGIN

    DECLARE @locationID INT;
    
    DECLARE @locationName NVARCHAR(255);

        DECLARE location_cursor CURSOR FOR
	
        SELECT ID, TenDiaDiem FROM DiaDiemDuLich;

    OPEN location_cursor;

    FETCH NEXT FROM location_cursor INTO @locationID, @locationName;

    -- Duyệt qua các địa điểm du lịch
    
    WHILE @@FETCH_STATUS = 0
    
    BEGIN
    
        -- In ra tên địa điểm và số lượng khách sạn tại đó
	
        PRINT 'Địa điểm: ' + @locationName + ' - Số lượng khách sạn: ' + CAST((SELECT COUNT(*) FROM KhachSan WHERE DiaDiemID = @locationID) AS NVARCHAR(10));

        FETCH NEXT FROM location_cursor INTO @locationID, @locationName;
	
    END;
    

    CLOSE location_cursor;
    
    DEALLOCATE location_cursor;
    
END;

- Tìm kiếm thông tin

-- Tạo một VIEW mới có tên 'View_HotelInfo'

CREATE VIEW View_HotelInfo AS

SELECT 

    ks.ID, -- ID của khách sạn
    
    ks.TenKhachSan, -- Tên của khách sạn
    
    ks.DiaChi, -- Địa chỉ của khách sạn
    
    ks.DiaDiemID, -- ID của địa điểm du lịch liên kết với khách sạn
    
    dd.TenDiaDiem, -- Tên của địa điểm du lịch
    
    ISNULL(AVG(dg.SoSao), 0) AS TrungBinhSoSao -- Tính trung bình số sao của các đánh giá, nếu không có đánh giá nào thì trả về 0
    
FROM 

    KhachSan ks -- Bảng KhachSan
    
LEFT JOIN 

    DiaDiemDuLich dd ON ks.DiaDiemID = dd.ID -- Kết nối bảng DiaDiemDuLich để lấy tên địa điểm du lịch
    
LEFT JOIN 

    DanhGia dg ON ks.ID = dg.DiaDiemID -- Kết nối bảng DanhGia để lấy các đánh giá liên quan đến khách sạn
    
GROUP BY 

    ks.ID, ks.TenKhachSan, ks.DiaChi, ks.DiaDiemID, dd.TenDiaDiem; -- Nhóm theo các cột cần thiết để tính trung bình số sao
    
GO

SELECT * 

FROM View_HotelInfo

ORDER BY TrungBinhSoSao DESC, TenKhachSan ASC;


