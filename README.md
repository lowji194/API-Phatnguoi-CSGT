# API Sử Dụng

Đây là tài liệu hướng dẫn sử dụng API để tra cứu thông tin giao thông.

## API Endpoint

Base URL: [https://theloi.io.vn/csgt/index.php](https://theloi.io.vn/csgt/index.php)

## Phương Thức Yêu Cầu

- Phương thức: GET
- Endpoint: `/csgt/index.php`

## Tham Số Query Params

| Tên Tham Số | Kiểu Dữ Liệu | Mô Tả | Ví Dụ |
|-------------|--------------|-------|-------|
| `bienso`    | String       | Biển số xe cần tra cứu. Lưu ý: cần loại bỏ khoảng trắng và ký tự đặc biệt trước khi thực hiện | `30A12345` |
| `loaixe`    | Integer      | Loại xe (1: ô tô, 2: xe máy, 3: xe điện) | `1` |
| `captcha`   | String       | Mã captcha để xác thực. Lưu ý: sử dụng apikey của ocr.space có thể không chính xác và chậm hơn, có thể sử dụng apikey của Autocaptcha.pro | `K87924392288957` |

## Ví Dụ Yêu Cầu

Dưới đây là một ví dụ về cách gửi yêu cầu GET để tra cứu thông tin biển số xe:

```
GET https://theloi.io.vn/csgt/index.php?bienso=30A12345&loaixe=1&captcha=K87924392288957
```

### Phản Hồi

API sẽ trả về thông tin liên quan đến biển số xe nếu yêu cầu hợp lệ.

#### Ví Dụ Phản Hồi Thành Công

```json
{
    "status": "success",
    "url": "https://www.csgt.vn/tra-cuu-phuong-tien-vi-pham.html?&LoaiXe=1&BienKiemSoat=29KXXXXX",
    "msg": "Có vi phạm",
    "data": [
        {
            "Biển kiểm soát": "29K-XXXXX",
            "Màu biển": "Nền mầu trắng, chữ và số màu đen",
            "Loại phương tiện": "Ô tô",
            "Thời gian vi phạm": "15:39, 30/12/2024",
            "Địa điểm vi phạm": "Đ. Kim Ngọc - Tỉnh ủy đi Sở GTVT, Phường Liên Bảo, Thành phố Vĩnh Yên, Tỉnh Vĩnh Phúc",
            "Hành vi vi phạm": "12321.5.5.a.01.Không chấp hành hiệu lệnh của đèn tín hiệu giao thông",
            "Trạng thái": "Chưa xử phạt",
            "Đơn vị phát hiện vi phạm": "Đội Cảnh sát giao thông, Trật tự - Công an thành phố Vĩnh Yên - Tỉnh Vĩnh Phúc",
            "Nơi giải quyết vụ việc": [
                "Đơn vị phát hiện vi phạm:Đội Cảnh sát giao thông, Trật tự - Công an thành phố Vĩnh Yên - Tỉnh Vĩnh Phúc",
                "1. Đội Cảnh sát giao thông, Trật tự - Công an thành phố Vĩnh Yên - Tỉnh Vĩnh Phúc",
                "Địa chỉ: TP Vĩnh Yên",
                "Số điện thoại liên hệ: 09675xxxx",
                "2. Đội Cảnh sát giao thông, Trật tự - Công an huyện Mê Linh - Thành phố Hà Nội"
            ]
        }
    ]
}
```

#### Ví Dụ Phản Hồi Thất Bại

```json
{
    "status": "error",
    "message": "Giải captcha sai quá 5 lần"
}
```

## Lưu Ý

- Đảm bảo nhập đúng mã captcha để truy cập thông tin.
- Tham số `bienso` phải là biển số xe hợp lệ và đã loại bỏ khoảng trắng và ký tự đặc biệt.
- Tham số `loaixe` phải nằm trong khoảng 1, 2, 3.

## Liên Hệ

Nếu có bất kỳ câu hỏi hoặc cần hỗ trợ, vui lòng liên hệ [email@example.com](mailto:email@example.com).
