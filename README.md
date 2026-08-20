# Phân tích Hiệu quả Chiến dịch Quảng cáo Mạng xã hội

**Bộ dữ liệu:** Social Media Advertisement Performance – Kaggle
**Công cụ:** Power BI, Power Query, DAX


## 1. Tổng quan

Dự án phân tích hiệu quả quảng cáo trên các nền tảng mạng xã hội, tập trung vào **chi phí, doanh thu, ROAS, phễu chuyển đổi và độ chính xác của nhắm mục tiêu**.

Quy trình thực hiện:

* Làm sạch và biến đổi dữ liệu bằng Power Query.
* Xây dựng mô hình dữ liệu **Star Schema** gồm 1 bảng Fact và 3 bảng Dimension.
* Xây dựng các chỉ số KPI bằng DAX.
* Thiết kế báo cáo Power BI với tính năng Drill-through và Tooltip.

## 2. Mô hình dữ liệu

| Bảng          | Vai trò   | Mô tả                                                                  |
| ------------- | --------- | ---------------------------------------------------------------------- |
| `ad_events`   | Fact      | Ghi nhận các sự kiện Impression, Click, Purchase, Like, Comment, Share |
| `ads`         | Dimension | Thông tin quảng cáo và cấu hình nhắm mục tiêu                          |
| `campaigns`   | Dimension | Thông tin chiến dịch và ngân sách                                      |
| `users_clean` | Dimension | Thông tin người dùng đã được loại bỏ dữ liệu trùng lặp                 |

Quan hệ chính:

`campaigns (1) → (n) ads (1) → (n) ad_events ← (n) users_clean (1)`

## 3. Các chỉ số chính

* **ROAS:** Tỷ suất hoàn vốn chi tiêu quảng cáo.
* **CTR:** Tỷ lệ nhấp chuột.
* **Tỷ lệ chuyển đổi.**
* **Tỷ lệ thất thoát:** Đánh giá mức độ sụt giảm qua từng bước của phễu chuyển đổi.
* **Ngân sách phân bổ:** Phân bổ ngân sách chiến dịch cho từng quảng cáo.
* **Tỷ lệ khớp / không khớp Targeting.**
* **Tỷ lệ tương tác ngoài nhóm mục tiêu.**
* ****
* **Doanh thu và ngân sách theo nền tảng.**

## 4. Nội dung báo cáo

### Trang 1 – Tổng quan thu hút người dùng

* Tổng quan ngân sách, doanh thu và ROAS.
* So sánh hiệu quả giữa các nền tảng.
* Phân tích doanh thu theo nhóm người dùng và quốc gia.
* Đánh giá độ chính xác của nhắm mục tiêu.

### Trang 2 – Hiệu suất chiến dịch

* Phân tích phễu chuyển đổi.
* So sánh CTR và Click theo nền tảng, giới tính và loại quảng cáo.
* Xác định các điểm thất thoát trong phễu.
* Phân tích mức độ khớp / không khớp với nhóm mục tiêu.

### Trang 3 – Chi tiết chiến dịch

* Drill-through từ chiến dịch đến từng quảng cáo.
* Phân tích chi tiết phễu chuyển đổi của từng quảng cáo.
* Tooltip hiển thị thông tin hiệu quả theo quốc gia.

## 5. Kết quả nổi bật

* ROAS tổng thể thấp hơn đáng kể so với mức mục tiêu.
* Phễu chuyển đổi có tỷ lệ thất thoát cao, đặc biệt ở bước **Click → Purchase**.
* Tỷ lệ tương tác ngoài nhóm mục tiêu còn cao.
* Facebook có hiệu quả về Click và doanh thu tốt hơn Instagram trong bộ dữ liệu.
* Hiệu quả quảng cáo có sự khác biệt giữa các quốc gia và nhóm người dùng.

## 6. Đề xuất

1. Rà soát và tối ưu lại **nhóm tuổi và sở thích mục tiêu**.
2. Phân bổ lại ngân sách dựa trên hiệu quả thực tế của từng nền tảng.
3. Thực hiện **A/B Testing** đối với nhóm mục tiêu và định dạng quảng cáo.
4. Tập trung Remarketing vào nhóm người dùng có giá trị cao.

## 7. Cấu trúc thư mục

```text
.
├── README.md
├── Data/
│   ├── Raw/
│   │   ├── ad_events.csv
│   │   ├── ads.csv
│   │   ├── campaigns.csv
│   │   └── users.csv
│   └── Clean/
│       └── users_clean.csv
└── PowerBI/
    └── Social_Media_Ad_Performance.pbix
```

## 8. Hướng dẫn sử dụng

1. Mở file `Social_Media_Ad_Performance.pbix` bằng Power BI Desktop.
2. Nếu cần, cập nhật đường dẫn dữ liệu tại **Transform Data → Data source settings**.
3. Nhấn **Refresh** để cập nhật dữ liệu.
