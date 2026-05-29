# Banknote Recognition – Nhận diện tiền tệ real-time

Dự án nhận diện tiền tệ Việt Nam real-time qua webcam sử dụng TensorFlow/Keras. Model có thể phân loại nhiều mệnh giá tiền Việt Nam bằng AI và hiển thị kết quả trực tiếp trên màn hình.

## Thực hiện bởi nhóm [HKT] học phần Trí tuệ nhân tạo tại UEHm

1. Nguyễn Bảo Hân - 31251027458
2. Trần Thế Đăng Khoa - 31251020280
3. Hoàng Bảo Trân - 31251020280
---

## Cấu trúc project

```bash
├── VND_Optimized_Kaggle.ipynb   # Notebook train model trên Kaggle
├── gui.py                       # Giao diện nhận diện tiền real-time
├── VND_model.h5          # File model đã train
└── README.md
```

---

## File project

### 1. `VND_Optimized_Kaggle.ipynb`

Notebook dùng để:

* Tiền xử lý dataset
* Train CNN model
* Validation/Test model
* Lưu model `.h5`

Chạy trên Kaggle hoặc Google Colab có GPU để train nhanh hơn.

---

### 2. `gui.py`

Script giao diện nhận diện tiền real-time bằng webcam.

Chức năng:

* Mở webcam
* Detect tiền trực tiếp
* Hiển thị tên mệnh giá
* Hiển thị confidence (%)
* Nhấn `Q` để thoát

---

### 3. `VND_model.h5`

Model đã train sẵn dùng cho nhận diện tiền Việt Nam.

Đặt file cùng thư mục với `gui.py` trước khi chạy.

---

## Cách chạy project

### 1. Clone repo

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

---

### 2. Cài thư viện

```bash
pip install tensorflow keras opencv-python numpy pillow
```

---

### 3. Chạy chương trình

```bash
python gui.py
```

Đưa tờ tiền vào trước webcam, AI sẽ nhận diện và hiển thị kết quả trực tiếp trên màn hình.

Nhấn phím `Q` để thoát chương trình.

---

## Hướng dẫn chỉnh sửa

### Thay đường dẫn model

Mở file `gui.py`, tìm dòng:

```python
MODEL_PATH = "VND_model.h5"
```

Nếu model ở thư mục khác thì thay bằng đường dẫn đầy đủ:

```python
MODEL_PATH = "C:/Users/ten/Downloads/VND_model.h5"
```

---

### Điều chỉnh ngưỡng confidence

Mặc định chương trình sẽ hiện `"Chua xac dinh duoc"` nếu confidence thấp.

Tìm đoạn:

```python
if confidence < 80:
```

* Tăng lên (90–95) nếu model nhận diện nhầm nhiều
* Giảm xuống (60–70) nếu model quá khó nhận diện

---

### Thêm mệnh giá mới

Nếu train thêm dữ liệu mới, cập nhật `CLASS_LABELS` trong `gui.py`:

```python
CLASS_LABELS = {
    0: "1000 VND",
    1: "2000 VND",
    2: "5000 VND",
    3: "10000 VND",
    4: "20000 VND",
    5: "50000 VND",
    6: "100000 VND",
    7: "200000 VND",
    8: "500000 VND"
}
```

Thứ tự index phải khớp với thứ tự class lúc train model.

---

## Các mệnh giá hỗ trợ

* 1.000 VND
* 2.000 VND
* 5.000 VND
* 10.000 VND
* 20.000 VND
* 50.000 VND
* 100.000 VND
* 200.000 VND
* 500.000 VND

---

## Yêu cầu hệ thống

* Python 3.10+
* Webcam
* TensorFlow / Keras
* OpenCV
* NumPy

Khuyến nghị:

* GPU NVIDIA để train model nhanh hơn
* Webcam HD để nhận diện chính xác hơn

---

## Công nghệ sử dụng

* Python
* TensorFlow / Keras
* OpenCV
* NumPy
* CNN (Convolutional Neural Network)

---
## Source code

Model có sử dụng những nguồn dataset từ kaggle, mô hình được tích hợp từ 2 nguồn repo chính và sử dụng tích hợp AI:
* Dataset URL: https://www.kaggle.com/datasets/nguyentrongdai/vietnamese-currency
* Code URL: https://github.com/thangnch/MiAI_Money_Classify?fbclid=IwY2xjawSGkW9leHRuA2FlbQIxMABicmlkETFqSVVoZU5nbUgxeFZKeENxc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHiYIqsFaV73HB7Q2feesYiIf9rAzgxCH3vFsE1-_ZShoDe-if6gQ7zVFFrt3_aem_ILcEmCIvz5HC2F63OwGcCA
* Code URL: https://github.com/tamtridung/Vietnam_currency_classification
---
## Ghi chú

* Model hoạt động tốt trong điều kiện đủ sáng
* Nên đưa tiền vào giữa khung hình
* Tránh nền quá phức tạp để tăng độ chính xác
* Webcam chất lượng thấp có thể làm giảm accuracy

---

