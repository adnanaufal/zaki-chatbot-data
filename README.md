# 🤖 ZAKI - Chatbot Konsultasi Zakat Berbasis Hybrid RAG

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![RAG](https://img.shields.io/badge/LLM-RAG-orange?logo=openai)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Development-yellow)

**ZAKI** adalah chatbot cerdas untuk layanan **informasi & konsultasi zakat**
Menggunakan **Hybrid Retrieval-Augmented Generation (RAG)** dengan **knowledge base** dari **Al-Qur’an** dan dokumen resmi BAZNAS, ZAKI mampu menjawab pertanyaan dengan **akurasi tinggi, sumber terpercaya, dan perhitungan zakat otomatis**.

---

## ✨ Fitur Utama
- 🔍 **Hybrid Search** — Kombinasi *semantic search* dan *keyword search* untuk hasil pencarian lebih relevan.
- 📚 **Knowledge Base Resmi** — Sumber dari Al-Qur’an (terjemahan), fatwa MUI, dan dokumen BAZNAS.
- 📊 **Kalkulator Zakat Otomatis** — Menghitung zakat maal, perdagangan, pertanian, dll. langsung dari pertanyaan.
- 🌐 **Bahasa Indonesia & Islami** — Model NLP dioptimalkan untuk Bahasa Indonesia dan terminologi zakat.
- 🛡 **Konten Aman** — Filtering & validasi sumber agar sesuai syariah.
- ⚡ **Integrasi Web** — Siap diintegrasikan ke website BAZNAS.

---

## 🏗 Arsitektur
- **Retriever:** FAISS + BM25
- **LLM Reranker:** IndoBERT + Cross-Encoder
- **Generator:** OpenAI / Local LLM
- **Knowledge Store:** Supabase PostgreSQL (embedding + metadata)

---

## 📂 Dataset
Proyek ini menggunakan dua dataset utama:

| Dataset                | Deskripsi |
|------------------------|-----------|
| `quran_zaki_rows.csv`  | Ayat-ayat Al-Qur’an terkait zakat (terjemahan & referensi) |
| `baznas_docs_rows.csv` | Dokumen regulasi, panduan zakat, fatwa MUI, dan data resmi BAZNAS |

Dataset sudah di-*embedding* menggunakan **IndoBERT**.

---

## 📊 Evaluasi
Model dievaluasi menggunakan **RAGAS** dengan metrik:
- **Faithfulness** — Jawaban sesuai dengan sumber.
- **Answer Relevancy** — Jawaban relevan dengan pertanyaan.
- **Context Recall** — Konteks yang digunakan cukup lengkap.
- **Context Precision** — Konteks tepat sasaran.

## 📊 Evaluasi Kedua (Soon)

Evaluasi sistem dilakukan menggunakan **[RAGAS](https://github.com/explodinggradients/ragas)** (Retrieval-Augmented Generation Assessment Suite) untuk mengukur kualitas sistem RAG secara objektif.

### 📏 Metrik yang Digunakan
1. **Faithfulness**  
   Mengukur sejauh mana jawaban sesuai dengan sumber konteks yang diambil.  
   *Metode:* Membandingkan isi jawaban dengan potongan dokumen yang digunakan (context) untuk mendeteksi *hallucination*.

2. **Answer Relevancy**  
   Mengukur keterkaitan jawaban dengan pertanyaan pengguna.  
   *Metode:* Embedding similarity antara pertanyaan dan jawaban.

3. **Context Recall**  
   Mengukur kelengkapan konteks yang diambil dari sumber data.  
   *Metode:* Perbandingan antara konteks yang digunakan sistem dengan *ground truth*.

4. **Context Precision**  
   Mengukur ketepatan konteks yang diambil — apakah benar-benar relevan dengan pertanyaan.  
   *Metode:* Analisis proporsi konteks yang relevan terhadap semua konteks yang digunakan.

5. **Answer Semantic Similarity (Opsional)**  
   Mengukur kesamaan makna antara jawaban model dan jawaban ideal (*ground truth*).
