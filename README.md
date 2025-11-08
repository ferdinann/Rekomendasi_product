# Laporan Proyek Machine Learning - Ferdinanta Ginting

## Project Overview

Di era digital saat ini, e-commerce telah menjadi bagian tak terpisahkan dari kehidupan kita. Kemudahan berbelanja secara online, pilihan produk yang beragam, dan harga yang kompetitif menjadi daya tarik utama bagi konsumen [1]. Hal ini mendorong pertumbuhan e-commerce yang sangat pesat, termasuk di Indonesia. Namun, dengan semakin banyaknya produk yang tersedia di platform e-commerce, konsumen seringkali merasa kesulitan untuk menemukan produk yang benar-benar sesuai dengan kebutuhan dan minat mereka. Terlalu banyak pilihan dapat menyebabkan information overload, yang pada akhirnya membuat konsumen merasa kewalahan dan kesulitan dalam mengambil keputusan [2].

Manfaat Sistem Rekomendasi dalam E-commerce
- Meningkatkan Kepuasan Pengguna: Dengan memberikan rekomendasi yang relevan, sistem ini membantu pengguna menemukan produk yang mereka butuhkan dengan lebih mudah dan cepat [3].
- Personalisasi Pengalaman Pengguna: Sistem rekomendasi memungkinkan platform e-commerce untuk menawarkan pengalaman berbelanja yang lebih personal bagi setiap pengguna. Rekomendasi yang diberikan disesuaikan dengan minat dan preferensi masing-masing pengguna, sehingga membuat pengalaman berbelanja menjadi lebih relevan dan menarik [3].
- Sistem rekomendasi adalah sebuah teknologi yang dirancang untuk membantu pengguna menemukan informasi atau produk yang relevan dengan preferensi mereka. Dalam konteks e-commerce, sistem rekomendasi dapat memberikan saran produk yang dipersonalisasi berdasarkan riwayat pembelian, preferensi pengguna, dan data lainnya [4].

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
    - Membuat sistem rekomendasi berdasarkan 10 produk terlaris dari produk yang berbeda-beda (Demographic Filtering)
    - Membuat sistem rekomendasi dengan pendekatan content based filtering yang menghitung kesamaan antara masing-masing content.
    - Membuat model based filtering untuk pengguna baru menggunkan algoritma clustering.
    - Menggabungkan model based(clustering) dengan content based filtering diatas dengan pendekatan Hybrid recommender system (Mixed)

## Data Understanding
[Data E-commerce Product Elektronic](https://www.kaggle.com/datasets/ferdinantaginting/data-product).

Data yang digunakan berasal dari kaggle dengan jumlah 9 kolom dan 885129 baris data. Empat feature adalah numerik dengan 3 type data int dan 1 lainnya adalah float dan 5 sisanya adalah type data object. Kondisi data masih cukup kotor dimana terdapat banyak data null saat pengecekan dengan isnull.sum dan juga banyak data duplicate saat pengecekan dengan duplicate.sum. 

**Data Exploration:**
- **Menampilkan jumlah data unik pada setiap feature pada data:** Mengetahui berapa banyak nilai berbeda yang terdapat dalam setiap kolom dataset. Ini memberikan wawasan tentang variasi data.
- **Menampilkan data unik pada kolom 'event_type':** Melihat nilai-nilai spesifik yang ada dalam kolom 'event_type', yang mungkin merepresentasikan jenis interaksi pengguna.
- **Menampilkan nilai unik pada setiap kolom dalam dataset:** Mendapatkan daftar semua nilai unik untuk setiap kolom, memberikan pemahaman mendalam tentang isi data.

#### Variabel-variabel pada E-commerce Product Elektronic dataset adalah sebagai berikut:
- event_time : merupakan waktu saat melakukan aksi pada aplikasi seperti waktu pembelian, menambahkan ke keranjang, dan melihat produk.
- event_type : merupakan jenis aksi yang dilakukan seperti pembelian, menambahkan ke keranjang, dan melihat produk.
- product_id : merupakan id atau kode unik setiap produk.
- category_id : merupakan id atau kode unik untuk setiap kategori produk.
- category_code : merupakan kategori, subkategori dan nama produk yang digabung dan dipisahkan dengan tanda titik dalam satu feature.
- brand : merupakan nama brand untuk setiap produk.
- price : merupakan harga untuk setiap produk yang ada pada aplikasi.
- user_id : merupakan id atau kode unik yang membedakan user 1 dengan user lainnya.
- user_session : merupakan sesi atau kode unik untuk aktivitas yang dilakukan user.

- Melakukan beberapa tahapan yang diperlukan untuk memahami data seperti menampilkan deskripsi data, informasi data, teknik visualisasi data beserta insight atau exploratory data analysis dan juga memeriksa missing value dan duplicate data.

## Data Preparation

**Handling Missing Values:**
- **Menghapus data null pada semua baris data:** Menghilangkan baris-baris yang mengandung setidaknya satu nilai null. Tindakan ini dilakukan untuk memastikan kualitas data yang akan dianalisis lebih lanjut.
- **Mengecek apakah masih ada data null:** Verifikasi setelah penghapusan untuk memastikan tidak ada lagi nilai null yang tersisa dalam dataset.

**Handling Duplicates:**
- **Menghapus data duplicate:** Menghilangkan baris-baris yang terduplikasi, menjaga hanya satu kemunculan dari setiap data yang unik.
- **Memverifikasi penghapusan data duplikat:** Memastikan bahwa proses penghapusan duplikat telah berhasil dan tidak ada lagi baris yang identik.

**Data Transformation:**
- **Membuat fungsi untuk memisahkan feature category_code menjadi 3 bagian berdasarkan karakter titik dan membuat 3 feature baru (kategori, subcategory, dan product):** Melakukan *feature engineering* dengan memecah informasi yang terkandung dalam satu kolom menjadi beberapa kolom yang lebih spesifik dan mudah dianalisis.
- **Mengubah event_type menjadi rating:** Mentransformasikan kolom 'event_type' menjadi skala numerik yang merepresentasikan 'rating'. Ini mungkin dilakukan untuk mempersiapkan data untuk algoritma yang memerlukan input numerik.
- **Memilih data dengan panjang data split yang sama dengan 3:** Memfilter data berdasarkan hasil pemisahan 'category_code', kemungkinan untuk memastikan konsistensi struktur kategori.
- **Menghapus kolom category_id dan category_code:** Menghilangkan kolom-kolom yang dianggap tidak relevan setelah proses transformasi atau karena redundansi informasi.

**Penyiapan Data untuk Modeling (Demographic Filtering):**
- **Menghapus beberapa feature yang tidak diperlukan dalam menentukan product Best Seller** diantaranya adalah 'event_type', 'category', 'user_id', 'event_time', 'user_session'
- **Menginisialisasi variabel untuk menyimpan data yang sudah difilter:** Membuat wadah untuk menyimpan subset data yang telah diproses dan siap digunakan untuk pemodelan.
- **Menyimpan 10 nama produk terlaris dalam variabel recomBS:** Mengidentifikasi dan menyimpan nama dari 10 produk dengan jumlah pembelian tertinggi. Ini kemungkinan akan digunakan sebagai dasar rekomendasi.
- **Menginisialisasi variabel untuk produk dengan nilai yang sama seperti recomBS:** Membuat variabel yang berisi data terkait dengan 10 produk terlaris.
- **Menghapus feature "rating":** Menghilangkan kolom 'rating', kemungkinan karena tidak relevan untuk pendekatan *Demographic filtering* pada tahap ini.
- **Menghapus data duplicate dan menampilkan data unik:** Memastikan bahwa data yang akan digunakan untuk pemodelan *Demographic filtering* bebas dari duplikasi dan hanya berisi item-item yang unik.

**Penyiapan Data untuk Cluster Based Algorithm (Model Based):**
- **Menghapus beberapa feature yang tidak digunakan dalam membuat model based** diantaranya adalah 'event_type', 'event_time', 'user_session', 'category', 'rating', 'price'
- **Mengencoding feature non numerik menjadi numerik untuk clustering:** Mengubah kolom-kolom yang berisi data kategorikal (teks) menjadi format numerik yang dapat diproses oleh algoritma *clustering*. Teknik seperti *label encoding* atau *one-hot encoding* mungkin digunakan.
- **Standardisasi data agar memiliki skala yang sama:** Menerapkan penskalaan fitur dengan StandardScaler untuk memastikan bahwa semua fitur memiliki rentang nilai yang serupa. Ini penting agar fitur dengan nilai yang lebih besar tidak mendominasi perhitungan jarak dalam algoritma *clustering*.
- **Menentukan jumlah kluster yang optimal:** Menggunakan metode visualisasi dengan *elbow method* untuk membantu menentukan jumlah kluster yang paling sesuai untuk data.

**Penyiapan Data untuk Modeling (Content Based Filtering):**
- Menghapus beberapa feature yang tidak digunakan untuk rekomendasi content base filtering.
- Menghapus data duplicate
- Encode feature non numerik menjadi numerik dengan LabelEncoder.

**Penyiapan Data untuk Modeling (Hybrid Recommender System (Mixed)
):**
- Menghapus feature cluster untuk menyeragamkan jumlah feature dan nama nama feature pada setiap model rekomendasi yang dibuat.
- Menggabungkan metode rekomendasi clustering dengan content based filtering.

## Modeling
Model yang dibangun untuk menyelesaikan permasalahan ini dibuat dengan membangun 4 algoritma yang berbeda diantaranya adalah :

1. Demographic Filtering
- prinsip kerja  : Memfilter produk atau data yang paling sering dibeli(best seller)
- cara kerja : Menghitung jumlah keseluruhan produk yang dibeli dan mengurutkannya berdasarkan nilai tertinggi
- tahapan :
   - filter produk yang pernah dibeli
   - Hitung jumlah kejadian pembelian
   - tampilkan 10 produk teratas
- Kelebihan:
   - Pendekatan ini sederhana dan mudah diterapkan karena hanya memerlukan data statistik seperti produk yang paling sering dibeli (best seller) tanpa perlu data pribadi pengguna.
   - Cocok digunakan untuk pengguna baru (cold-start user) karena tidak memerlukan riwayat interaksi pengguna sebelumnya.
   - Dapat memberikan rekomendasi populer yang cenderung disukai oleh banyak orang, sehingga meningkatkan kemungkinan interaksi awal pengguna.
- Kekurangan:
   - Rekomendasi yang dihasilkan bersifat umum dan tidak personal, karena semua pengguna mendapatkan saran produk yang sama.
   - Tidak mempertimbangkan preferensi individu, minat, atau perilaku pengguna tertentu.
   - Cenderung mengabaikan keberagaman produk, yang dapat menyebabkan fenomena popularity bias (produk terkenal direkomendasikan berulang kali).
- Output
				
| index| product_id | brand | price | subcategory | product |
|----------|----------|----------|---------|----------|------|
|420038	|779865	|asus	|268.06	|components	|videocards|
|399626	|494235	|hi-black|	10.52	|peripherals	|printer|
|369024	|4101537 |	asus|	307.43	|components	|videocards|
|538197	|4155387 |	sapphire|	213.11	|components	|videocards|
|368787	|3961720 |	msi	 |572.57	|components	|videocards|
|25880	|1044429 |	pioneer|	96.35	|accessories|	player|
|656288	|4079108 | 	asus	|489.54	|components	|videocards|
|73050	|125338	 |creative	|57.46	|audio	|acoustic|
|6881	|136700	| asrock	|77.73	|components	|motherboard|
|613358	|4101560 |	asus	|509.54	|components	|videocards|

2. Clustering
- prinsip kerja : mengelompokkan produk yang memiliki jarak terdekat
- cara kerja : menginisialisasi jumlah centroid yang akan menjadi pusat pengelompokan data yang terdekat dengan centroid
- tahapan
  - Meng Encode feature non numerik menjadi numerik
  - Standarisasi data agar memiliki skala yang sama
  - Menampilkan jumlah centroid yang optimal dengan elbow method
  - latih model
  - simpan model dengan joblib
- Kelebihan:
  - Dapat mengelompokkan produk atau pengguna berdasarkan kemiripan fitur sehingga memungkinkan pembentukan pola perilaku yang lebih kompleks.
  - Memungkinkan sistem untuk merekomendasikan produk serupa kepada pengguna dengan preferensi yang sama, bahkan tanpa interaksi eksplisit antar pengguna.
  - Mengurangi kompleksitas data dengan membagi pengguna atau item ke dalam kelompok yang lebih homogen.
- Kekurangan:
  - Hasil rekomendasi sangat bergantung pada kualitas dan hasil preprocessing (seperti encoding dan standardisasi).
  - Sulit menangani data dinamis karena perubahan preferensi pengguna bisa membuat model cepat usang.
  - Pemilihan jumlah cluster yang tidak optimal dapat mengakibatkan hasil rekomendasi yang tidak akurat.
- output
  - Top 10 produk dengan cluster yang sama dengan product "cooler"
    
| product_id | brand | user_id | subcategory  | product | cluster|
|------------|-------|---------|--------------|----------|------|
|139905.0   |zalman  |1.515916e+18   |components       |cooler |0 |
|635807.0   |pantum  |1.515916e+18  |peripherals    | printer    |0 |
|664325.0  | carver | 1.515916e+18  |  tools   |   saw  |   0 |
|716611.0 |  d-link  |1.515916e+18 |  network  |  router  |    0 |
|716611.0 |  d-link | 1.515916e+18 |  network |  router |   0 |
|1080093.0 |  ricoh | 1.515916e+18 | peripherals |  printer| 0 |
|1455459.0  | sony | 1.515916e+18|   video| tv  |  0 |
|3537266.0 | kenwood | 1.515916e+18 | accessories | player | 0 |
|523117.0 | asrock | 1.515916e+18 |  components | motherboard | 0 |
|10914.0 | sony | 1.515916e+18|  camera | video    |   0 |


3. Item based filtering
- prinsip kerja : Membuat persentasi kemiripan item dengan item lainnya dengan skala 0-1
- cara kerja : mencari item yang memiliki kemiripan dengan produk yang dilihat
- tahapan
  - Meng Encode feature non numerik menjadi numerik
  - memanggil fungsi cosine similarity yang telah di import sebelumnya dan menambahkan dataset sebagai parameternya.
-  Kelebihan:
  - Memberikan rekomendasi yang relevan dan spesifik berdasarkan kesamaan konten produk (seperti merek, kategori, atau harga).
  - Dapat berfungsi dengan baik untuk pengguna dengan riwayat interaksi terbatas, karena sistem hanya membutuhkan informasi dari produk yang disukai pengguna sebelumnya.
  - Menghindari masalah cold-start untuk pengguna baru yang sudah memberikan sedikit interaksi awal terhadap produk tertentu.
- Kekurangan:
  - Cenderung menghasilkan rekomendasi yang monoton karena sistem terus merekomendasikan produk dengan karakteristik serupa (overspecialization problem).
  - Tidak memperhitungkan faktor sosial atau tren pasar yang mungkin berpengaruh terhadap preferensi pengguna.
  - Membutuhkan representasi fitur produk yang baik; jika fitur tidak informatif, performa sistem akan menurun.
- output
  - Top 5 produk yang memiliki kemiripan dengan produk "printer"

| index | brand    | subcategory | product |
|-------|----------|-------------|---------|
|952	|eurolux   | tools	     |welding  |
|636743	|chieftec  |components   |power_supply|
|63076	|cougar    |components   |power_supply|
|29389	|fubag     |tools        |welding|
|1619	|greenworks|tools	     |wrench|


2. Hybrid filtering (Mixed)
- prinsip kerja : menggabungkan beberapa hasil rekomendasi
- cara kerja : menggabungkan beberapa hasil rekomendasi dari berbagai strategi
- tahapan
  - membuat fungsi untuk menggabungkan hasil rekomendasi antara clustering dan content based filtering
- Kelebihan:
  - Menggabungkan kelebihan beberapa metode (dalam hal ini clustering dan content-based filtering) untuk menghasilkan rekomendasi yang lebih akurat dan seimbang.
  - Mengurangi kelemahan masing-masing pendekatan, misalnya mengatasi popularity bias dari demographic filtering dan overspecialization dari content-based filtering.
  - Dapat meningkatkan metrik performa seperti recall, NDCG, dan diversity, karena sistem mempertimbangkan berbagai sumber informasi.
  - Lebih fleksibel untuk diterapkan pada berbagai jenis data dan skenario pengguna, baik pengguna baru maupun lama.
- Kekurangan:
  - Kompleksitas implementasi lebih tinggi dibandingkan pendekatan tunggal, karena memerlukan integrasi antar model dan sinkronisasi output rekomendasi.
  - Membutuhkan waktu komputasi dan sumber daya yang lebih besar dalam proses pelatihan dan evaluasi.
  - Sulit untuk menyeimbangkan kontribusi dari tiap metode dalam sistem gabungan, sehingga tuning parameter menjadi lebih rumit.
- output
  - Top 10 produk rekomendasi berdasarkan referensi produk "tv"

|index|product_id| brand |user_id	|subcategory| product |
|-----|----------|-------|--------|-----------|---------|
|0	|139905.0|	zalman|	1.515916e+18|	components|	cooler|
|1	|635807.0	|pantum|	1.515916e+18|	peripherals	|printer|
|2	|664325.0|	carver|	1.515916e+18|	tools	|saw|
|3	|716611.0|	d-link|	1.515916e+18|	network|	router|
|6	|1455459.0|	sony|	1.515916e+18|	video|	tv|
|7	|3537266.0|	kenwood|	1.515916e+18|	accessories|player|
|8	|523117.0|	asrock|	1.515916e+18|	components	|motherboard|
|9	|10914.0|	sony|	1.515916e+18|	camera|	video|
|10	|3828758.0|	eva	|1.515916e+18|	audio|	acoustic|
|11	|1507291.0|	supermicro|	1.515916e+18|components|power_supply|


## Evaluation
Metrik evaluasi yang digunakan adalah antara lain :

1. Silhouette Score
2. Davies-Bouldin Index
3. Calinski-Harabasz Index
4. Presisi
5. Recall
6. Precision@k
7. Recall@k
8. Mean Reciprocal Rank (MRR)
9. Hit Rate@k
10. Normalized Discounted Cumulative Gain@k (NDCG@k)
11. Diversity

Metrik evaluasi untuk Model based (clustering)
| Silhouette Score | Davies-Bouldin Index | Calinski-Harabasz Index |
|----------|----------|----------|
| 0.7225198528080168 | 0.347105893653442 | 1096950.5421773233 |


Metrik evaluasi untuk content based filtering
| Presisi | Recall |
|---------|--------|
| 1.00 | 0.80 |

Metrik evaluasi untuk Hybrid Recommendation filtering
| Precision@k | Recall@k | MRR | Hit Rate@k | NDCG@k | Diversity |
|---------|--------|---------|--------|---------|--------|
| 0.1000 | 1.0000 | 0.3819 | 1.0000 | 0.5220 | 0.8774 |

- Penjelasan mengenai metrik yang digunakan
  - Silhouette Score mengukur seberapa mirip suatu objek dengan kelompoknya sendiri (kohesi) dibandingkan dengan kelompok lain (separasi). Skor ini berkisar antara -1 hingga +1.
  - Davies-Bouldin Index mengukur rata-rata kemiripan setiap kelompok dengan kelompok yang paling mirip dengannya. Skor yang lebih rendah menunjukkan clustering yang lebih baik, di mana kelompok-kelompoknya padat dan terpisah dengan baik.
  - Calinski-Harabasz Index mengukur rasio antara varians antar kelompok (between-cluster variance) dan varians dalam kelompok (within-cluster variance). Skor yang lebih tinggi menunjukkan clustering yang lebih baik, di mana kelompok-kelompoknya padat dan terpisah dengan baik.
  - precision adalah metrik yang mengukur seberapa akurat model dalam memprediksi kelas positif
  - recall adalah metrik yang Mengukur seberapa baik model dalam mengidentifikasi semua kasus positif yang
  - Precision@k (P@k): Mengukur proporsi item dalam k rekomendasi teratas yang relevan bagi pengguna.
  - Recall@k (R@k): Mengukur proporsi item relevan yang berhasil direkomendasikan dalam k rekomendasi teratas.
  - Mean Reciprocal Rank (MRR): Mengukur peringkat rata-rata dari rekomendasi relevan pertama untuk setiap pengguna.
  - Hit Rate@k (HR@k): Mengukur persentase pengguna yang memiliki setidaknya satu item relevan dalam k rekomendasi teratas mereka.
  - Normalized Discounted Cumulative Gain@k (NDCG@k): Mengukur kualitas peringkat rekomendasi dengan mempertimbangkan relevansi setiap item dan posisinya, dinormalisasi terhadap DCG ideal.
  - Diversity: Mengukur seberapa berbeda item-item dalam daftar rekomendasi satu sama lain, biasanya berdasarkan fitur-fitur item.

- Formula metriks yang digunakan
1. Silhouette Score

- Formula untuk seluruh clustering (S):

#### S = sum(s(i) for i in semua_objek) / N

Keterangan:

sum(ekspresi for item in koleksi): Notasi untuk menjumlahkan hasil dari ekspresi untuk setiap item dalam koleksi.
semua_objek: Kumpulan semua objek dalam dataset.
N: Jumlah total objek.

2. Davies-Bouldin Index

- Formula untuk kemiripan antar kelompok (R_ij):

#### R_ij = (S_i + S_j) / d(centroid_i, centroid_j)

Keterangan:

S_i: Rata-rata jarak objek dalam kelompok i ke centroid kelompok i.
S_j: Rata-rata jarak objek dalam kelompok j ke centroid kelompok j.
centroid_i: Vektor yang merepresentasikan pusat kelompok i.
centroid_j: Vektor yang merepresentasikan pusat kelompok j.
d(p1, p2): Fungsi untuk menghitung jarak antara dua titik (p1 dan p2).

- Formula untuk Davies-Bouldin Index (DB):

#### DB = sum(D_i for i in semua_kelompok) / k
Keterangan:

k: Jumlah total kelompok.

3. Calinski-Harabasz Index

Formula untuk Calinski-Harabasz Index (CH):

#### CH = ((N - k) / (k - 1)) * (SS_B / SS_W)

Keterangan:

N: Jumlah total objek.
k: Jumlah total kelompok.

4. Precicion = TP / (TP + FP)

5. Recall = TP / (TP + FN)

- Penjelasan :

   - TP = True Positive
   - TN = True Negative
   - FN = False Negative
   - FP = False Positive
6. Precision@k (P@k) = (Jumlah item relevan dalam k rekomendasi teratas) / k
7. Recall@k (R@k) = (Jumlah item relevan dalam k rekomendasi teratas) / (Jumlah total item relevan)
8. Mean Reciprocal Rank (MRR) = SUM(1 / rank_i untuk setiap pengguna i) / (Jumlah total pengguna)
9. Hit Rate@k (HR@k) = (Jumlah pengguna yang memiliki setidaknya 1 item relevan dalam k rekomendasi) / (Jumlah total pengguna)
10. Normalized Discounted Cumulative Gain@k (NDCG@k) = DCG_k / IDCG_k
   - dengan
	DCG_k = SUM(rel_i / log2(i + 1) untuk i dari 1 sampai k)
	IDCG_k = DCG_k ideal (relevansi tertinggi di peringkat teratas)

11. Diversity = AVERAGE(dissimilarity(item_i, item_j) untuk semua pasangan item i dan j dalam rekomendasi)

- Berdasarkan model yang telah dibuat dan di evaluasi maka problem statement yang telah dibuat sebelumnya sudah terjawab dan juga telah mencapai goals yang diharapkan

    - Sistem rekomendasi berdasarkan 10 produk terlaris dari produk
    - Sistem rekomendasi yang menghitung kesamaan antara masing-masing content.
    - Sistem rekomendasi untuk pengguna baru menggunakan algoritma clustering.
    - Menggabungkan model based(clustering) dengan content based filtering diatas dengan pendekatan Hybrid recommender system (Mixed)
    - Berdasarkan ke-11 metrik yang digunakan setelah di evaluasi maka semua model memiliki performa baik tetapi yang memiliki metrik evaluasi yang paling bagus dari semuanya adalah model content based filtering dengan presisi 1.0 dan recall 0.8.

 - Kesimpulan Evaluasi model Hybrid recommendation system:

	Model ini cenderung "luas" dalam rekomendasinya. Ia berhasil mencakup semua item yang relevan (recall dan hit rate tinggi), dan ketika merekomendasikan item relevan, item 	tersebut cenderung berada di peringkat yang baik (MRR dan NDCG lumayan). Namun, model juga merekomendasikan banyak item yang tidak relevan, yang menyebabkan presisi yang rendah. Keragaman yang tinggi bisa menjadi penyebab presisi rendah jika model terlalu mengeksplorasi item yang tidak disukai pengguna.
- Solution statement yang direncanakan berdampak karena melalui berbagai model yang dibangun dapat dilihat bahwa setiap model memiliki hasil evaluasi yang beragam sehingga model yang dibangun bisa di evaluasi dan dibandingkan dengan lainnya sehingga mempermudah pemilihan model yang tepat untuk menyelesaikan permasalahan tetapi tidak semua metode rekomendasi membutuhkan metrik evaluasi seperti model Demographic filtering yang sudah akurat dengan perhitungan manual saja.

## Daftar Pustaka
- [1] K. Choi, D. Yoo, G. Kim, and Y. Suh, “A hybrid online-product recommendation system: combining implicit rating-based collaborative filtering and sequential pattern analysis,” Electron. Commer. Res. Appl., vol. 11, no. 4, pp. 309-317, Jul. 2012. 
- [2] “Recommender system,” Wikipedia. [Online]. Available: https://en.wikipedia.org/wiki/Recommender_system. [Accessed: Nov. 7, 2025].
- [3] G. Adomavicius and A. Tuzhilin, “Toward the next generation of recommender systems: a survey of the state-of-the-art and possible extensions,” IEEE Trans. Knowl. Data Eng., vol. 17, no. 6, pp. 734-749, Jun. 2005. 
- [4] “Hybrid Quality-Based Recommender Systems: A Systematic Literature Review,” X. vol. 11, no. 1, pp. 12, 2024. 
MDPI
