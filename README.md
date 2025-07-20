# IBM-Granite

# Analisis Sentimen Ulasan Pelanggan terhadap Produk di Aplikasi Tokopedia menggunakan LLM IBM Granite
<img width="364" height="138" alt="image" src="https://github.com/user-attachments/assets/0748c152-5d6c-4677-b46b-cde679f56f0a" />



![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-2.x-blue.svg)
![Matplotlib](https://img.shields.io/badge/matplotlib-3.x-blue.svg)
![Seaborn](https://img.shields.io/badge/seaborn-0.12.x-blue.svg)
![IBM WatsonX](https://img.shields.io/badge/IBM-WatsonX-blue.svg)

Proyek ini merupakan *capstone project* yang bertujuan untuk melakukan analisis sentimen pada dataset ulasan produk. Analisis ini memanfaatkan kemampuan *Large Language Model* (LLM), yaitu **IBM Granite**, untuk mengklasifikasikan setiap ulasan ke dalam sentimen Positif, Negatif, atau Netral.

## 📝 Latar Belakang Proyek

Memahami suara pelanggan adalah kunci bagi bisnis untuk berkembang. Ulasan produk yang dibiarkan menumpuk tanpa dianalisis adalah sebuah kehilangan potensi. Proyek ini mencoba menjawab pertanyaan:
* Bagaimana sentimen umum pelanggan terhadap produk berdasarkan ulasan mereka?
* Apa saja tema atau kata kunci utama yang muncul dalam ulasan positif dan negatif?
* Apakah ada korelasi antara rating bintang yang diberikan pelanggan dengan sentimen yang terkandung dalam teks ulasan mereka?

## 💾 Dataset

Dataset yang digunakan dalam proyek ini adalah `product_reviews_dirty.csv`, yang berisi ulasan produk dari berbagai platform. Kolom utama yang digunakan adalah:
* `review_text`: Teks ulasan yang ditulis oleh pelanggan.
* `rating`: Rating bintang (1-5) yang diberikan oleh pelanggan.

Dataset awal bersifat "kotor" dan mengandung sekitar 1000 baris data ulasan yang kosong, yang kemudian dibersihkan pada tahap pra-pemrosesan.

## 🛠️ Teknologi yang Digunakan

* **Bahasa Pemrograman:** Python 3.10+
* **Library Analisis Data:** Pandas
* **Library Visualisasi:** Matplotlib & Seaborn
* **Library Pemrosesan Teks:** Scikit-learn (untuk N-gram) & WordCloud
* **Platform & Model AI:** IBM WatsonX dengan model `ibm/granite-8b-instruct`

## ⚙️ Metodologi Proyek

Proyek ini dilaksanakan melalui beberapa tahapan utama:

1.  **Pra-pemrosesan Data:** Memuat dataset, memeriksa struktur data, dan membersihkan baris data yang tidak memiliki teks ulasan.
2.  **Pengambilan Sampel:** Mengambil sampel acak sebanyak 200 ulasan dari data yang sudah bersih untuk dianalisis guna efisiensi proses.
3.  **Analisis Sentimen dengan LLM:**
    * Setiap teks ulasan dari sampel dikirim sebagai *prompt* ke model **IBM Granite** melalui API IBM WatsonX.
    * Prompt dirancang untuk menginstruksikan model agar mengklasifikasikan teks ke dalam kategori 'Positif', 'Negatif', atau 'Netral'.
    * Hasil klasifikasi dari model disimpan dalam kolom baru di tabel data.
4.  **Visualisasi dan Interpretasi:** Hasil analisis kemudian divisualisasikan untuk menemukan pola dan wawasan yang bermakna.

## 📊 Hasil dan Visualisasi

Berikut adalah beberapa hasil visualisasi utama dari analisis yang telah dilakukan:

### Distribusi Sentimen
Diagram ini menunjukkan persentase keseluruhan dari setiap sentimen dalam sampel data.

<img width="653" height="730" alt="image" src="https://github.com/user-attachments/assets/cfbba87d-6f08-44bb-aa1e-6499ee4383d6" />

*Visualisasi ini menunjukkan proporsi sentimen dari sampel ulasan yang dianalisis oleh model IBM Granite. Hasilnya menunjukkan bahwa sentimen pelanggan secara umum sangat baik, dengan 83.5% ulasan diklasifikasikan sebagai Positif. Meskipun demikian, terdapat 15.5% sentimen Negatif  yang menjadi fokus analisis lebih lanjut untuk menemukan potensi perbaikan.*

### Word Clouds (Awan Kata)
Word cloud menyoroti kata-kata yang paling sering muncul, dipisahkan antara ulasan positif dan negatif untuk melihat perbedaan tema.

<img width="1569" height="402" alt="image" src="https://github.com/user-attachments/assets/030b5934-4790-49f9-8e31-7a4f0fc2188b" />

*Word cloud digunakan untuk mengidentifikasi kata kunci yang paling sering muncul secara visual, dipisahkan berdasarkan sentimen untuk melihat perbedaan tema. Ulasan Positif: Kata-kata seperti 'cepat', 'sesuai', 'bagus', dan 'terima kasih' sangat dominan. Ini menunjukkan kepuasan pelanggan berpusat pada kecepatan pengiriman dan kualitas produk yang sesuai ekspektasi. Ulasan Negatif: Kata kunci yang menonjol adalah 'lama', 'kecewa', 'tipis', dan 'pesanan'. Ini mengindikasikan bahwa keluhan utama pelanggan terkait dengan durasi pengiriman dan kualitas produk yang dianggap kurang (misalnya, bahan yang tipis) atau tidak sesuai pesanan.*

### Hubungan Rating dan Sentimen
Heatmap ini membandingkan rating bintang dari pelanggan dengan hasil klasifikasi sentimen dari AI.

<img width="787" height="629" alt="image" src="https://github.com/user-attachments/assets/7e09926b-e197-41ec-a5ce-6c8779c3c69f" />

*Heatmap ini membandingkan antara rating bintang (1-5) yang diberikan pelanggan dengan hasil klasifikasi sentimen dari model AI. Terlihat korelasi yang sangat kuat: Rating tinggi (4 dan 5 bintang) sebagian besar teridentifikasi sebagai Positif oleh AI, dengan total 138 ulasan. Rating rendah (1 dan 2 bintang) berkorelasi kuat dengan sentimen Negatif.Temuan menarik adalah adanya beberapa anomali, seperti satu ulasan dengan rating bintang 5 yang terdeteksi Negatif, yang kemungkinan mengandung sarkasme atau kritik halus yang berhasil ditangkap oleh model*

## 💡 Kesimpulan

Dari analisis yang dilakukan, dapat disimpulkan bahwa:
* Secara umum, sentimen pelanggan terhadap produk cenderung **Positif**.
* Kekuatan utama produk di mata pelanggan adalah **kecepatan pengiriman** dan **kesesuaian produk dengan deskripsi**.
* Area perbaikan utama terletak pada **kualitas bahan produk** (kain tipis, mudah rusak) dan **akurasi estimasi waktu pengiriman**.
* Penggunaan LLM IBM Granite terbukti efektif dalam menangkap nuansa sentimen yang tidak bisa hanya diukur dari rating bintang.

## Project by [IRVAN ALFARITZI] 🚀

Menjelajahi persimpangan antara teknologi, data, dan rasa ingin tahu. Mari terhubung!
---
