# RECOMMENDATION SYSTEMS: TRADITIONAL HYBRID & LLM-ENHANCED

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Gemini](https://img.shields.io/badge/Google-Gemini%20API-4285F4?logo=googlegemini)](https://ai.google.dev/)
[![Status](https://img.shields.io/badge/Status-Production--Ready-success)]()

> **MODULE DESCRIPTION:** Phân hệ cốt lõi chịu trách nhiệm xây dựng hệ thống khuyến nghị thông minh. Điểm đột phá của dự án là khả năng **hiểu ý định người dùng qua ngôn ngữ tự nhiên** nhờ LLM (Gemini), kết hợp cơ chế **Fallback** linh hoạt về hệ thống Hybrid truyền thống để đảm bảo hiệu năng và độ ổn định thực tế.

---

## CORE INNOVATION: LLM FEATURE EXTRACTION

Thay vì chỉ xử lý dữ liệu thô, project tập trung vào việc trích xuất đặc trưng ngữ nghĩa từ câu hỏi của người dùng:

1.  **PHÂN TÍCH NGỮ NGHĨA:** Hiểu sâu các yêu cầu mang tính cảm tính (Ví dụ câu prompt của người dùng: *"Muốn nấu canh chua cho gia đình 4 người ăn thì cần mua những gì?"*).
2.  **TRÍCH XUẤT ĐẶC TRƯNG (KEYWORD EXTRACTION):** Tự động bóc tách Key-features như: Chủng loại, hương vị, thương hiệu, mục đích sử dụng.
3.  **LÀM GIÀU ĐẦU VÀO (INPUT ENRICHMENT):** Sử dụng các từ khóa đã trích xuất để làm mượt dữ liệu đầu vào, giúp bộ lọc Content-based đạt độ chính xác tối ưu.

---

## WORKFLOW PIPELINE

Quy trình vận hành được thiết kế theo tư duy **"Hybrid-First"** và **"Safe-Failure"**:

* **USER INPUT:** Tiếp nhận yêu cầu dạng văn bản tự do.
* **LLM ENGINE:** Gọi API Gemini để xử lý. Nếu thành công, sử dụng Keyword trích xuất.
* **FALLBACK MECHANISM:** Nếu API lỗi hoặc Timeout, hệ thống tự động chuyển sang **Traditional Path** sử dụng dữ liệu thô từ lịch sử và thuộc tính cứng.
* **RECOMMENDATION ENGINE:** Chạy song song Content-based (TF-IDF) và Rule-based (Association Rules).
* **RANKING:** Sắp xếp sản phẩm theo độ tương đồng và chỉ số phổ biến (Popularity).

---

## KEY METRICS & EVALUATION

Hệ thống được đo lường khắt khe qua bộ chỉ số tiêu chuẩn của hệ thống khuyến nghị hiện đại:

| NHÓM CHỈ SỐ | CHỈ SỐ CỤ THỂ | Ý NGHĨA HỆ THỐNG |
| :--- | :--- | :--- |
| **ĐỘ CHÍNH XÁC** | `Precision@K`, `Recall@K` | Tỷ lệ sản phẩm gợi ý thực sự khớp với nhu cầu người dùng. |
| **XẾP HẠNG** | `MRR (Mean Reciprocal Rank)` | Vị trí của sản phẩm phù hợp nhất (càng gần Top 1 càng tốt). |
| **ĐỘ PHỦ** | `Coverage` | Khả năng bao phủ danh mục sản phẩm, tránh chỉ gợi ý các món quá phổ biến. |
| **TRẢI NGHIỆM** | `Personalization`, `Novelty` | Mức độ cá nhân hóa và khả năng gợi ý những sản phẩm mới lạ. |

---

## USAGE GUIDE

### BƯỚC 1: BASELINE & TRADITIONAL HYBRID
* **File:** `src/TraditionalRecommendation.ipynb`
* **Chức năng:** Xây dựng mô hình nền tảng sử dụng TF-IDF và Association Rules.
* **Mục tiêu:** Đảm bảo hệ thống luôn có kết quả trả về ngay cả khi không có internet/API.

### BƯỚC 2: LLM INTEGRATION & OPTIMIZATION
* **File:** `src/LLMsRecommendation.ipynb`
* **Chức năng:** Tích hợp Gemini API để xử lý văn bản đầu vào và trích xuất đặc trưng.
* **Mục tiêu:** Nâng tầm chất lượng gợi ý từ "đúng từ khóa" sang "đúng ý định".

---

## TECH STACK

* **LLM ENGINE:** `Google Gemini API` (Generative AI).
* **VECTORIZATION:** `TfidfVectorizer` (Scikit-learn).
* **SIMILARITY:** `Cosine Similarity`.
* **COMPUTATION:** `NumPy`, `Pandas`, `SciPy (Sparse Matrix)`.
* **PERSISTENCE:** `Joblib` (Lưu trữ model).

---

## PROJECT STRUCTURE

```text
Recommendation-Systems/
├── models/
|   ├── Content/                      # Các file model phục vụ cho Content-based
|   |   ├── X_char.npz
|   |   ├── X_word.npz
|   |   ├── product_index.csv
|   |   ├── tfidf_char.joblib
|   |   └── tfidf_word.joblib
|   ├── Rules/                        # Các file csv phục vụ cho Collaborative Filltering
│   |   ├── category_rules.csv        
│   |   └── item_rules.csv
│
├── src/                              # Source Code
│   ├── TraditionalRecommendation.ipynb # Hệ thống Hybrid truyền thống (Fallback)
│   └── LLMsRecommendation.ipynb        # Hệ thống nâng cao sử dụng Gemini API
│
└── README.md                         # Tài liệu hướng dẫn cho folder recommendation-system
