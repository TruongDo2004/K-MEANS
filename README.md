
**Tên học phần**: Học Máy  
**Đề tài**: Xây dựng mô hình K-Means để phân khúc thị trường dựa trên dữ liệu giao dịch bán buôn  

### Thành viên tham gia:
- **[Đỗ Trường Anh]**  
  Liên hệ: [dotruonganh2004@gmail.com]
- **[Nguyễn Thị Lan Anh]**  
  Liên hệ: [lan352639@gmail.com]
- **[Phạm Trọng Toàn]**  
  Liên hệ: [Phamtrongtoank4@gmail.com]

### Giới thiệu bài toán:
Trong môi trường kinh doanh ngày càng cạnh tranh, việc phân khúc khách hàng giúp các doanh nghiệp tối ưu hóa chiến lược marketing và nâng cao hiệu quả kinh doanh. Phân khúc khách hàng là quá trình chia khách hàng thành các nhóm dựa trên các đặc điểm chung như hành vi mua sắm, tần suất giao dịch, giá trị đơn hàng, v.v. 

Mục tiêu của dự án này là sử dụng dữ liệu giao dịch bán buôn để phân tích và phân loại khách hàng thành các nhóm khác nhau, từ đó giúp doanh nghiệp hiểu rõ hơn về các phân khúc thị trường và áp dụng các chiến lược phù hợp cho từng nhóm. Thuật toán **K-Means** được áp dụng để thực hiện phân cụm, cho phép xác định các cụm khách hàng có hành vi mua hàng tương đồng.

Dữ liệu sử dụng bao gồm thông tin về hóa đơn (mã hóa đơn, mã sản phẩm, mô tả sản phẩm), số lượng, giá đơn vị, mã khách hàng, quốc gia và ngày giao dịch.

### Phương pháp:
Dự án được thực hiện theo các bước chính sau đây:

1. **Thu thập và chuẩn bị dữ liệu**:
   - Dữ liệu được lấy từ các giao dịch bán buôn của khách hàng, bao gồm các trường như: mã hóa đơn (`INV_NO`), mã sản phẩm (`S_CODE`), mô tả sản phẩm (`DESC`), số lượng (`QUANTITY`), đơn giá (`UNIT_PRICE`), mã khách hàng (`CUST_ID`), ngày hóa đơn (`INV_DATE`), và quốc gia (`Country`).
   - Xử lý các giá trị thiếu (`NaN`), loại bỏ các bản ghi trùng lặp, và xử lý dữ liệu ngoại lai (outliers) như giá trị đơn hàng và số lượng sản phẩm bất thường.

2. **Tiền xử lý dữ liệu**:
   - Chuyển đổi định dạng dữ liệu ngày (`INV_DATE`) thành dạng chuẩn để phân tích xu hướng bán hàng theo tháng và ngày trong tuần.
   - Sử dụng các phương pháp trực quan hóa (biểu đồ đường, biểu đồ thanh) để phân tích xu hướng doanh thu và xác định các yếu tố quan trọng như thời gian mua hàng cao điểm và quốc gia có doanh số cao nhất.

3. **Phân tích và chuẩn bị các biến số đầu vào cho mô hình K-Means**:
   - Lựa chọn các biến số chính cho phân cụm: `QUANTITY` (số lượng mua) và `UNIT_PRICE` (giá đơn vị).
   - Chuẩn hóa dữ liệu bằng cách sử dụng **StandardScaler** để đảm bảo các biến số được đưa về cùng một thang đo, giúp cải thiện hiệu quả của thuật toán K-Means.

4. **Triển khai mô hình K-Means**:
   - Sử dụng thuật toán **K-Means** để phân khách hàng thành nhiều cụm. Số lượng cụm (k) được lựa chọn thông qua phương pháp **Elbow Method** để tìm ra số cụm tối ưu.
   - Đánh giá mô hình bằng **Silhouette Score**, một thước đo giúp đánh giá mức độ tách biệt giữa các cụm. Điểm silhouette cao cho thấy các cụm được phân chia rõ ràng, trong khi điểm thấp cho thấy các cụm có sự chồng chéo.

5. **Đánh giá và trực quan hóa kết quả**:
   - Trực quan hóa các cụm khách hàng bằng biểu đồ phân tán để dễ dàng nhận diện đặc điểm của từng nhóm khách hàng. 
   - Phân tích đặc điểm của từng nhóm: nhóm có xu hướng mua số lượng lớn nhưng giá trị đơn hàng thấp, hoặc nhóm mua ít nhưng giá trị cao, giúp doanh nghiệp hiểu rõ hành vi của từng phân khúc khách hàng.

### Kết quả chạy mô hình:
- **Kết quả phân cụm**: Mô hình K-Means đã chia tập dữ liệu thành `k` cụm khách hàng khác nhau, mỗi cụm đại diện cho một phân khúc với các đặc điểm hành vi mua sắm riêng biệt.
- **Silhouette Score**: Mô hình đạt được điểm silhouette là 0.9996447686344725, cho thấy mức độ tách biệt tốt giữa các cụm, đảm bảo rằng các khách hàng trong cùng một cụm có hành vi tương đồng.
- **Phân tích kết quả**: 
  - Một số cụm thể hiện rõ sự khác biệt về số lượng sản phẩm mua và giá đơn vị. Ví dụ: một cụm bao gồm các khách hàng mua số lượng lớn sản phẩm với đơn giá thấp, thường là các doanh nghiệp nhỏ hoặc đại lý.
  - Cụm khác bao gồm các khách hàng có giá trị đơn hàng cao nhưng số lượng sản phẩm mua ít hơn, thường là những khách hàng cá nhân hoặc doanh nghiệp với nhu cầu đặc thù.
  - Phân tích này cung cấp cơ sở để doanh nghiệp xây dựng chiến lược marketing, quảng cáo, và dịch vụ chăm sóc khách hàng phù hợp cho từng nhóm.

### Kết luận:
Việc phân cụm khách hàng bằng thuật toán K-Means là một phương pháp hiệu quả để khám phá các phân khúc thị trường và hiểu rõ hơn về hành vi mua sắm của khách hàng. Qua quá trình phân tích, dự án đã cung cấp những thông tin quan trọng về các nhóm khách hàng tiềm năng, từ đó giúp doanh nghiệp đưa ra những chiến lược tối ưu hơn trong việc tiếp cận và phục vụ khách hàng.

