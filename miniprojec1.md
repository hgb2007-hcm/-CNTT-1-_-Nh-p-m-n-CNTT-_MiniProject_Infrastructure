# HỆ THỐNG QUẢN TRỊ HẠ TẦNG & NHẬT KÝ KỸ THUẬT

## ***1. Cấu trúc Cây thư mục dự án (greentech-system/)***

Em sử dụng powershell để tạo ra cấu trúc thư mục như thế này :

CNTT1_NhapMonCNTT_MiniProject_GreenTech/
├── docs/
│   ├── README.md
│   └── srs-he-thong.docx
├── scripts/
│   └── auto_report.bat
├── data/
│   ├── log-he-thong.log
│   └── quan-ly-thiet-bi.xlsx
└── .env

## ***2. Các Modul***

***Modul 1***

Trong powershell em sử dụng câu lệnh : ***mkdir CNTT1_NhapMonCNTT_MiniProject_GreenTech; cd CNTT1_NhapMonCNTT_MiniProject_GreenTech; mkdir docs, scripts, data; New-Item -ItemType File ".env"; New-Item -ItemType File "docs/README.md", "docs/srs-he-thong.docx"; New-Item -ItemType File "scripts/auto_report.bat"; New-Item -ItemType File "data/log-he-thong.log", "data/quan-ly-thiet-bi.xlsx"*** , để tạo cấu trúc thư mục như trên 

***Modul 2***

Vì file log của trạm cảm biến IoT ngoài trang trại rất nặng (lên tới 500MB), nếu mở bằng Notepad hay đọc toàn bộ vào RAM thì máy tính sinh viên năm nhất như em sẽ đứng máy ngay lập tức. Do đó, mình viết script sử dụng lệnh lọc dòng trực tiếp qua đường ống pipe mà không làm tràn RAM.

Robot lọc log tự động được viết như sau : @echo off
chcp 65001 > nul
echo ======================================================== >> ..\backup\bao-cao-su-co.txt
echo [BAO CAO SU CO HE THONG IOT] - Ngay: %DATE% %TIME% >> ..\backup\bao-cao-su-co.txt
echo ======================================================== >> ..\backup\bao-cao-su-co.txt

REM Su dung findstr de loc nhanh cac dong CRITICAL va ERROR tu file log ma khong load toan bo vao RAM
findstr /i "CRITICAL ERROR" ..\data\log-he-thong.log >> ..\backup\bao-cao-su-co.txt

echo. >> ..\backup\bao-cao-su-co.txt
echo Da trich xuat va cap nhat log thanh cong!
pause

***Modul 3***

**Tài liệu hướng dẫn sử dụng**

# GreenTech IoT Infrastructure System

Hệ thống quản lý hạ tầng và giám sát thiết bị trạm cảm biến nông nghiệp thông minh.
## 1. Hướng dẫn chạy Script tự động lọc Log
Để quét và trích xuất các lỗi nghiêm trọng (`CRITICAL`, `ERROR`) từ tệp nhật ký hệ thống, mở Command Prompt hoặc bấm đúp vào tệp batch tại thư mục `scripts/`:
```cmd
cd scripts
auto_report.bat