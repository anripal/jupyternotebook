# Optimalisasi Strategi Telemarketing dan Prediksi Nasabah Potensial untuk Meningkatkan Convertion Rate Term Deposit
![Alt text](https://github.com/anripal/jupyternotebook/blob/main/TagusBank/Tableau.png)

---

Halo! tolong gunakan file ini sebagai panduan sebelum menjalankan Jupyter Notebook File.

Notebook ini dibuat dengan tujuan akan menjadi portofolio dalam perjalanan saya sebagai Data Analyst. Mohon dimaklumi jika ada kesalahan, saya mencoba yang terbaik!

Kamu bisa kunjungi versi Tableu dari analisis dataset [disini](https://public.tableau.com/app/profile/destaria.anripal/viz/TAGUSBANK-BankTelemarketingCampaign/Dashboard)

Untuk slide presentasi ada [disini.](https://www.canva.com/design/DAGgd0Ozy9Q/dRbt4NSzev-HoHXDNkY3Yw/edit?utm_content=DAGgd0Ozy9Q&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

---

## Konteks
Perbankan di Portugal memainkan peran penting dalam perekonomian dengan menyediakan berbagai layanan keuangan, termasuk produk investasi seperti *term deposit*. Produk ini memberikan keuntungan bagi bank dalam menjaga stabilitas keuangan serta menawarkan opsi investasi berisiko rendah bagi nasabah. Namun, konversi pelanggan ke produk ini masih menjadi tantangan, terutama dalam strategi pemasaran yang dilakukan melalui telemarketing.

Tagus Bank menggunakan strategi telemarketing untuk menawarkan produk term deposit kepada nasabah. Meskipun metode ini memungkinkan bank untuk menjangkau lebih banyak nasabah, efektivitasnya masih diragukan karena banyak panggilan yang tidak menghasilkan konversi. Berdasarkan data, dari total **39,971 nasabah yang dihubungi**, hanya **4,486 nasabah yang menerima tawaran term deposit**, yang menghasilkan **Conversion Rate** sebesar **11%**. Angka ini menunjukkan bahwa sebagian besar nasabah menolak penawaran, menandakan bahwa kampanye telemarketing yang dilakukan belum sepenuhnya efektif dalam meningkatkan konversi. Faktor-faktor seperti status pekerjaan, usia, riwayat kampanye sebelumnya, dan durasi panggilan diduga memiliki pengaruh yang signifikan terhadap keputusan nasabah untuk menerima atau menolak penawaran tersebut.

Masih banyak nya tingkat penolakan ini mengindikasikan bahwa strategi telemarketing saat ini belum optimal dalam meningkatkan *Conversion Rate*. Untuk meningkatkan konversi di kampanye berikut nya, diperlukan pendekatan berbasis data guna mengidentifikasi pola dan karakteristik nasabah yang lebih mungkin menerima penawaran. Dengan memahami faktor-faktor utama yang memengaruhi keputusan nasabah, tim telemarketing dapat menyusun strategi yang lebih tepat sasaran dan meningkatkan peluang konversi.

Oleh karena itu, **Head of Telemarketing** di Tagus Bank meminta tim Data Scientist untuk melakukan analisis data dan membangun model prediktif guna mengoptimalkan strategi pemasaran dan meningkatkan rasio konversi telemarketing. Model ini diharapkan dapat membantu tim telemarketing dalam menentukan kelompok nasabah dengan probabilitas konversi lebih tinggi, sehingga upaya pemasaran dapat lebih efektif dan terarah.

Target:  
- 0: Nasabah menolak penawaran term deposit
- 1: Nasabah menerima penawaran term deposit

## Rumusan Masalah
Strategi telemarketing yang tidak terarah dapat menyebabkan upaya pemasaran kurang efektif, menghabiskan waktu tim telemarketing, dan menurunkan peluang konversi. Saat ini, Tagus Bank menghadapi tantangan dalam meningkatkan conversion rate term deposit, karena kampanye telemarketing masih dilakukan secara luas tanpa mempertimbangkan karakteristik atau riwayat interaksi nasabah.

Jika strategi telemarketing tetap dilakukan secara acak tanpa analisis berbasis data, beberapa permasalahan yang dapat terjadi meliputi:
    
- Conversion Rate dari team Telemarketing tidak meningkat karena aktifitas telemarketing tidak difokuskan ke dataset yang memiliki potensial closing yang lebih besar.
    
- Aktifitas telemarketing yang tidak terarah (Spray and Prey) akan mengakibatkan konversi Nasabah tidak dapat diprediksi dengan baik, sehingga sales Forecast di team Telemarketing akan kurang tepat dan tidak dapat dikontrol.

Dengan adanya analisis yang memahami pola nasabah yang lebih responsif terhadap penawaran serta metode komunikasi yang paling efektif, team telemarketing bisa memprioritaskan aktifitas cold-calling menggunakan metode komunikasi yang lebih efektif dan ke kelompok Nasabah yang memiliki conversion rate tinggi.

Berdasarkan Dataset yang digunakan, sebagian besar Nasabah yang dihubungi team Telemarketing adalah nasabah baru.

## Tujuan
Berdasarkan permasalahan tersebut, Tagus Bank ingin membangun model prediktif untuk mengidentifikasi nasabah dengan probabilitas tinggi menerima penawaran *term deposit*. Dengan model ini, tim telemarketing dapat memprioritaskan panggilan kepada prospek yang lebih potensial, sehingga meningkatkan *conversion rate* dan mengoptimalkan hasil dari setiap kampanye telemarketing. Untuk itu, kita akan melakukan analisis berbasis data dengan menjawab pertanyaan berikut:

1. Bagaimana karakteristik demografis dan finansial nasabah memengaruhi keputusan mereka dalam menerima atau menolak penawaran term deposit?

2. Bagaimana efektivitas strategi kampanye saat ini dalam meningkatkan konversi penawaran term deposit?

3. Sejauh mana riwayat interaksi dan hasil kampanye sebelumnya memengaruhi penawaran term deposit pada kampanye saat ini?

4. Bagaimana kondisi ekonomi makro memengaruhi keputusan nasabah dalam penawaran term deposit?

Selain itu, bank juga ingin mengidentifikasi faktor-faktor utama yang memengaruhi keputusan nasabah dalam menerima atau menolak penawaran. Dengan wawasan ini, strategi telemarketing dapat disesuaikan agar lebih efektif, meningkatkan kualitas interaksi dengan nasabah, dan secara keseluruhan memperbaiki pendekatan pemasaran yang digunakan.

## Pendekatan Analisis
Untuk mengoptimalkan strategi telemarketing, kita akan melakukan analisis data guna mengidentifikasi pola yang membedakan nasabah yang menerima dan menolak penawaran term deposit. Analisis ini mencakup karakteristik demografi dan finansial nasabah, efektivitas kampanye saat ini, hasil kampanye sebelumnya, serta dampak kondisi makroekonomi terhadap keputusan nasabah.

Setelah itu, kita akan membangun model klasifikasi berbasis Supervised Machine Learning untuk memprediksi probabilitas seorang nasabah menerima term deposit. Model ini akan menjadi alat bantu bagi tim telemarketing dalam pengambilan keputusan, sehingga strategi pemasaran lebih terarah dan efektif.

Berikut tahapan analisis dan pengembangan model yang akan dilakukan:
- **Data Cleaning**: Menangani data yang hilang, inkonsisten, atau duplikasi.
- **Exploratory Data Analysis (EDA)**: Memahami pola dalam data melalui visualisasi dan statistik deskriptif.
- **Feature Engineering & Preprocessing**: Mengubah dan menyesuaikan fitur agar optimal untuk model.
- **Benchmarking Model**: Mencoba beberapa algoritma Klasifikasi Supervised Machine Learning untuk menentukan model dengan performa terbaik.
- **Hyperparameter Tuning**: Mengoptimalkan parameter model untuk meningkatkan akurasi prediksi.
- **Model Evaluation & Selection**: Mengevaluasi model dengan metrik yang sesuai dengan tujuan bisnis.
- **Implementation**: Menerapkan model sebagai alat bantu bagi tim telemarketing dalam pengambilan keputusan.

## Metrik Evaluation
![Alt text](https://github.com/anripal/jupyternotebook/blob/main/TagusBank/metrics.png)

Metrik utama yang digunakan adalah Precision agar memastikan bahwa sebagian besar nasabah yang dihubungi memiliki potensi konversi tinggi sehingga tim telemarketing dapat fokus pada nasabah yang lebih mungkin menerima penawaran. Namun, kita juga tetap mempertimbangkan trade-off antara Precision dan Recall. Maka kita menggunakan F0.5-Score sebagai metrik pendukung.

## Kesimpulan
### Data Analisis
Berdasarkan analisis yang dilakukan, dapat disimpulkan bahwa keputusan nasabah untuk menerima atau menolak tawaran term deposit dipengaruhi oleh berbagai faktor. Berikut adalah poin-poin penting dari hasil analisis:

- **Faktor Demografis**
  - Kelompok usia 25-54 tahun memiliki potensi terbesar untuk menerima tawaran, mengingat mereka berada pada usia produktif dan lebih stabil secara finansial.
  - Kelompok usia muda (15-24 tahun) dan usia tua (55-64 tahun dan 65+) cenderung menolak tawaran karena keterbatasan pengalaman finansial atau kesiapan pensiun.
  - Status pekerjaan juga memengaruhi, dengan nasabah yang sudah pensiun atau bekerja di sektor "Blue-collar" memiliki tingkat penolakan tinggi, sementara "Student" lebih terbuka meski cenderung menolak tawaran.

- **Riwayat Kredit**
  - Nasabah tanpa riwayat kredit buruk lebih terbuka terhadap tawaran, sedangkan nasabah dengan riwayat kredit buruk hampir dipastikan menolak tawaran.

- **Kondisi Pasar dan Metode Kontak**
  - Kepemilikan pinjaman dan kondisi pasar perumahan tidak berpengaruh signifikan.
  - Metode kontak melalui ponsel lebih efektif dibandingkan telepon rumah dalam menarik respon positif.

- **Waktu Kampanye**
  - Bulan Maret dan Desember menunjukkan tingkat konversi tertinggi, mungkin terkait dengan kestabilan keuangan setelah pembayaran bonus tahunan.
  - Bulan Mei, Juli, dan November menunjukkan tingkat penerimaan yang lebih rendah, mungkin karena pengeluaran setelah periode belanja besar atau liburan.

- **Hari dalam Seminggu**
  - Hari Kamis adalah yang paling efektif untuk telemarketing dengan tingkat konversi tertinggi.
  - Senin adalah hari dengan konversi terendah, disarankan untuk mengurangi intensitas kampanye pada hari ini.

- **Durasi Telemarketing dan Pengalaman Sebelumnya**
  - Durasi lebih panjang cenderung meningkatkan peluang penerimaan tawaran, meskipun penurunan signifikan terjadi setelah lebih dari 2000 detik.
  - Nasabah yang memiliki pengalaman sukses dengan penawaran sebelumnya lebih cenderung menerima tawaran, sementara mereka yang gagal atau tidak memiliki pengalaman cenderung menolak.

- **Faktor Ekonomi**
  - Indikator ekonomi seperti tingkat pengangguran, inflasi, dan kepercayaan konsumen mempengaruhi penerimaan tawaran. Dalam kondisi ekonomi baik atau inflasi rendah, nasabah lebih terbuka terhadap tawaran.
  - Suku bunga yang tinggi dan jumlah tenaga kerja yang stabil cenderung meningkatkan tingkat penerimaan tawaran.

### Model Machine Learning
1. Algoritma machine learning yang di terapkan selama proses pemodelan untuk mengklasifikasikan nasabah yang menerima penawaran deposito adalah model Logistic Regression dan tidak menggunakan kolom duration. Kolom ini hanya tersedia setelah panggilan telemarketing dilakukan, sehingga tidak cocok digunakan dalam model prediksi yang berbasis data historis.

2. Model terbaik yang dihasilkan memiliki precision score sebesar 0.67, yang berarti dari 1.000 nasabah yang diprediksi sebagai calon yang akan menerima penawaran, sekitar 670 di antaranya benar-benar menerima penawaran tersebut. 

3. Data balancing tidak diterapkan karena model sudah menunjukkan kinerja optimal selama benchmarking, dengan precision dan False Positive (FP) yang terjaga tanpa mengorbankan recall. Nilai F0.5 score lebih baik dibandingkan dengan model yang menggunakan teknik balancing. Meski tidak menggunakan balancing, kondisi imbalance data tetap mempengaruhi hasil. Model cenderung memprediksi kelas mayoritas (menolak tawaran), sehingga potensi konversi nasabah yang tertarik bisa terlewat. Meskipun F0.5 score terjaga, model masih berisiko kehilangan nasabah yang seharusnya tertarik..

4. Berdasarkan Feature Importance Methode, kolom data penting yang digunakan dalam model meliputi data tentang riwayat kampanye dan hasil sebelumnya, faktor ekonomi (seperti suku bunga dan tingkat ketenagakerjaan), serta frekuensi dan durasi komunikasi antara telemarketing dan nasabah. Kolom-kolom ini terbukti signifikan dalam meningkatkan akurasi prediksi model. Namun, Logistic Regression memiliki keterbatasan dalam menangkap interaksi kompleks antar fitur.

5. Pendekatan berbasis data dengan implementasi model machine learning ini berpotensi meningkatkan conversion rate sebesar 67%, yang jauh lebih tinggi dibandingkan dengan conversion rate awal yang hanya sebesar 11%. Hal ini menjadikan model ini sebagai solusi yang lebih optimal dan menguntungkan bagi perusahaan, terutama jika dibandingkan dengan hasil yang diperoleh saat eksplorasi data awal.

## Rekomendasi
### Pendekatan Data Analisis untuk Strategi Telemarketing Bank
1. **Target Nasabah Potensial**
- **Strategi Berdasarkan Usia:** Sesuaikan produk deposito dengan profil usia nasabah. Untuk nasabah muda dan masih produktif bekerja, tawarkan deposito dengan jangka waktu yang lebih pendek dan imbal hasil yang kompetitif. Untuk nasabah yang lebih tua, tawarkan produk deposito jangka panjang dengan bunga lebih tinggi yang lebih sesuai untuk tujuan pensiun mereka.
- **Strategi Berdasarkan Status Pekerjaan:** Status pekerjaan nasabah (job) dapat memberikan gambaran mengenai stabilitas finansial mereka. Untuk nasabah dengan pekerjaan stabil, tawarkan produk deposito yang lebih konservatif dan aman, dengan jangka waktu lebih panjang dan bunga yang lebih tinggi. Untuk nasabah dengan pekerjaan yang lebih fleksibel, tawarkan produk deposito yang dapat dipilih dalam berbagai jangka waktu atau produk investasi yang lebih likuid dan menguntungkan.
- **Strategi Berdasarkan Status Pernikahan:** Status pernikahan (marital) dapat menunjukkan preferensi finansial nasabah. Untuk nasabah yang sudah menikah, tawarkan produk deposito dengan jangka panjang dan imbal hasil yang lebih tinggi, karena mereka mungkin berencana menabung untuk kebutuhan keluarga atau masa pensiun. Untuk nasabah yang belum menikah, tawarkan produk deposito yang lebih fleksibel dengan jangka waktu lebih pendek dan bunga yang kompetitif, sesuai dengan kebutuhan pribadi mereka.
- **Prioritaskan Nasabah yang Sudah Pernah Dihubungi (Warm to Hot Leads):** Nasabah lama atau yang sudah pernah dihubungi sebelumnya dan memiliki durasi panggilan yang panjang menunjukkan adanya komunikasi yang lebih positif dan lebih terbuka terhadap tawaran produk. Prioritaskan nasabah ini dalam kampanye selanjutnya. Berikan penawaran produk yang relevan dengan kebutuhan finansial mereka yang sudah dipahami dari percakapan sebelumnya. Jika nasabah tersebut sudah melakukan konversi sebelumnya, tawarkan program loyalitas atau keuntungan tambahan untuk meningkatkan retensi dan membangun hubungan jangka panjang.
- **Strategi untuk Nasabah Baru (Cold Leads):** Nasabah yang baru pertama kali dihubungi pada kampanye ini perlu pendekatan yang lebih personal untuk membangun hubungan dan menarik minat mereka. Gunakan data demografis dan informasi pekerjaan serta status pernikahan untuk menyesuaikan penawaran produk yang sesuai dengan kebutuhan dan profil nasabah. Sesuaikan pesan pemasaran agar lebih relevan berdasarkan usia, status pekerjaan, dan status pernikahan mereka. Misalnya, tawarkan produk deposito yang lebih fleksibel untuk nasabah muda yang baru memulai karir, atau produk dengan bunga lebih tinggi untuk nasabah yang lebih tua dan memiliki rencana pensiun.

### Model Machine Learning
- **Eksperimen dengan Model Lain:** Meskipun Logistic Regression telah memberikan hasil yang cukup baik, eksplorasi model lain seperti Random Forest atau XGBoost dapat dilakukan sebagai langkah lanjutan. Model-model ini dikenal lebih efektif dalam menangani data yang tidak seimbang dan dapat menghasilkan performa yang lebih baik dalam hal recall, khususnya pada kelas minoritas “Menerima Tawaran”.

- **Penerapan Penyesuaian Threshold:** Untuk meningkatkan recall pada kelas minoritas, penerapan penyesuaian threshold pada model Logistic Regression bisa dicoba. Misalnya dengan menurunkan ambang batas klasifikasi “yes”, model dapat lebih sensitif dalam mendeteksi nasabah yang berpotensi menerima tawaran, meskipun hal ini mungkin akan mempengaruhi metrik precision.

- **Hyperparameter Tuning Lebih Lanjut:** Dengan waktu yang terbatas, hyperparameter tuning dilakukan menggunakan RandomizedSearch. Sebagai langkah lanjutan, menggunakan teknik pencarian hyperparameter yang lebih mendalam seperti Grid Search dilakukan untuk menemukan kombinasi hyperparameter yang lebih optimal. Hal ini diharapkan bisa meningkatkan kinerja model lebih lanjut.

- **Eksperimen Teknik Interpretasi Model:** Meskipun keterbatasan waktu adalah faktor, menerapkan SHAP (SHapley Additive exPlanations) untuk interpretasi model di masa depan dapat memberikan wawasan penting tentang fitur-fitur mana yang paling berpengaruh terhadap keputusan model. Ini sangat penting dalam konteks bank yang perlu menjelaskan alasan keputusan untuk pelanggan atau regulator.

- **Integrasi Model Prediksi dalam Skrip Telemarketing:** Hasil prediksi dari model dapat diintegrasikan langsung dalam skrip atau sistem telemarketing. Telemarketer dapat melihat skor prediksi atau probabilitas bahwa nasabah cenderung menerima tawaran (*warm to hot leads*) atau menolak tawaran (*cold leads*) sebelum melakukan panggilan. Dengan demikian, mereka bisa lebih siap dan menyesuaikan pendekatan mereka berdasarkan data tersebut, misalnya dengan menawarkan produk yang lebih relevan atau memberikan penawaran khusus berdasarkan profil nasabah.

- **Penyesuaian dan Pembaruan Berdasarkan Feedback Pengguna:** Mengingat keterbatasan waktu dalam pengembangan model, penting untuk membangun siklus pembelajaran yang berkelanjutan. Feedback dari tim telemarketing dan hasil kampanye dapat digunakan untuk memperbarui dan menyesuaikan model secara berkala. Ini akan memastikan bahwa model dapat tetap relevan dan akurat seiring berjalannya waktu.

---

Sekian solusi berbasis data yang saya sampaikan,

Terima Kasih!
