---

## Giới thiệu
Dự án này thực hiện **phân tích, xử lý và xây dựng mô hình học máy** nhằm **dự đoán khả năng mắc bệnh tiểu đường type 2** dựa trên bộ dữ liệu công khai của [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database).

**Mục tiêu:**
- Áp dụng quy trình chuẩn của một bài toán Machine Learning.
- So sánh hiệu quả giữa 3 mô hình khác nhau: **Logistic Regression**, **Random Forest** và **XGBoost**.
- Đánh giá mô hình dựa trên **Accuracy**, **F1-score** và **ROC-AUC**.

---

## Cấu trúc dự án
project/ </br>
│</br>
├── data/</br>
│ ├── diabetes.csv</br>
│</br>
├── preprocessing/</br>
│ ├── preprocessing.ipynb</br>
│ └── preprocessing.html</br>
│</br>
├── eda/</br>
│ ├── eda.ipynb</br>
│ ├── eda.html</br>
│ └── img/ (chứa các hình ảnh, biểu đồ EDA)</br>
│</br>
├── models/</br>
│ ├── model_XGB.ipynb</br>
| ├── model_XGB.html</br>
│</br>
├── exps/</br>
│ ├── exp1_LR/</br>
│ │ ├── exp1.ipynb</br>
│ │ ├── exp1.html</br>
│ │</br>
│ ├── exp2_LF/</br>
│ │ ├── exp2.ipynb</br>
│ │ ├── exp2.html</br>
│ │</br>
│ ├── exp3_XGB/</br>
│ │ ├── exp3.ipynb</br>
│ │ ├── exp3.html</br>
│ │</br>
│ └── summary_result.xlsx</br>
│</br>
├── docs/</br>
│ ├── report.md</br>
│ ├── slide.pptx</br>
│ ├── paper.docx</br>
│ └── poster.png</br>
│</br>
└── README.md </br>

---

## Mô tả chức năng từng phần

| Thư mục | Nội dung chính | Chức năng |
|----------|----------------|-----------|
| **data/** | Dữ liệu gốc từ Kaggle | Cung cấp dữ liệu đầu vào cho toàn bộ pipeline |
| **preprocessing/** | Tiền xử lý dữ liệu | Làm sạch dữ liệu, xử lý missing value, chuẩn hóa, mã hóa biến |
| **eda/** | Phân tích khám phá dữ liệu (EDA) | Trực quan hóa dữ liệu, kiểm tra tương quan, phát hiện outlier |
| **models/** | Huấn luyện mô hình ML | Chứa các mô hình Logistic Regression, Random Forest, XGBoost |
| **exps/** | Các thí nghiệm so sánh | Đánh giá ảnh hưởng của preprocessing và tuning đến kết quả mô hình |
| **docs/** | Báo cáo và trình bày | Chứa các tài liệu, báo cáo, slide, poster của dự án |

---

## Chi tiết các thí nghiệm (Experiments)

| Tên Exp | Nội dung chính | Đặc điểm |
|----------|----------------|-----------|
| **Exp1 – Baseline** | Huấn luyện mô hình **trên dữ liệu gốc chưa chọn đặc trưng** | Kết quả cơ bản để so sánh |
| **Exp2 – Feature Selected** | Lọc ra các đặc trưng quan trọng (theo tương quan & feature importance) | Cải thiện độ chính xác đáng kể |
| **Exp3 – Final Tuned** | Áp dụng **GridSearchCV** và **tuning siêu tham số** | Đạt kết quả cao nhất trong các thí nghiệm |

- File `summary_result.xlsx` tổng hợp kết quả của cả 3 thí nghiệm.

---

## Mô hình được chọn
Sau khi thử nghiệm 3 mô hình (Logistic Regression, Random Forest, XGBoost),  
**XGBoost** cho hiệu năng tốt nhất và được chọn làm mô hình cuối cùng.

- File notebook: `models/model_XGB.ipynb`  
- File HTML: `models/model_XGB.html`  
- Độ chính xác (Accuracy): *~86%*  
- ROC-AUC: *~91%*  

---

## Quy trình thực hiện tổng quát

```text
1. EDA → Phân tích và hiểu dữ liệu  
2. Preprocessing → Làm sạch, chuẩn hóa, chọn đặc trưng  
3. Experiments → Chạy 3 thí nghiệm với mức độ xử lý và tuning khác nhau  
4. Modeling → Huấn luyện 3 mô hình (LR, RF, XGB)  
5. Evaluation → So sánh kết quả và chọn mô hình tốt nhất  
6. Documentation → Viết báo cáo và trình bày kết quả
