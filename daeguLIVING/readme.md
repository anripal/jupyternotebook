# **README**
Halo! tolong gunakan file ini sebagai panduan sebelum menjalankan Jupyter Notebook File.

Notebook ini dibuat sebagai Capstone Project ketiga saya dalam mengikuti pembelajaran Data Science & Machine Learning bootcamp yang diadakan oleh Purwadhika. Di sini saya akan melakukan implementasi  dasar model machine learning terhadap suatu kasus. Mohon dimaklumi jika ada kesalahan, saya mencoba yang terbaik! :)

Dataset yang akan digunakan adalah Daegu Real Estate data. Dataset ini telah saya sediakan di repository atau bisa di download [disini](https://www.kaggle.com/datasets/gunhee/koreahousedata).

Kamu juga bisa melihat slide presentasi nya [disini](https://docs.google.com/presentation/d/149aw-RDeKJYy8Exe1gTs86FH8x30KsjU7MHcuFIF6DU/edit?usp=sharing).

---
## **Apa yang saya lakukan dalam pengimplementasian model Machine Learning ini?**
Perusahaan properti di Daegu (daeguLiving) menyediakan layanan jual-beli apartemen melalui platform online.

**Masalah**  
Menentukan harga apartemen yang kompetitif untuk klien mereka (pengguna platform, pemilik dan pembeli properti).

**Goals**  
DaeguLiving's Business Strategic Team  memerlukan 'prediction tool' yang dapat membantu klien (dalam hal ini pemilik properti) untuk dapat menentukan harga apartement secara akurat berdasarkan fitur properti sehingga calon pembeli properti juga dapat memiliki referensi harga yang jelas dan transparan.

**Analytics Approach**  
Menganalisis data untuk dapat menemukan pola dari fitur-fitur yang ada, yang membedakan harga apartemen satu dengan yang lainnya. 

**Metrik Evaluasi**
- **RMSE** - Root of Mean Squared Error *(metrik utama)*
- **MAE** - Mean of Absolute Error
- **MAPE** - Mean of Absolute Percentage Error

### **Step By Step**
#### **1. Data Understanding**
Disini kita perlu mempelajari Features Variables dan pengaruh nya terhadap Target Variables. Apakah mereka berpengaruh? Apakah diantara mereka ada yang saling berkorelasi? Pola apa yang bisa kita dapatkan untuk mempelajari Target Variables?

Setelah menganalisis dataset untuk menjawab pertanyaan diatas, berikut kolom dataset yang telah di sortir:

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| HallwayType | Object | Apartment type |
| TimeToSubway | Object | Time to nearest subway station |
| SubwayStation | Object | Name of nearest subway station |
| YearBuilt | Integer | Year apartment was built |
| N_FacilitiesInApt | Integer | Number of facilities in the apartment |
| Total_Nearby_Facilities | Float | Number of facilities, office and school nearby |
| Size(sqf) | Integer | Size of apartment |
| SalePrice | Integer | Apartment price in USD|

<br>

#### **2. Train Test Split**
Features Variable: HallwayType, TimeToSubway, SubwayStation, YearBuilt, N_FacilitiesInApt, Total_Nearby_Facilities and Size(sqf).
Target Variable: SalePrice

#### **3. Model Benchmarking**
Berikut model Machine Learning yang digunakan
```
from sklearn.linear_model import LinearRegression
from sklearn.neighbors import KNeighborsRegressor
from sklearn.tree import DecisionTreeRegressor
from sklearn.svm import SVR
from sklearn.ensemble import RandomForestRegressor
from xgboost import XGBRegressor
from sklearn.linear_model import Ridge
from sklearn.linear_model import Lasso
from sklearn.ensemble import GradientBoostingRegressor  
from sklearn.ensemble import AdaBoostRegressor
```

Kita mendapatkan `Support Vector Regression (SVR)` dan `GradientBoostingRegressor` sebagai 2 top model terbaik di Benchmark model dan menggunakan `GradientBoostingRegressor` untuk di Hyperparameter Tuning.

#### **4. Model Hypertune**
Model terbaik adalah **Tuned** `GradientBoostingRegressor`.
```
 {'model__subsample': 0.8,
 'model__n_estimators': 200,
 'model__min_samples_split': 10,
 'model__min_samples_leaf': 1,
 'model__max_features': 'log2',
 'model__max_depth': 4,
 'model__learning_rate': 0.05}
 ```

#### **5. Performance Comparison Fit to Test Set **
| **Model** | **RMSE** | **MAE** | **MAPE %** |
| --- | --- | --- | --- |
| GradReg Before Tuning | 46340.670419 | 37157.846718 | 18.27 |
| GradReg Tuned | 46302.964984 | 36881.581870 | 18.16 |

<br>

### **Kesimpulan**
- Model benchmark: `Support Vector Regression (SVR)` (RMSE 47305.07, MAE 37199.29 dan MAPE 17.9%) dan `GradientBoostingRegressor` (RMSE 46340.67, MAE 37157.84 dan MAPE 18.2%).
- Best Model: Tuned `GradientBoostingRegressor` (RMSE 46251.50, MAE 36860.82 dan MAPE 18.16%).
- Test Set Performance: Memperbaiki semua performa metrik terutama RSME (walau tidak signifikan), mengindikasikan kearuasian prediksi di data yang baru.
- Model Range: Performa terbaik dengan rentang harga berkisar dari 32,743 USD ~ 585,840 USD. Diluar rentang ini, prediksi rentan terhadap error dan kurang akurat.
- MAPE Interpretation: MAPE nya 18% yang artinya prediksi harga apartemen berpotensi meleset 18% dari harga seharusnya.
- Feature Importance: Fitur inti yang sangat berpengaruh terhadap harga apartemen adalah `'Size (sqf)', 'HallwayType' dan 'N_FacilitiesInApt'`.
- Business Insights: Ukuran apartemen, jumlah fasilitas, dan tipe lorong merupakan faktor utama yang memengaruhi harga apartemen di Daegu, sehingga pengembang properti dapat fokus meningkatkan fitur-fitur ini untuk memaksimalkan nilai jual.
- Sebelumnya, pemilik apartemen kesulitan menentukan harga jual yang kompetitif. Harga terlalu tinggi membuat apartemen sulit terjual, sementara harga terlalu rendah merugikan pemilik. Kurangnya transparansi juga menyulitkan pembeli memperkirakan harga sebenarnya. Dengan model machine learning yang diimplementasikan, perusahaan daeguLiving kini memiliki alat prediksi harga apartemen yang membantu pemilik menetapkan harga lebih adil dan kompetitif, sekaligus meningkatkan efisiensi proses penjualan. Alat ini menghemat waktu, meningkatkan kepuasan pengguna, mempercepat transaksi, dan memperluas basis pelanggan, serta membangun kepercayaan antara pemilik apartemen dan calon pembeli.

### **Recommendation**
- A/B Testing
Implementasikan A/B testing untuk membandingkan keakuratan prediksi harga model dengan metode tradisional, seperti harga pasar atau penilaian oleh agen properti.

Fokuskan uji coba pada apartemen dengan karakteristik unik, seperti unit di lantai atas dengan pemandangan terbuka atau apartemen dengan fasilitas eksklusif (misalnya, private gym, sky garden).

Analisis apakah model memberikan harga yang lebih akurat dibandingkan metode manual, terutama untuk apartemen dengan fitur premium.

Jika model menunjukkan performa yang lebih baik dibandingkan metode tradisional dalam mayoritas kasus, model dapat dijadikan acuan utama dalam menentukan harga properti. Namun, jika model masih memiliki margin error yang besar dalam kasus tertentu, model dapat digunakan sebagai rekomendasi pendukung, dengan verifikasi tambahan oleh agen properti.

- Pengelompokkan Error untuk Optimasi Model
Identifikasi prediksi dengan error tinggi, baik overestimation maupun underestimation. Ambil 5% kasus dengan error paling ekstrim dan analisis hubungannya dengan variabel independen.

Prioritaskan analisis pada apartemen dengan harga tinggi yang memiliki banyak variasi dalam spesifikasi (misalnya, penthouse, unit sudut dengan balkon luas, atau apartemen di gedung baru dengan teknologi smart home).

Jika model sering overestimate harga pada unit premium, pertimbangkan untuk menambahkan fitur terkait lokasi, kualitas bangunan, atau preferensi pasar terhadap tipe properti tertentu.

Model dapat digunakan sebagai acuan utama untuk properti dengan spesifikasi standar. Untuk properti dengan harga tinggi atau fitur unik, disarankan model digunakan sebagai rekomendasi tambahan, dengan analisis manual oleh ahli properti.

- Penambahan Fitur yang Lebih Relevan dengan Harga
Tambahkan fitur yang lebih korelatif dengan harga apartemen untuk meningkatkan akurasi prediksi.

Tambahkan jarak ke pusat bisnis atau landmark populer untuk mengetahui dampaknya pada harga apartemen.

Masukkan rating fasilitas umum di sekitar properti (misalnya, skor sekolah, jumlah restoran/kafe terdekat) untuk melihat pengaruhnya terhadap nilai apartemen.

Gunakan data historis harga jual unit serupa di lokasi yang sama untuk memperhitungkan tren harga properti.

Jika fitur tambahan meningkatkan akurasi model secara signifikan, model dapat digunakan sebagai acuan utama. Namun, jika masih terdapat ketidakpastian dalam faktor harga, model tetap digunakan sebagai alat bantu rekomendasi dengan validasi tambahan.

- Ekspansi Model untuk Pengembangan Lainnya

Model dapat diperluas untuk memprediksi harga properti yang lebih strategis, termasuk apartemen investasi dan unit high-demand.

Fokuskan pengembangan model pada properti yang memiliki permintaan tinggi, seperti unit studio untuk pekerja profesional, apartemen di dekat universitas, atau unit sewa jangka pendek di kawasan wisata.

Analisis perubahan harga musiman untuk properti dengan permintaan dinamis, seperti apartemen di daerah dengan event tahunan besar (misalnya, dekat stadion, pusat konvensi, atau distrik perkantoran utama).

Model dapat dijadikan acuan utama untuk properti dengan tren harga yang stabil. Untuk properti dengan fluktuasi harga yang tinggi, model dapat digunakan sebagai alat bantu analisis, dengan referensi tambahan dari tren pasar terkini.

---
###### **Notebook ini dibuat oleh Destaria Anripal**
