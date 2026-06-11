<div align="center">

# 🔬 EdTech-KHTN-CI

### Hệ thống Tự động hóa Đề kiểm tra Khoa học Tự nhiên (THCS)

*Tài liệu kiến trúc giải pháp EdTech định hướng Agentic Engineering*  
*Python · Quarto · LaTeX · Streamlit · Docker*

[![app-ci](https://github.com/thaydang/EdTech-KHTN-CI/actions/workflows/app-ci.yml/badge.svg)](https://github.com/thaydang/EdTech-KHTN-Docs)
[![auto-render](https://github.com/thaydang/EdTech-KHTN-CI/actions/workflows/auto-render.yml/badge.svg)](https://github.com/thaydang/EdTech-KHTN-Docs)
[![docker-ci](https://github.com/thaydang/EdTech-KHTN-CI/actions/workflows/docker-ci.yml/badge.svg)](https://github.com/thaydang/EdTech-KHTN-Docs)

![Python](https://img.shields.io/badge/Pythonps://img.shields.io/badge/Lua-2.1%25-2C2D72?logo=lua&logoColor=white)
!Shell
https://img.shields.io/badge/License-MIT-green

---

📌 **LƯU Ý VỀ PHẠM VI KHO LƯU TRỮ**  

Kho lưu trữ này cung cấp **tài liệu giải pháp và kiến trúc hệ thống** cho bài toán tự động hóa xây dựng đề kiểm tra môn **Khoa học Tự nhiên (KHTN)** cấp THCS.  
Mã nguồn vận hành thực tế của ứng dụng được quản lý riêng phục vụ triển khai nội bộ.

</div>

---

## 📖 Giới thiệu

**EdTech-KHTN-CI** là một giải pháp công nghệ giáo dục được thiết kế nhằm:

- Chuẩn hóa quy trình xây dựng ngân hàng câu hỏi KHTN  
- Tự động hóa việc sinh đề kiểm tra theo ma trận đặc tả  
- Đảm bảo đầu ra DOCX/PDF đúng chuẩn hình thức và kỹ thuật sư phạm  

Giải pháp hướng tới các khối lớp **6 – 9**, bám sát Chương trình GDPT 2018 và các hướng dẫn hiện hành của Bộ GD&ĐT.

Hệ thống kết hợp mô hình **giáo viên định hướng nội dung bằng ngôn ngữ tự nhiên** với động cơ xử lý tài liệu tự động dựa trên **Python – Quarto – LaTeX**, kèm theo giao diện thao tác trực quan và quy trình kiểm định chất lượng qua CI/CD.

### ✨ Điểm nổi bật

* 🤖 **Agentic Workflow:** AI Agent hỗ trợ phân tích ngữ cảnh, sinh cấu trúc nội dung `.qmd` phù hợp yêu cầu cần đạt.
* 🖨️ **Render Engine tự động:** Chuỗi Quarto → Pandoc → Lua Filter đảm bảo cấu trúc câu hỏi và định dạng cột A–B–C–D được bảo toàn.
* 📊 **Ma trận đặc tả chuẩn hóa:** Điều phối linh hoạt tỷ lệ các mức độ nhận thức (NB – TH – VD – VDC).
* 🐳 **Môi trường đồng nhất:** Đóng gói toàn bộ hệ phụ trợ (font, TeX Live…) giúp loại bỏ lỗi hiển thị khi thay đổi thiết bị.

---
[README.md.md](https://github.com/user-attachments/files/28819011/README.md.md)
[README.md](https://github.com/user-attachments/files/28818993/README.md)

## 🏗️ Kiến trúc hệ thống tổng thể

```text
┌─────────────────────────────────────────────────────────────┐
│                   [KHỐI LÕI – AI BRAIN]                     │
│  exam-khtn/.agent/  →  Rules · Agents · Workflows            │
│  Định hướng AI sinh nội dung Markdown (.qmd) chuẩn KHTN     │
└──────────────────────────┬──────────────────────────────────┘
                           │ Biên dịch .qmd
                           ▼
┌─────────────────────────────────────────────────────────────┐
│               [KHỐI ĐỘNG CƠ – CORE ENGINE]                  │
│  Lua Filters  →  Can thiệp Pandoc AST                       │
│  LaTeX Header →  Chuẩn hóa PDF                              │
└──────────────────────────┬──────────────────────────────────┘
                           │ Quarto / Pandoc
                           ▼
┌─────────────────────────────────────────────────────────────┐
│              [KHỐI THỰC THI – EXECUTORS]                    │
│  Streamlit App  ·  CI Scripts ·  Docker                     │
│  Render · Kiểm thử · Phân phối học liệu                     │
└─────────────────────────────────────────────────────────────┘
