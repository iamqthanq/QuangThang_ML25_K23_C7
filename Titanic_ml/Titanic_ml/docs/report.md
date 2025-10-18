# TRƯỜNG ĐẠI HỌC SÀI GÒN  
## KHOA CÔNG NGHỆ THÔNG TIN  

### HỌC PHẦN: NHẬP MÔN MÁY HỌC - 841449  
# Challenge 1: Titanic - Machine Learning from Disaster  

**Giảng viên hướng dẫn:**  
Đỗ Như Tài  

**Nhóm sinh viên thực hiện:**  
- Vũ Ngọc Tùng – 3123410418  
- Tạ Quang Thắng – 3123410345  
- Phạm Hồng Thái – 3123410331  
- Phan Thanh Tùng – 3123410417  

**TP. HCM, 15/10/2025**  

---

## LỜI CẢM ƠN

Chúng em xin chân thành cảm ơn thầy **Đỗ Như Tài** – giảng viên bộ môn *Nhập môn máy học*, thuộc Khoa Công Nghệ Thông Tin, Trường Đại học Sài Gòn, đã trang bị cho chúng em những kiến thức, tài liệu và kỹ năng cần thiết để hoàn thành báo cáo này.

Trong quá trình thực hiện, do kiến thức và kinh nghiệm thực tế còn hạn chế nên bài báo cáo không tránh khỏi thiếu sót. Chúng em rất mong nhận được ý kiến đóng góp của thầy để nhóm học hỏi thêm và hoàn thiện hơn trong các bài báo cáo tiếp theo.

**Chúng em xin chân thành cảm ơn thầy!**

**Thành phố Hồ Chí Minh, ngày 15 tháng 10 năm 2025**  
**Sinh viên thực hiện:**  
Vũ Ngọc Tùng  
Tạ Quang Thắng  
Phạm Hồng Thái  
Phan Thanh Tùng  

---

## NHẬN XÉT VÀ ĐÁNH GIÁ CỦA GIẢNG VIÊN


---

## MỤC LỤC
1. [Giới thiệu](#1-giới-thiệu)
2. [Mục tiêu](#2-mục-tiêu)
3. [Bộ dữ liệu của dự án](#3-bộ-dữ-liệu-của-dự-án)
4. [Quy trình thực hiện dự án](#4-quy-trình-thực-hiện-dự-án)
5. [Kết quả](#5-kết-quả)
6. [Kết luận và hướng phát triển](#6-kết-luận-và-hướng-phát-triển)

---

## 1. Giới thiệu

### 1.1 Giới thiệu tổng quát

Thảm họa **chìm tàu Titanic (1912)** là một trong những sự kiện bi thương và nổi tiếng nhất trong lịch sử hàng hải. Con tàu "không thể chìm" này đã va phải tảng băng trôi trong chuyến đi đầu tiên từ Southampton (Anh) đến New York (Mỹ), khiến hơn **1500 người thiệt mạng**.  

Dữ liệu hành khách được ghi chép rất đầy đủ, phản ánh mối quan hệ giữa nhân khẩu học, điều kiện xã hội và khả năng sống sót — tạo thành một bộ dữ liệu kinh điển cho bài toán **phân tích và dự đoán bằng Machine Learning**.

Trong kỷ nguyên công nghệ 4.0, việc áp dụng học máy vào khai thác dữ liệu Titanic giúp người học:
- Hiểu rõ quy trình phân tích dữ liệu thực tế.
- Nhận diện các yếu tố ảnh hưởng đến khả năng sống sót.
- Rèn luyện quy trình làm việc khoa học dữ liệu: từ xử lý, chọn đặc trưng, huấn luyện mô hình đến đánh giá hiệu năng.

### 1.2 Thành viên nhóm tham gia

| Họ và tên | MSSV | Nhiệm vụ |
|------------|-------|-----------|
| Vũ Ngọc Tùng | 3123410418 | Report, Paper |
| Tạ Quang Thắng | 3123410345 | Slide PowerPoint, hỗ trợ nội dung |
| Phạm Hồng Thái | 3123410331 | Poster, nội dung chương trình |
| Phan Thanh Tùng | 3123410417 | Poster, nội dung chương trình |

---

## 2. Mục tiêu

Xây dựng mô hình học máy dự đoán biến mục tiêu **“Survived”** (0 – chết, 1 – sống sót).  

Thông qua đó, nhóm rèn luyện kỹ năng:
- Tiền xử lý dữ liệu
- Phân tích đặc trưng
- Đánh giá và chọn mô hình  
- Làm quen với pipeline cơ bản của Machine Learning:

1. Thu thập và hiểu dữ liệu  
2. Làm sạch dữ liệu (xử lý giá trị thiếu, biến dạng)  
3. Biến đổi và tạo đặc trưng mới (Feature Engineering)  
4. Huấn luyện mô hình  
5. Đánh giá và dự đoán kết quả  

Kết quả dự đoán được **nộp lên Kaggle** để so sánh độ chính xác.

---

## 3. Bộ dữ liệu của dự án

### 3.1 Bộ dữ liệu cung cấp

| Tên file | Nội dung | Mô tả |
|-----------|-----------|-------|
| train.csv | Dữ liệu huấn luyện | Chứa thông tin hành khách và biến mục tiêu “Survived” |
| test.csv | Dữ liệu kiểm tra | Không chứa nhãn “Survived”, dùng để dự đoán |
| gender_submission.csv | File mẫu | Gợi ý định dạng file nộp kết quả |

- **Tập huấn luyện (train):** 891 hàng, 12 tính năng  
- **Tập kiểm tra (test):** 418 hàng, 11 tính năng

### 3.2 Các biến trong dữ liệu

| Tên biến | Kiểu dữ liệu | Mô tả |
|-----------|--------------|-------|
| PassengerId | Số nguyên | Mã hành khách |
| Survived | 0 hoặc 1 | 1 - sống sót, 0 - tử vong |
| Pclass | 1, 2, 3 | Hạng vé |
| Name | Chuỗi | Họ tên hành khách |
| Sex | Chuỗi | Giới tính |
| Age | Số thực | Tuổi |
| SibSp | Số nguyên | Số anh/chị/em hoặc vợ/chồng đi cùng |
| Parch | Số nguyên | Số cha/mẹ hoặc con đi cùng |
| Ticket | Chuỗi | Mã vé |
| Fare | Số thực | Giá vé |
| Cabin | Chuỗi | Thông tin khoang |
| Embarked | C, Q, S | Cảng khởi hành |

---

## 4. Quy trình thực hiện dự án

### 4.1 Khám phá dữ liệu (EDA)
- Quan sát kích thước dữ liệu, kiểu dữ liệu  
- Kiểm tra giá trị thiếu (Age, Cabin, Embarked)  
- Thống kê mô tả và biểu đồ:  
  - Tỷ lệ sống sót theo giới tính  
  - Theo hạng vé (Pclass)  
  - Tương quan giữa tuổi và khả năng sống sót  

### 4.2 Tiền xử lý dữ liệu (Data Preprocessing)
- Điền giá trị thiếu (ví dụ: `Age` bằng trung bình)  
- Mã hóa biến phân loại:
  - `Sex`: male → 0, female → 1  
  - `Embarked`: S → 0, C → 1, Q → 2  
- Chuẩn hóa dữ liệu nếu cần  
- Xử lý giá trị ngoại lai (outlier)  

### 4.3 Tạo đặc trưng mới (Feature Engineering)
- `FamilySize = SibSp + Parch + 1`  
- Trích xuất `Title` từ cột `Name`  
- Gộp nhóm giá trị hiếm để giảm nhiễu  

### 4.4 Xây dựng và huấn luyện mô hình (Modeling)
Các mô hình được thử nghiệm:
- Logistic Regression  
- Decision Tree / Random Forest  
- K-Nearest Neighbors (KNN)  
- Support Vector Machine (SVM)  
- Gradient Boosting / XGBoost  

Quy trình:
- Chia dữ liệu (80% train – 20% validation)  
- Huấn luyện và đánh giá bằng **Accuracy** hoặc **F1-score**  

### 4.5 Đánh giá và so sánh mô hình
- So sánh hiệu suất giữa các mô hình  
- Chọn mô hình tốt nhất  
- Dự đoán nhãn *Survived* cho `test.csv`  
- Xuất file `submission.csv`  

---

## 5. Kết quả
- File dự đoán được chấm trên **Kaggle** bằng độ chính xác (Accuracy).  
- Mục tiêu: **Accuracy ≥ 0.75**  
- Một số kết quả quan sát:
  - Nữ giới và hành khách hạng vé cao có khả năng sống sót cao hơn  
  - Trẻ em có tỷ lệ sống sót cao hơn trung bình  

---

## 6. Kết luận và hướng phát triển

Dự án **Titanic – Machine Learning from Disaster** giúp người học:
- Hiểu quy trình thực tế của một dự án học máy  
- Làm quen với xử lý dữ liệu thiếu và không đồng nhất  
- Rèn kỹ năng chọn, huấn luyện và đánh giá mô hình  
- Sử dụng thành thạo các thư viện: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`

**Hướng phát triển:**
- Tối ưu mô hình bằng `GridSearchCV`  
- Áp dụng **ensemble methods** (Bagging, Boosting, Stacking)  
- Triển khai web app bằng **Flask / Streamlit**

---

