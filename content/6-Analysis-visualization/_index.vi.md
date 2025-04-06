+++
title = "Phân tích và trực quan hóa"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

#### Phân tích và trực quan hóa

#### Tổng quan về Amazon Athena

**Amazon Athena** là một dịch vụ truy vấn tương tác được sử dụng để phân tích dữ liệu trong Amazon S3 bằng SQL tiêu chuẩn. Chúng ta chỉ cần trỏ đến dữ liệu của bạn trong Amazon S3, xác định lược đồ và bắt đầu truy vấn với trình soạn thảo truy vấn tích hợp. Amazon Athena cho phép chúng ta khai thác tất cả dữ liệu của mình trong Amazon S3 mà không cần phải thiết lập các quy trình ETL phức tạp. Amazon Athena tính phí dựa trên các truy vấn được chạy.

**Amazon Athena** sử dụng Presto với hỗ trợ SQL ANSI và hoạt động với nhiều định dạng dữ liệu tiêu chuẩn, bao gồm CSV, JSON, ORC, Avro và Parquet. Athena được khuyến nghị cho nhu cầu truy vấn nhanh, nhưng nó cũng có thể xử lý các phân tích phức tạp, bao gồm các phép join lớn, các window function và mảng.
![Athena](/images/1/athena.png?width=10pc)

#### Tổng quan về Amazon QuickSight

**Amazon Quick Sight** là một dịch vụ biểu diễn dữ liệu được quản lý hoàn toàn bởi AWS.
![QuickSight](/images/1/quicksight.jpeg?width=10pc)

- **Nguồn dữ liệu (Data source)** là kho lưu trữ dữ liệu bên ngoài, và bạn cần cấu hình cách truy cập dữ liệu trong kho lưu trữ bên ngoài này, ví dụ như Amazon S3, Amazon Athena, Salesforce, v.v.

- **Tập dữ liệu (Dataset)** xác định dữ liệu cụ thể trong Nguồn dữ liệu mà bạn muốn sử dụng. Ví dụ, Nguồn dữ liệu có thể là một bảng nếu bạn đang kết nối với cơ sở dữ liệu. Nó có thể là một tệp nếu bạn đang kết nối với một Nguồn dữ liệu Amazon S3.

- **Phân tích (Analysis)** chứa một tập hợp các Hình ảnh trực quan và câu chuyện có liên quan, ví dụ như cho một mục tiêu kinh doanh cụ thể hoặc KPI.

- **Hình ảnh trực quan (Visual)** là biểu diễn đồ họa của dữ liệu của bạn. Bạn có thể tạo các loại Hình ảnh trực quan khác nhau trong một phân tích, sử dụng các tập dữ liệu và loại Hình ảnh trực quan khác nhau.

- **Bảng điều khiển (Dashboard)** là một trang bao gồm một hoặc nhiều Phân tích chỉ để xem, mà bạn có thể chia sẻ với người dùng Amazon QuickSight khác cho mục đích báo cáo. Bảng điều khiển lưu giữ cấu hình của Phân tích tại thời điểm bạn xuất bản nó, bao gồm những thứ như bộ lọc, tham số, điều khiển và thứ tự sắp xếp.

#### Nội dung

1. [Phân tích dữ liệu với Athena](../6-Analysis-visualization/1-analysis-athena/_index.vi.md)
2. [Trực quan hóa với AWS QuickSight](../6-Analysis-visualization/2-visualize-quicksight/_index.vi.md)
