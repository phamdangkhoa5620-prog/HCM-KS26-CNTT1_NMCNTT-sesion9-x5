&#x20;# ipo

\*\* Input

Nhiệt độ , độ ẩm , ánh sáng , độ pH

\*\* Process

Bộ cảm biến nhiệt độ , bộ xữ lí thông tin , thiết bị tắt bật tưới nước tự động

\*\* Ouput

trạng thái bơm , nước, quạt , đèn

Cảnh báo thời tiết ảnh hưởng như thế nào

Thay đổi linh động để phù hợp với lan

\# Sơ đồ phối hợp phần cứng và phần mềm

Cảm biến môi trường

Nhiệt độ · Độ ẩm · Ánh sáng · EC · pH



2\. SoC / Bộ điều khiển nhúng



Đọc cảm biến · Xử lý lệnh · Điều khiển đầu ra



3\. Gateway → Internet → Nền tảng Smart-Farm



4\. Truyền dữ liệu · Lưu lịch sử · Phân tích · Cảnh báo



Ứng dụng điện thoại và thiết bị chấp hành



Bơm · Quạt · Đèn · Báo cáo



\# 🚀 SMART-FARM — Hệ thống IoT cho trang trại Lan



> \*\*Smart-Farm\*\* là hệ thống IoT hỗ trợ người nông dân theo dõi môi trường, nhận cảnh báo và điều khiển thiết bị chăm sóc cây Lan.



!\[Hình hướng dẫn sử dụng Smart-Farm](https://rikkeiedu-storage.s3.ap-southeast-2.amazonaws.com/uploads/editor-images/1787648283613\_687ec2e7-229c-4942-a347-080fae59560a.webp)



\---



\## 1. Giới thiệu dự án



\- Theo dõi nhiệt độ, độ ẩm không khí, độ ẩm đất, ánh sáng, EC và pH.

\- Cảnh báo khi thông số vượt ngưỡng.

\- Điều khiển máy bơm, quạt và đèn nếu được hỗ trợ.

\- Lưu lịch sử và xem báo cáo môi trường.



\## 2. Sơ đồ kiến trúc hệ thống



```mermaid

flowchart TD

&#x20;   A\[Cảm biến môi trường] --> B\[SoC / Bộ điều khiển]

&#x20;   B --> C\[Gateway]

&#x20;   C --> D\[Nền tảng Smart-Farm]

&#x20;   D --> E\[Ứng dụng điện thoại]

&#x20;   E --> F\[Lệnh điều khiển]

&#x20;   F --> B

&#x20;   B --> G\[Bơm / Quạt / Đèn]

```



\## 3. Hướng dẫn cài đặt và sử dụng



\### Chuẩn bị

\- \[ ] Kiểm tra cảm biến và bộ điều khiển.

\- \[ ] Kiểm tra nguồn điện, nguồn nước và đường ống.

\- \[ ] Đảm bảo kết nối mạng nếu cần.

\- \[ ] Chuẩn bị tài khoản Smart-Farm.



\### Khởi động



```text

1\. Kiểm tra nguồn điện và cảm biến.

2\. Khởi động bộ điều khiển và gateway.

3\. Kiểm tra kết nối mạng.

4\. Mở ứng dụng Smart-Farm.

5\. Đăng nhập bằng tài khoản được cấp.

6\. Kiểm tra thông số môi trường.

```



\### Năm bước sử dụng

1\. \*\*Đăng nhập:\*\* Mở ứng dụng và nhập tài khoản.

2\. \*\*Xem thông số:\*\* Theo dõi nhiệt độ, độ ẩm, ánh sáng, EC và pH.

3\. \*\*Nhận cảnh báo:\*\* Kiểm tra thông báo và tình trạng thực tế.

4\. \*\*Điều khiển thiết bị:\*\* Chọn thủ công hoặc tự động nếu được hỗ trợ.

5\. \*\*Xem báo cáo:\*\* Xem dữ liệu theo ngày, tuần hoặc tháng nếu có.



\## 4. SoC và mô hình IPO



\*\*SoC (System on a Chip)\*\* là hệ thống trên một vi mạch, có thể tích hợp CPU, bộ nhớ và giao tiếp ngoại vi.



| Thành phần IPO | Ý nghĩa | Ví dụ |

|---|---|---|

| Input — Đầu vào | Dữ liệu hoặc lệnh | Cảm biến ghi nhận 32°C |

| Process — Xử lý | Phân tích dữ liệu | So sánh với ngưỡng cài đặt |

| Output — Đầu ra | Kết quả hoặc hành động | Cảnh báo hoặc bật quạt |



\### Chu trình Fetch–Decode–Execute



> \*\*Fetch (Nạp lệnh):\*\* CPU lấy lệnh từ bộ nhớ chương trình.

>

> \*\*Decode (Giải mã):\*\* CPU xác định ý nghĩa của lệnh.

>

> \*\*Execute (Thực thi):\*\* CPU thực hiện lệnh, có thể cập nhật trạng thái điều khiển hoặc gửi tín hiệu ra ngoại vi.



\## 5. Mô hình DIKW



DIKW gồm Data (Dữ liệu), Information (Thông tin), Knowledge (Tri thức) và Wisdom (Quyết định).



```text

&#x20;            /\\

&#x20;           / W \\    WISDOM — Quyết định phù hợp

&#x20;          /-----\\

&#x20;         /   K   \\  KNOWLEDGE — Tri thức

&#x20;        /---------\\

&#x20;       /     I     \\ INFORMATION — Thông tin

&#x20;      /-------------\\

&#x20;     /       D       \\ DATA — Dữ liệu: 32°C

&#x20;    /\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\\

```



| Cấp độ | Ví dụ |

|---|---|

| Data | Cảm biến ghi nhận 32°C. |

| Information | Nhiệt độ vượt ngưỡng 30°C đã cài. |

| Knowledge | Nhiệt độ cao có thể ảnh hưởng đến cây tùy giống và điều kiện chăm sóc. |

| Wisdom | Kiểm tra thực tế, cân nhắc thông gió hoặc làm mát và xác minh an toàn. |



> Không tưới nước chỉ vì nhiệt độ cao. Cần xem thêm độ ẩm đất và nhu cầu của cây.



\## 6. Bảng thông số và tính năng



| Thông số | Đơn vị thường dùng | Mục đích |

|---|---|---|

| Nhiệt độ | °C | Theo dõi nhiệt độ |

| Độ ẩm không khí | %RH | Theo dõi độ ẩm |

| Độ ẩm đất | % hoặc giá trị cảm biến | Hỗ trợ quyết định tưới |

| Ánh sáng | lux | Theo dõi cường độ sáng |

| EC | mS/cm | Đánh giá độ dẫn điện |

| pH | Không có đơn vị | Theo dõi tính axit/kiềm |



\- \[x] Theo dõi thông số môi trường.

\- \[x] Cảnh báo theo ngưỡng cấu hình.

\- \[x] Hỗ trợ điều khiển thiết bị nếu được triển khai.

\- \[x] Xem lịch sử nếu nền tảng hỗ trợ.

\- \[ ] Kiểm tra ngưỡng phù hợp với giống Lan.

\- \[ ] Kiểm tra dự phòng khi mất mạng.

\- \[ ] Kiểm thử dừng bơm an toàn.



\## 7. Lưu ý an toàn và xử lý sự cố



\- Không tháo lắp thiết bị khi đang hoạt động.

\- Kiểm tra nguồn nước và đường ống trước khi bật bơm.

\- Không dùng dữ liệu cảm biến lỗi hoặc quá cũ để tưới tự động.

\- Thiết lập giới hạn thời gian chạy bơm và điều kiện dừng.



\### Kiểm thử: RAM đầy do nhật ký



\*\*Hiện tượng:\*\* Bộ điều khiển phản hồi chậm hoặc không ghi được nhật ký do hết RAM.



1\. Ưu tiên trạng thái an toàn của thiết bị.

2\. Kiểm tra tiến trình sử dụng RAM và bộ đệm nhật ký.

3\. Giới hạn bộ đệm và áp dụng xoay vòng nhật ký (log rotation).

4\. Xóa bản ghi cũ theo chính sách, không xóa dữ liệu quan trọng tùy tiện.

5\. Đảm bảo lỗi nhật ký không chặn vòng điều khiển thiết yếu.

6\. Chỉ khởi động lại khi có phương án bảo vệ đầu ra và phục hồi an toàn.

7\. Kiểm tra lại RAM, cảm biến, kết nối và thiết bị sau khắc phục.



| Sự cố | Hành động ban đầu |

|---|---|

| Mất dữ liệu cảm biến | Kiểm tra nguồn và kết nối |

| Không có cảnh báo | Kiểm tra mạng và ngưỡng |

| Bơm không hoạt động | Kiểm tra nguồn và điều khiển |

| RAM đầy | Giới hạn nhật ký, kiểm tra bộ đệm |

| Mất Internet | Kiểm tra khả năng vận hành cục bộ |



\## 8. Hỗ trợ kỹ thuật



Khi báo sự cố, chuẩn bị thời điểm, thiết bị bị ảnh hưởng, nội dung cảnh báo, trạng thái kết nối và nhật ký lỗi đã thu thập an toàn. Liên hệ người phụ trách hoặc nhà cung cấp theo thông tin bàn giao.



\## 9. Kết luận



\- \*\*SoC:\*\* Nền tảng phần cứng thực thi chương trình.

\- \*\*IPO:\*\* Đầu vào → Xử lý → Đầu ra.

\- \*\*DIKW:\*\* Dữ liệu → Thông tin → Tri thức → Quyết định.



\*\*Mục tiêu:\*\* Chăm sóc cây Lan hiệu quả, sử dụng tài nguyên hợp lý và duy trì hoạt động an toàn.



\---



\*Tài liệu Smart-Farm — phiên bản 1.0. Xác nhận ngưỡng và cấu hình theo thiết bị thực tế trước khi vận hành.\*

