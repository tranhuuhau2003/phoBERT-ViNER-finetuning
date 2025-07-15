
# 📘 phoBERT-ViNER-finetuning

Fine-tuning mô hình PhoBERT cho bài toán **Nhận diện thực thể tiếng Việt (Vietnamese Named Entity Recognition - NER)** sử dụng thư viện [Hugging Face Transformers](https://huggingface.co/transformers/).

## 🚀 Mục tiêu

Dự án này thực hiện fine-tuning mô hình [PhoBERT](https://huggingface.co/vinai/phobert-base) — một pretrained language model cho tiếng Việt — nhằm cải thiện khả năng nhận diện các thực thể như tên người, địa điểm, tổ chức, v.v. Dữ liệu huấn luyện sử dụng là bộ **VLSP NER** (hoặc bộ tương đương đã được tiền xử lý).

---

## 🧠 Mô hình sử dụng

- **Pretrained model**: [`vinai/phobert-base`](https://huggingface.co/vinai/phobert-base)
- **Thư viện**: `transformers`, `torch`, `seqeval`, `scikit-learn`, `pandas`, `matplotlib`
- **Task**: Sequence labeling (BIO format)

---

## 🛠️ Cài đặt

```bash
# Clone repo
git clone https://github.com/tranhuuhau2003/phoBERT-ViNER-finetuning.git
cd phoBERT-ViNER-finetuning

# Tạo virtual environment (khuyến khích)
python -m venv venv
source venv/bin/activate   # (Linux/Mac)
venv\Scripts\activate.bat  # (Windows)

# Cài đặt thư viện cần thiết
pip install -r requirements.txt
```

---

## 📁 Cấu trúc thư mục

```bash
phoBERT-ViNER-finetuning/
│
├── data/                  # Dữ liệu NER đã được tiền xử lý (train/dev/test)
│
├── models/                # Thư mục lưu checkpoint mô hình sau khi huấn luyện
│
├── utils/                 # Hàm hỗ trợ: tokenizer, evaluation, convert dữ liệu
│   └── ner_utils.py
│
├── train.py               # Script huấn luyện mô hình
├── evaluate.py            # Script đánh giá mô hình đã huấn luyện
├── inference.py           # Dự đoán thực thể cho câu mới
├── requirements.txt       # Danh sách thư viện cần thiết
└── README.md              # Tài liệu hướng dẫn (bạn đang đọc)
```

---

## 🏋️‍♂️ Huấn luyện mô hình

```bash
python train.py \
    --train_file data/train.txt \
    --valid_file data/valid.txt \
    --model_name phobert-base \
    --output_dir models/phobert_ner \
    --epochs 5 \
    --batch_size 16 \
    --lr 3e-5
```

---

## 📊 Đánh giá mô hình

```bash
python evaluate.py \
    --model_dir models/phobert_ner \
    --test_file data/test.txt
```

- Các metric đánh giá:
  - **Precision**
  - **Recall**
  - **F1-score** (sử dụng `seqeval`)

---

## 💬 Dự đoán thực thể

```bash
python inference.py --text "Nguyễn Văn A sinh sống tại Hà Nội."
```

---

## 📈 Kết quả mẫu

| Entity Type | Precision | Recall | F1-score |
|-------------|-----------|--------|----------|
| PER         | 92.1%     | 90.5%  | 91.3%    |
| LOC         | 89.7%     | 91.2%  | 90.4%    |
| ORG         | 86.3%     | 84.0%  | 85.1%    |
| **Macro Avg** | **89.4%** | **88.6%** | **89.0%** |

---

## 📚 Tham khảo

- [PhoBERT on HuggingFace](https://huggingface.co/vinai/phobert-base)
- [VLSP NER 2016 Dataset](https://vlsp.org.vn/contest/vlsp-2016)
- [Hugging Face Transformers](https://github.com/huggingface/transformers)

---

## 👨‍💻 Tác giả

- **Trần Hửu Hậu** – [GitHub](https://github.com/tranhuuhau2003)

---

## 📄 Giấy phép

Dự án được phát hành theo giấy phép MIT. Xem file `LICENSE` để biết thêm chi tiết.
