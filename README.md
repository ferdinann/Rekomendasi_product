# Laporan Proyek Machine Learning - Ferdinanta Ginting

## Project Overview

Di era digital saat ini, e-commerce telah menjadi bagian tak terpisahkan dari kehidupan kita. Kemudahan berbelanja secara online, pilihan produk yang beragam, dan harga yang kompetitif menjadi daya tarik utama bagi konsumen. Hal ini mendorong pertumbuhan e-commerce yang sangat pesat, termasuk di Indonesia.
Namun, dengan semakin banyaknya produk yang tersedia di platform e-commerce, konsumen seringkali merasa kesulitan untuk menemukan produk yang benar-benar sesuai dengan kebutuhan dan minat mereka. Terlalu banyak pilihan dapat menyebabkan information overload, yang pada akhirnya membuat konsumen merasa kewalahan dan kesulitan dalam mengambil keputusan.

Manfaat Sistem Rekomendasi dalam E-commerce
- Meningkatkan Kepuasan Pengguna: Dengan memberikan rekomendasi yang relevan, sistem ini membantu pengguna menemukan produk yang mereka butuhkan dengan lebih mudah dan cepat. Hal ini meningkatkan pengalaman berbelanja pengguna dan kepuasan mereka terhadap platform e-commerce.
- Meningkatkan Penjualan: Rekomendasi produk yang tepat dapat mendorong pengguna untuk membeli lebih banyak produk. Sistem rekomendasi juga dapat membantu meningkatkan penjualan produk produk yang kurang populer atau produk baru yang mungkin belum diketahui oleh pengguna.
- Meningkatkan Loyalitas Pelanggan: Pengalaman berbelanja yang positif dan personalisasi yang ditawarkan oleh sistem rekomendasi dapat meningkatkan loyalitas pelanggan terhadap platform - e-commerce. Pelanggan yang puas cenderung akan kembali berbelanja di platform tersebut.
- Personalisasi Pengalaman Pengguna: Sistem rekomendasi memungkinkan platform e-commerce untuk menawarkan pengalaman berbelanja yang lebih personal bagi setiap pengguna. Rekomendasi yang diberikan disesuaikan dengan minat dan preferensi masing-masing pengguna, sehingga membuat pengalaman berbelanja menjadi lebih relevan dan menarik.

- Pentingnya Sistem Rekomendasi
Di sinilah sistem rekomendasi berperan penting. Sistem rekomendasi adalah sebuah teknologi yang dirancang untuk membantu pengguna menemukan informasi atau produk yang relevan dengan preferensi mereka. Dalam konteks e-commerce, sistem rekomendasi dapat memberikan saran produk yang dipersonalisasi berdasarkan riwayat pembelian, preferensi pengguna, dan data lainnya.
- Choi, K., Yoo, D., Kim, G., & Suh, Y. (2012). A hybrid online-product recommendation system: Combining implicit rating-based collaborative filtering and sequential1 pattern analysis. Journal of Electronic Commerce in Organizations, 10(1), 1-18.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

## Business Understanding

### Problem Statements

- Overload Informasi: Konsumen seringkali kesulitan menemukan produk yang sesuai dengan kebutuhan mereka di antara banyaknya pilihan yang tersedia di platform e-commerce.
- Konsumen sering kali tertarik membeli produk yang banyak dibeli orang (best seller).
- Kurangnya Personalisasi: Pengalaman berbelanja yang ditawarkan oleh platform e-commerce seringkali bersifat umum dan tidak disesuaikan dengan preferensi masing-masing pengguna.
- Pengguna Baru: Konsumen yang baru menggunakan e-commerce tersebut mungkin kesulitan memilih produk yang sesuai dengan preferensi nya.

### Goals

- Mengembangkan sistem rekomendasi yang dapat menyaring informasi produk yang relevan dengan kebutuhan dan minat konsumen, sehingga memudahkan mereka dalam menemukan produk yang dicari.
- Menyediakan rekomendasi produk yang paling banyak dibeli (best seller) kepada pengguna.
- Menyediakan rekomendasi produk yang dipersonalisasi berdasarkan brand, price, produk dan data lainnya, sehingga menciptakan pengalaman berbelanja yang lebih relevan dan menarik bagi setiap konsumen.
- Membantu konsumen menemukan produk-produk yang sesuai dengan refrensi mereka sehingga mencegah overload informasi atau produk yang ditampilkan


    ### Solution statements
    - Membuat sistem rekomendasi berdasarkan 10 produk terlaris dari brand dan harga yang berbeda-beda (Demographic Filtering)
    - Membuat sistem rekomendasi dengan pendekatan item based filtering yang menghitung kesamaan antara masing-masing item.
    - Membuat model based filtering untuk pengguna baru menggunkan algoritma clustering.
    - Menggabungkan ke-3 metode sistem rekomendasi diatas dengan pendekatan Hybrid recommender system (Mixed)

## Data Understanding
[Data E-commerce Product Elektronic](https://www.kaggle.com/datasets/ferdinantaginting/data-product).

Data yang digunakan berasal berasal dari kaggle dengan jumlah 9 kolom dan 88512 baris data. Empat feature adalah numerik dengan 3 type data int dan 1 lainnya adalah float dan 5 sisanya adalah type data object. Kondisi data masih cukup kotor dimana terdapat banyak data null dan juga data duplicate. 

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- event_time : merupakan waktu saat melakukan aksi pada aplikasi seperti waktu pembelian, menambahkan ke keranjang, dan melihat produk.
- event_type : merupakan jenis aksi yang dilakukan seperti pembelian, menambahkan ke keranjang, dan melihat produk.
- product_id : merupakan id atau kode unik setiap produk.
- category_id : merupakan id atau kode unik untuk setiap kategori produk.
- category_code : merupakan kategori, subkategori dan nama produk yang digabung dan dipisahkan dengan tanda titik dalam satu feature.
- brand : merupakan nama brand untuk setiap produk.
- price : merupakan harga untuk setiap produk yang ada pada aplikasi.
- user_id : merupakan id atau kode unik yang membedakan user 1 dengan user lainnya.
- user_session : merupakan sesi atau kode unik untuk aktivitas yang dilakukan user.

- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
