# Kiểm thử API với Postman

## Giới thiệu
Mục tiêu của bài tập này là thực hành kiểm thử API bằng cách sử dụng Postman. Bài tập bao gồm các bước từ việc lựa chọn một API thực tế, phân tích tài liệu API, viết các trường hợp kiểm thử, thực hiện kiểm thử và ghi lại kết quả kiểm thử.

## API Được Chọn
API được lựa chọn cho bài tập này là **OpenWeatherMap API**, một API phổ biến cung cấp dữ liệu thời tiết theo thời gian thực.

## Phân Tích Tài Liệu API
Để hiểu rõ các chức năng và điểm cuối của OpenWeatherMap API, tài liệu API đã được tham khảo:
- **Điểm cuối chính**: `https://api.openweathermap.org/data/2.5/weather`
- **Phương thức**: GET
- **Tham số bắt buộc**:
  - `q` (Tên thành phố, ví dụ: `q=Hanoi`)
  - `appid` (API key của người dùng)

## Các Trường Hợp Kiểm Thử
Các trường hợp kiểm thử chính cho API này bao gồm:
1. **Truy vấn với thành phố hợp lệ**: Kiểm thử API với tên thành phố hợp lệ để đảm bảo API trả về dữ liệu đúng.
2. **Truy vấn với thành phố không tồn tại**: Kiểm thử API với tên thành phố không tồn tại để kiểm tra cách xử lý lỗi của API.
3. **API key không hợp lệ và không có API key**: Kiểm thử API với API key không hợp lệ để đảm bảo API xử lý lỗi xác thực đúng cách và kiểm thử API mà không cung cấp API key để kiểm tra phản hồi của API.
4. **Trường hợp 4: Kiểm thử truy vấn không có mã địa lý**: Kiểm thử API với không có mã địa lý để kiểm tra phản hồi của API.

## Thực Hiện Các Trường Hợp Kiểm Thử với Postman

### Trường Hợp Kiểm Thử 1: Truy vấn với thành phố hợp lệ
- **Điểm cuối**: `https://api.openweathermap.org/data/2.5/weather?q=Hanoi&appid=8a7c5f0be154320f7be5cdd94e638411`
- **Phương thức**: GET
- **Kết quả mong đợi**: Mã trạng thái 200 và dữ liệu thời tiết cho thành phố Hanoi.

### Trường Hợp Kiểm Thử 2: Truy vấn với thành phố không tồn tại
- **Điểm cuối**: `https://api.openweathermap.org/data/2.5/weather?q=nonecity&appid=8a7c5f0be154320f7be5cdd94e638411`
- **Phương thức**: GET
- **Kết quả mong đợi**: Mã trạng thái 404 và thông báo lỗi không tìm thấy thành phố.

### Trường Hợp Kiểm Thử 3: API key không hợp lệ và không có API
- **Điểm cuối**: `https://api.openweathermap.org/data/2.5/weather?q=Hanoi&appid=invalidapikey` và `https://api.openweathermap.org/data/2.5/weather?q=Hanoi`
- **Phương thức**: GET
- **Kết quả mong đợi**: Mã trạng thái 401 và thông báo lỗi xác thực.

### Trường Hợp Kiểm Thử 4: Không có mã địa lý
- **Điểm cuối**: `https://api.openweathermap.org/data/2.5/weather?q=&appid=8a7c5f0be154320f7be5cdd94e638411`
- **Phương thức**: GET
- **Kết quả mong đợi**: Mã trạng thái 400 và thông báo không có mã địa lý.

## Kết Quả Kiểm Thử

### Trường Hợp Kiểm Thử 1
- **Mã Trạng Thái**: 200
- **Kết Quả**: Dữ liệu thời tiết chi tiết cho thành phố Hanoi.

### Trường Hợp Kiểm Thử 2
- **Mã Trạng Thái**: 404
- **Kết Quả**: Thông báo "city not found".

### Trường Hợp Kiểm Thử 3
- **Mã Trạng Thái**: 401
- **Kết Quả**: Thông báo lỗi xác thực "Invalid API key".

### Trường Hợp Kiểm Thử 4
- **Mã Trạng Thái**: 400
- **Kết Quả**: Thông báo "Nothing to geocode".

## Báo Cáo Kiểm Thử Chi Tiết

**Mục Tiêu Kiểm Thử:**
- Xác định và xác thực các phản hồi của OpenWeatherMap API dựa trên các truy vấn khác nhau.

**Phạm Vi Kiểm Thử:**
- Các điểm cuối liên quan đến việc lấy dữ liệu thời tiết của thành phố.

**Kết Quả Kiểm Thử:**
- Tất cả các trường hợp kiểm thử được thực hiện và kết quả phù hợp với mong đợi.
- API hoạt động đúng với thành phố hợp lệ và xử lý các lỗi một cách thích hợp khi cung cấp dữ liệu không hợp lệ hoặc thiếu API key.

**Khuyến Nghị:**
- API hoạt động tốt và xử lý các lỗi đúng cách. Khuyến nghị duy trì tài liệu chi tiết và cung cấp các ví dụ cụ thể để hỗ trợ người dùng API.
