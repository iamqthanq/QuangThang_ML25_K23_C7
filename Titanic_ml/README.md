---

## Giới thiệu
Dự án này thực hiện phân tích, xử lý và xây dựng mô hình học máy nhằm dự đoán khả năng sống sót của hành khách trên tàu Titanic, dựa trên bộ dữ liệu công khai của [Kaggle Titanic Challenge](https://www.kaggle.com/c/titanic).

Mục tiêu:
- Áp dụng quy trình chuẩn của một bài toán Machine Learning.
- So sánh hiệu quả giữa các mô hình và các mức độ **Feature Engineering (FE)** khác nhau.
- Đánh giá mô hình dựa trên độ chính xác và AUC.

---

## Cấu trúc dự án
project/ </br>
│</br>
├── data/</br>
│ ├── train.xlsx</br>
│ ├── test.xlsx</br>
│ └── (dữ liệu gốc từ Kaggle)</br>
│</br>
├── eda/</br>
│ ├── eda.ipynb</br>
│ ├── eda.html</br>
│ └── img/ (chứa các hình ảnh, biểu đồ EDA)</br>
│</br>
├── processing/</br>
│ ├── processing.ipynb</br>
│ └── processing.html</br>
│</br>
├── models/</br>
│ ├── model_RF.ipynb</br>
│ └── model_RF.html</br>
│</br>
├── exps/</br>
│ ├── exp1_no_FE/</br>
│ │ ├── exp1.ipynb</br>
│ │ ├── exp1.html</br>
│ │ └── exp1_summary_result.xlsx</br>
│ │</br>
│ ├── exp2_title_familysize/</br>
│ │ ├── exp2.ipynb</br>
│ │ ├── exp2.html</br>
│ │ └── exp2_summary_result.xlsx</br>
│ │</br>
│ ├── exp3_full_FE/</br>
│ │ ├── exp3.ipynb</br>
│ │ ├── exp3.html</br>
│ │ └── exp3_summary_result.xlsx</br>
│ │</br>
│ └── summary_result.xlsx (so sánh tổng hợp giữa 3 exp)</br>
│</br>
├── docx/</br>
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
| **data/** | Dữ liệu gốc (train/test từ Kaggle) | Cung cấp dữ liệu đầu vào |
| **eda/** | Phân tích khám phá dữ liệu (Exploratory Data Analysis) | Hiểu cấu trúc dữ liệu, trực quan hóa, phát hiện missing value/outlier |
| **processing/** | Tiền xử lý dữ liệu và Feature Engineering | Làm sạch dữ liệu, mã hóa, tạo đặc trưng mới (Title, FamilySize, HasCabin, ...) |
| **models/** | Xây dựng và huấn luyện mô hình | Huấn luyện các mô hình (Random Forest, XGBoost, Logistic Regression, v.v.) |
| **exps/** | Các thí nghiệm so sánh (Experiment 1–3) | So sánh ảnh hưởng của mức độ Feature Engineering đến kết quả mô hình |
| **docx/** | Báo cáo, slide, paper, poster | Tổng hợp kết quả, trình bày và thuyết trình dự án |

---

## Chi tiết các thí nghiệm (Experiments)

| Tên Exp | Nội dung chính | Đặc điểm |
|----------|----------------|-----------|
| **Exp1 – No FE** | Huấn luyện mô hình **không sử dụng Feature Engineering** | Chỉ dùng dữ liệu gốc từ Kaggle |
| **Exp2 – Title + FamilySize** | Thêm hai đặc trưng mới | Cải thiện độ chính xác đáng kể |
| **Exp3 – Full FE** | Thực hiện đầy đủ Feature Engineering (Title, FamilySize, HasCabin, TicketPrefix, FareBin, AgeBin, ...) | Đạt kết quả cao nhất |

- Mỗi thư mục `expX/` có một file `expX_summary_result.xlsx` để so sánh các mô hình trong cùng thí nghiệm.  
- File `summary_result.xlsx` (ngoài cùng thư mục `exps/`) tổng hợp kết quả 3 thí nghiệm để rút ra kết luận cuối cùng.

---

## Mô hình được chọn
Sau khi thử nghiệm nhiều mô hình (Logistic Regression, SVM, Decision Tree, Random Forest, XGBoost),  
**Random Forest (RF)** đạt **hiệu suất cao nhất**, được chọn làm mô hình chính cho phần triển khai.

- File notebook: `models/model_RF.ipynb`  
- File HTML: `models/model_RF.html`  
- Độ chính xác (Accuracy): *84.74%*  
- AUC: *~89.82%*  

---

## Quy trình thực hiện tổng quát

```text
1. EDA → Hiểu dữ liệu, phát hiện vấn đề  
2. Processing → Làm sạch + tạo đặc trưng (Feature Engineering)  
3️. Experiments → Thử nghiệm 3 cấp độ FE khác nhau  
4️. Modeling → Huấn luyện mô hình tốt nhất (Random Forest)  
5️. Evaluation → So sánh, chọn mô hình cuối cùng  
6️. Documentation → Viết báo cáo, slide, paper, poster


