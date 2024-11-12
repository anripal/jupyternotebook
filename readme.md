# **README**
Halo! tolong gunakan file ini sebagai panduan sebelum menjalankan Jupyter Notebook File.

Notebook ini dibuat sebagai Capstone Project kedua saya sebagai student di Data Science & Machine Learning bootcamp yang diadakan oleh Purwadhika. Di sini saya akan melakukan analisis disebuah dataset. Tujuannya, ini akan menjadi portofolio dalam perjalanan saya sebagai Data Analyst. Mohon dimaklumi jika ada kesalahan, saya mencoba yang terbaik! :)

Dataset yang akan dianalisis adalah SaaS (Software as Service) Company data. Dataset ini telah saya sediakan di repository atau bisa di download [disini](https://www.kaggle.com/datasets/nnthanh101/aws-saas-sales).

Kamu bisa kunjungi versi Tableu dari analisis dataset [disini](https://public.tableau.com/app/profile/destaria.anripal/viz/SaaS_CapstoneProjMod2_DestariaAnripal/Dashboard1)

Untuk versi presentasi, ada [disini](https://drive.google.com/drive/folders/1Zm_R4gzKz_5BnsEwMPn85-bEFIXLPul9)

---

## Analisis apa yang saya lakukan?

**SparksHUB** adalah perusahaan fiksi yang menyediakan perangkat lunak berbasis cloud bagi perusahaan-perusahaan B2B. Dengan solusi ini, pelanggan dapat menggunakan perangkat lunak untuk kebutuhan Sales & Marketing tanpa perlu melakukan installasi di tempat. 

Sebagai sebuah perusahaan, SparksHUB tentunya mengalami untung dan rugi dari segi pendapatan (profitabilitas). Selama ini SparksHUB telah mendokumentasikan setiap transaksi yang mencakup rincian lokasi pelanggan, industri yang dilayani, segmen pelanggan, produk yang dibeli, diskon yang diberikan, serta profit atau kerugian dari tiap transaksi tersebut.

Di tengah persaingan pasar yang ketat, kemajuan teknologi, dan kebutuhan pelanggan yang berkembang, SparksHUB perlu memastikan bahwa setiap produk dan strategi penjualan berkontribusi pada peningkatan pendapatan. Oleh karena itu, mereka membutuhkan pendekatan yang lebih efektif untuk memahami pola penjualan, profitabilitas tiap segmen pelanggan, serta efektivitas strategi diskon.

Maka dari itu mereka meminta seorang Data Analyst untuk menganalisis data yang mereka miliki agar selanjutnya dapat membuat kebijakan yang tepat sehingga mengurangi kerugian, meningkatkan pendapatan serta memperkuat posisi pasar. Terutama pada segmen dan produk dengan kontribusi tertinggi bagi perusahaan.

---

## **Pernyataan Masalah**
Memastikan bahwa setiap produk dan strategi penjualan yang selama ini dilakukan berkontribusi pada peningkatan pendapatan dibanding kerugian.

## **Goals**
1. **Produk** SparksHUB mana yang memberikan kontribusi tertinggi terhadap profit perusahaan, dan produk mana yang perlu peningkatan agar lebih menguntungkan?

2. Seberapa efektif strategi **diskon** saat ini dalam meningkatkan volume penjualan tanpa mengorbankan profitabilitas? Apakah ada nominal diskon tertentu yang optimal bagi perusahaan?

3. Berdasarkan **segmen** pelanggan (SMB, Strategis, Enterprise) mana yang memberikan kontribusi terbesar terhadap pendapatan? Apa strategi yang dapat meningkatkan nilai dari setiap segmen ini?

4. Berdasarkan demografi pelanggan, **kapan dan di wilayah** mana penjualan serta profit SparksHUB mencapai puncaknya, dan apakah terdapat pola musiman yang dapat dioptimalkan untuk perencanaan pemasaran ke depan?

5. **Industri** apa yang paling menguntungkan bagi SparksHUB? Apakah ada sektor yang memiliki potensi besar untuk ekspansi atau fokus tambahan dalam strategi pemasaran?

## **Tujuan Goals**
Mendapatkan  wawasan strategis untuk menghasilkan kebijakan yang tepat sehingga mengoptimalkan pendapatan.

---

## **Dataset**
Kita cek dataset yang dimiliki, ini saat belum melalui proses Data Cleansing:
<img width="1396" alt="1" src="https://github.com/user-attachments/assets/d33d693f-e45e-4042-952a-f30c637cc713">
<img width="447" alt="2" src="https://github.com/user-attachments/assets/d49335fe-e194-480a-9ce7-e4bb7d440f2d">


## **Kolom Dataset**
Berikut petunjuk dari tiap-tiap kolom di database:
1. Row ID: *A unique identifier* di tiap transaksi
2. Order ID: *A unique identifier* di tiap order
3. Order Date: Tanggal order dibuat
4. Date Key: Tanggal Order dalam bentuk data numerik dari (YYYMMDD)
5. Contact Name: Nama dari representasi perusahaan yang melakukan order
6. Country: Negara dimana order dilakukan
7. City: Kota dimana order dilakukan
8. Region: Wilayah mana order dilakukan
9. Sub-Region: Sub-Wilayah mana order dilakukan
10. Customer: Nama Perusahaan yang melakukan order
11. Customer ID: *A unique identifier* tiap kustomer
12. Industry: Bidang industri yang konsumen lakukan
13. Segment: Segmen Pelanggan
14. Product: Produk SparksHUB yang dipesan
15. License: *License Key* untuk produk
16. Sales: Jumlah total penjualan untuk transaksi
17. Quantity: Jumlah total item dalam transaski
18. Discount: Diskon yang berlaku pada transaksi
19. Profit: Keuntungan dari transaksi

Ini setelah dilakukan Data Cleansing:
<img width="1396" alt="3" src="https://github.com/user-attachments/assets/cd568d8d-764c-41f6-bae8-d718dfa9155f">
<img width="327" alt="4" src="https://github.com/user-attachments/assets/5184b211-a419-41ad-a726-53fd0707320d">


Sebelum dan setelah dibersihkan, kita tetap memiliki total data yang sama, 9994 baris dan 19 kolom karena tidak ada missing value. Namun, ada beberapa hal yang berubah yaitu:
1. Penambahan satu kolom baru (`Kategori Profit`) dan penghapusan kolom yang tidak relevan (`Order Date`)
2. Mengganti format data di beberapa kolom sesuai dengan isi dan tujuan nya
3. Memastikan seluruh data di `Date Key` sesuai format YYYYMMDD
4. Mendapatkan timeframe data, seluruh data ini merupakan transaksi yang dimulai dari 4 Januari 2020 sampai 31 Desember 2023
5. Tiap kolom yang berhubungan, sudah di validasi bahwa semua nya mempunyai pasangan data yang konsisten
6. Menemukan beberapa outliers dan mengatasi nya dengan pertimbangan sesuai tujuan analisis
7. Mengetahui bahwa kolom numerikal yang relevan, berdistribusi tidak normal

---

## **Data Analisis**
Pada dasarnya, analisis dilakukan untuk melakukan rumusan masalah dari objektif. Berikut yang dilakukan di tahap ini:

1. Evalusi profitabilitas tiap produk
2. Cek efektivitas diskon yang selama ini diberikan ke pelanggan terhadap penjualan dan profitabilitaas
3. Profitabilitas berdasarkan segmen pelanggan
4. Analisis profit dan penjualan berdasarkan waktu dan wilayah
5. Evaluasi industri yang dilayani

---

Untuk memudahkan membaca notebook, berikut wawasan strategis yang saya temukan secara umum untuk di notice:

## **Evaluasi**
Secara produk:
- Produk dengan Rasio Profit Terbaik
    Produk-produk seperti `Alchemy`, `ChatBotPlugin` dan `Saas Connector Pack- Gold` berada di titik 0 Rasio Profit yang dapat dianggap sebagai produk dengan performa sangat baik karena mereka tidak mengalami kerugian. Di antara mereka, `Alchemy` menunjukkan keuntungan tertinggi, menjadikannya kandidat utama untuk lebih diinvestasikan atau ditingkatkan dari segi penjualan.
- Produk dengan Keuntungan Tinggi tetapi Mengalami Kerugian (Moderate Efficiency)
    Beberapa produk seperti `Data Smasher, Support dan Site Analytics` memang memiliki keuntungan yang signifikan. Namun, kerugian yang mereka alami cukup besar, sehingga rasio profit menjadi negatif (di bawah 0). Ini menunjukkan bahwa meskipun menguntungkan, mereka membutuhkan kontrol biaya atau pengurangan pengeluaran operasional untuk meningkatkan efisiensi keuntungan bersih.
- Produk Moderat dalam Keuntungan dan Kerugian
    `FinanceHub` menempati posisi sedang dengan keuntungan dan kerugian yang cukup berimbang, serta Rasio Profit moderat. Dengan kerugian lebih besar dari produk-produk sebelumnya, produk ini mungkin membutuhkan strategi efisiensi agar bisa meningkatkan margin keuntungannya, terutama jika ingin bersaing dengan produk-produk lain dalam hal pendapatan bersih.
- Produk dengan Keuntungan Kecil dan Kerugian Besar
    Produk seperti `Marketing Suite - Gold`, `OneView`, dan `SaaS Connector Pack` menunjukkan keuntungan yang lebih kecil dibandingkan dengan kerugian. Ini berarti bahwa walaupun mereka menghasilkan keuntungan, kontribusi bersih mereka terhadap pendapatan cukup terbatas. Sebagai strategi, mungkin perlu dievaluasi apakah produk-produk ini layak untuk dipertahankan atau harus mengalami penyesuaian harga atau biaya produksi untuk meningkatkan keuntungan.
- Produk dengan Rasio Profit Rendah (Keuntungan Tipis)
    `ContactMatcher` dan `Big Ol Database` menunjukkan margin keuntungan bersih yang sangat kecil. Ini berarti bahwa sebagian besar pendapatan yang dihasilkan habis untuk menutupi kerugian. Pengoptimalan biaya, inovasi produk, atau penyesuaian model bisnis mungkin diperlukan untuk meningkatkan profitabilitas produk ini.
- Produk dengan Profitabilitas Negatif
    `Marketing Suite` adalah produk yang banyak mengalami kerugian, dengan rasio profit yang paling rendah (-1.4). Ini menandakan bahwa kerugian jauh lebih besar daripada keuntungan. Dalam jangka panjang, produk ini mungkin akan lebih membebani perusahaan, sehingga strategi penghentian, rebranding, atau repositioning produk dapat dipertimbangkan agar lebih efektif.

Secara diskon:
Angka diskon yang sering SparksHUB berikan (20%) termasuk dalam tingkat Diskon Low, yang artinya memberikan rata-rata penjualan dan profit yang cukup.Yang perlu dievaluasi lanjut oleh SparksHUB adalah tentang diskon yang lebih besar dari Low (Medium dan High) karena memberikan efek negatif sehingga menurunkan profit.

Secara segmen pelanggan:
Tidak ada segmen yang lebih menguntungkan secara signifikan antar segmen lain terhadap perusahaan. Semua segmen berkontribusi sama secara penjualan dan profitabilitas

Puncak Profit berdasarkan Waktu & Wilayah:
Puncak profit dan penjualan terjadi di November 2023 wilayah APJ dan AMER dikarenakan diskon yang diberikan paling tinggi diantara tahun-tahun sebelumnya. APJ menghasilkan profit yang signifikan dibanding AMER, walau AMER mengalami penjualan yang paling besar. Namun secara keseluruhan, profit pada tahun 2023 tidak sebanyak tahun 2022. Ini mengindikasikan, diskon yang diadakan belum efektif.

Secara industri yang dilayani:
- Industri paling menguntungkan bagi SparksHUB adalah MISC (Miscellaneous) Industry dengan Profit Margin 25%. Profit Margin diambil dari segi efektifitas profit yang dihasilkan dibanding dengan penjualan yang dilakukan
- Sektor yang memiliki potensi besar untuk difokuskan atau diekspansi yaitu Consumer Products dan Finance Industry. Hal ini disimpulkan karena sektor-sektor tersebut memiliki Profit Growth paling tinggi diantara yang lain dan perlu pengoptimalan dari sisi efektifitas profit. Pertumbuhan kedua sektor ini cenderung naik setiap tahun nya (rentang waktu Timeframe to Assume di dataset) dengan jumlah transaksi yang banyak.



## **Kesimpulan**
1. Produk yang paling menguntungkan bagi SparksHUB adalah Alchemy, OneView, dan SaaS Connector Pack - Gold, yang memberikan kontribusi profit tinggi dan konsisten. Produk Site Analytics dan FinanceHub memiliki potensi untuk dioptimalkan, sementara Marketing Suite menunjukkan kerugian yang signifikan dan perlu evaluasi.

2. Strategi diskon SparksHUB saat ini kurang efektif dalam meningkatkan volume penjualan secara signifikan tanpa mengorbankan profit. Diskon dalam rentang 0-33% menunjukkan hasil paling optimal untuk menjaga profit sembari meningkatkan penjualan, sedangkan diskon lebih dari itu, cenderung berdampak kerugian.

3. Ketiga segmen pelanggan SparksHUB (SMB, Strategis, dan Enterprise) berkontribusi secara seimbang terhadap profit dan penjualan, tanpa ada segmen yang dominan.

4. Kenaikan penjualan dan profit SparksHUB terjadi setiap akhir tahun (Kuartal 4), puncak nya pada November 2023 di APJ (Asia, Pacific Japan) dan AMER (America), namun diikuti penurunan profit signifikan di setiap awal tahun (Kuartal 1).

5. Industri yang paling menguntungkan SparksHUB adalah Miscellaneous (MISC) dengan profit margin 25%. Namun, industri Consumer Products dan Finance menunjukkan potensi besar untuk ekspansi karena pertumbuhan profitnya yang stabil dan transaksi yang tinggi.

## **Rekomendasi**
1. Produk
- Perkenalkan program loyalitas atau penawaran khusus bagi pelanggan yang menggunakan produk Alchemy, OneView, dan SaaS Connector Pack - Gold. Ini untuk mempertahankan kontribusi pendapatan yang stabil dan meningkatkan nilai jangka panjang pelanggan.
- Tawarkan bundling atau diskon khusus untuk Site Analytics dan FinanceHub guna meningkatkan volume penjualan tanpa mengorbankan profit margin yang signifikan.
- Tinjau ulang produk Marketing Suite secara keseluruhan. Jika produk tidak menunjukkan ada nya potensi perubahan, relokasikan anggaran ke produk-produk dengan kontribusi profit lebih tinggi.

2. Diskon
- Terapkan kebijakan untuk membatasi diskon hingga maksimum 33% agar dapat meningkatkan volume penjualan tanpa merusak margin keuntungan.
- Targetkan diskon rendah pada segmen pelanggan yang sensitif terhadap harga dan potensi pembelian ulang, untuk menjaga loyalitas tanpa mengorbankan profitabilitas.
- Lakukan diskon yang lebih merata sepanjang tahun, khususnya di kuartal lain selain Q4, untuk menyeimbangkan penjualan dan profit

3. Segmen Pelanggan
- Rancang penawaran spesifik yang sesuai dengan kebutuhan masing-masing segmen untuk mendorong pertumbuhan seragam di ketiga segmen.
- Misalnya untuk segmen SMB (Small & Medium Business), fokus pada harga yang terjangkau dan fleksibilitas pembayaran untuk membantu pelanggan mengadopsi produk dengan risiko lebih rendah. Seperti:
    * Tawarkan paket bundling dengan diskon khusus atau uji coba gratis
    * Opsi pembayaran fleksibel seperti Langganan Bulanan yang tidak mengikat untuk mendukung anggaran pelangggan segmen ini yg biasanya terbatas
    * Layanan Konsultasi Gratis ntuk membantu pelanggan mengoptimalkan penggunaan produk
- Untuk segmen Strategic, berikan layanan tambahan dan fokus pada *customer relationship* agar menjadi pelanggan yang loyal. Seperti:
    * Berikan opsi untuk Produk Customizable sesuai dengan kebutuhan khusus pelanggan
    * Sediakan akses ke dukungan teknis prioritas dan pelatihan eksklusif
    * Buat skema diskon berjenjang, misalnya berdasarkan volume pembelian atau komitmen jangka panjang.
- Untuk segmen Enterprise, perusahaan berskala besar biasanya membutuhkan sistem yang terintegrasi sehingga memberikan solusi yang terukur untuk menunjang skala operasional mereka. Penawaran untuk segmen ini dapat berupa:
    * Tawarkan kontrak eksklusif dengan Fitur Premium atau Produk Khusus yang hanya tersedia untuk skala enterprise.
    * Sediakan Program Kemitraan yang menawarkan potensi kolaborasi, seperti program co-marketing atau dukungan teknis onsite.

4. Waktu
- Di bulan Januari sampai Juni fokus pada strategi pemasaran yang kuat untuk mengurangi ketergantungan pada diskon di event akhir tahun. Misalnya gencar menawarkan pelanggan untuk menyarankan produk lain yang relevan berdasarkan pembelian sebelumnya. Ini bisa meningkatkan volume penjualan tanpa perlu menawarkan diskon besar.
- Manfaatkan momentum puncak penjualan di APJ (Asia, Pacific and Japan) dan AMER (America) dengan kampanye sesuai dengan wilayah masing-masing untuk memperkuat profitabilitas regional. Misalnya di APJ, lakukan campaign di platforn populer seperti WeChat (China) dan Line (Jepang & Thailand). Untuk AMER (America), ikuti exhibit teknologi untuk memasarkan produk yang disediakan oleh SparksHUB.

5. Industri
- Tingkatkan investasi di Research & Development dalam mengembangkan produk atau fitur baru untuk pelanggan yang ada di industri Consumer Products dan Finance. Manfaatkan potensi pertumbuhannya yang konsisten.
- Tawarkan fitur tambahan lewat uji coba gratis selama 90 hari untuk produk yang dibeli MISC Industry, sebagai strategi agar sektor ini lebih sering melakukan transaksi dan tetap menjaga profitnya yang tinggi.

---
