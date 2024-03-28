# Hotel Booking Demand Analysis   

## Delta Group_JC_DS_OL_12_C_Final Project Team:
- Muhammad Dangga
- Rizki Nugraha
- Kelvin Chandra Sidhi

## Business Problem Understanding

**Context**

Industri perhotelan secara luas bergantung pada manajemen yang efisien terhadap permintaan pemesanan untuk memaksimalkan pendapatan dan meminimalkan risiko ketidak-terpenuhan kamar yang disebabkan karena pembatalan pesanan kamar. Dalam lingkungan bisnis yang kompetitif, pemahaman yang mendalam tentang perilaku pelanggan saat melakukan pemesanan hotel untuk pengambilan keputusan yang tepat dalam menentukan strategi perencanaan operasional

**Problem Statement**

1. Menentukan strategi yang tepat untuk menghandle pembatalan pesanan 
2. Memahami pola pembatalan pemesanan dan faktor-faktor yang mempengaruhinya. Tujuannya adalah untuk mengurangi risiko kehilangan pendapatan akibat pembatalan dan mengembangkan kebijakan pembatalan yang lebih efektif.
3. Memberikan insight dan rekomendasi kepada manajemen hotel berdasarakan temuan model, seperti startegi untuk mengurangi pembatalan dan meningkatkan pengalaman pelanggan

**Goals**

Maka berdasarkan permasalahan tersebut, perusahaan ingin memiliki sebuah model yang memiliki kemampuan untuk memprediksi kemungkinan customer akan membatalkan pesanan hotelnya atau tidak, sehingga dapat memfokuskan strategi bisnis yang dapat digunakan untuk pengambilan keputusan dalam menentukkan strategi perencanaan operasional Terutama saat High seasson berlangsung.

Dan juga, perusahaan ingin mengetahui faktor/variabel apa yang membuat seorang customer akan membatalkan pesanan mereka atau tidak (costumer behaviour), sehingga mereka dapat membuat rencana yang lebih baik untuk perusahaan.

**Analytic Approach**

Berbagai teknik analisis data digunakan, termasuk eksplorasi data, kita akan menganalisis data untuk menemukan faktor/variable apa yang mempengaruhi seorang customer akan membatalkan pesanannya atau tidak, dan kemudian kita akan membangun model klasifikasi yang akan membantu perusahaan untuk dapat memprediksi probabilitas customer akan membatalkan pesanannya tersebut atau tidak.


**Metric Evaluation**

1. Type 1 error : False Positive

* False Positive ketika model memprediksi cancel ternyata book
* Konsekuensi : Terjadi Over Capasity dari kamar hotel, sehingga kemungkinan hotel harus melakukan upgrade ke kamar yang lebih tinggi dan available.

2. Type 2 error False Negative

* False False Negative ketika model memprediksi booking ternyata cancel.
* Konsekuensinya : kita akan kehilangan pelanggan tanpa sempat mengantisipasinya,0 kemungkinan * akan ada kamar yang kosong karena tidak di antisipasi oleh OverBooking. 

Berdasarkan Konsekuensinya, akan dicoba untuk menghandle kapasitas kamar dari strategi Overbook. 

## Dataset

**Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| Hotel | Object | Nama hotel |
| is_canceled | Integer | Apakah pemesanan dibatalkan atau tidak (0 untuk tidak dibatalkan dan 1 untuk dibatalkan) |
| lead_time | Integer | waktu (dalam hari) antara transaksi pemesanan dan kedatangan aktual |
| arrival_date_year | Integer | Tahun kedatangan |
| arrival_date_month | Object | Bulan kedatangan |
| arrival_date_week_number | Integer | Nomor minggu dari tanggal kedatangan |
| arrival_date_day_of_month | Integer | Hari di bulan tanggal kedatangan |
| stays_in_weekend_nights | Integer | Jumlah malam akhir pekan yang dihabiskan di hotel |
| stays_in_week_nights	 | Integer | Jumlah malam hari yang dihabiskan di hotel |
| adults | Integer | Jumlah orang dewasa dalam catatan pemesanan tunggal |
| children | Float | Jumlah anak dalam satu catatan pemesanan |
| babies | Integer | Jumlah bayi dalam satu catatan pemesanan |
| meal | Object | Jenis makanan yang dipilih |
| country | Object | Negara asal pelanggan (sebagaimana disebutkan oleh mereka) |
| market_segment | Object | Segmen apa melalui pemesanan yang dibuat dan untuk tujuan apa |
| distribution_channel | Object | Melalui media mana pemesanan dilakukan |
| is_repeated_guest | Integer | Apakah pelanggan pernah melakukan pemesanan sebelumnya (0 untuk No dan 1 untuk Ya) |
| previous_cancellations | Integer | Jumlah pemesanan yang dibatalkan sebelumnya. |
| previous_bookings_not_canceled | Integer | Jumlah pemesanan sebelumnya yang tidak dibatalkan |
| reserved_room_type | Object | Tipe kamar yang dipesan oleh pelanggan |
| assigned_room_type | Object | Tipe kamar yang ditetapkan ke pelanggan |
| booking_changes | Integer | Jumlah perubahan pemesanan yang dilakukan oleh pelanggan |
| deposit_type | Object | Jenis deposit pada saat melakukan pemesanan (No deposit/ Refundable/ No refund) |
| agent | Float | ID agen untuk pemesanan |
| company | Float | ID perusahaan yang melakukan pemesanan |
| days_in_waiting_list | Integer | Jumlah hari dalam daftar tunggu |
| customer_type | Object | Jenis pelanggan (Sementara, Grup, dll.) |
| adr | float | Tarif rata-rata harian. |
| required_car_parking_spaces | Integer | Jumlah parkir mobil yang ditanyakan dalam pemesanan |
| total_of_special_requests | Integer | jumlah total permintaan khusus |
| reservation_status | object | Apakah pelanggan sudah check out atau membatalkan, atau tidak muncul |
| reservation_status_date | object | Tanggal pembuatan status reservasi |

## Summary

### Berdasarkan EDA yang kita analisis didapatkan beberapa hal di antaranya :
1. Pemesan paling banyak berasal dari pemesan domestik yaitu portugal di ikuti pengunjung luar negeri seperti britanian franch hingga sepanyol, yang mengartikan pengunjung dari latar belakang ini memiliki potensial lebih lanjut untuk di ajang promosi dan pemasaran yang lebih besar karena memiliki lingkup audience yang besar
2. Hotel yang melakukan sistem deposit tidak terlalu berpengaruh kepada pelanggan untuk melanjutkan booking di temuin sekita 93.81 persen hotel dari 888 pesanan hotel yang melakukan sistem non refund tetap melakukan cancel, hal ini menjadikan hotel tetap untung walau pengunjung membatalkan pesanan
3. Puncak dari jumlah pesanan terdapat pada bulan Agustus dan July, 10.985 pesanan terdapat di bulan agustus dan 9840 pesanan berada pada bulan july, Agustus dan July ini juga masih satu seasson yang itu summer yang mengartikan kunjungan terbanyak berasal di season Summer hal ini menjadi suatu acuan dimana machine learning yang kita buat nantinya akan sangat menguntungkan di antara bulan july sampai agustus ini.
4. Kemampuan Hotel untuk memberikan spesial request yang di ajukan oleh pengunjung juga secara langsung menambah minat pengunjung untuk melanjutkan menginap.

### Alasan pembatalan pemesanan bisa berbeda-beda. Pelanggan mungkin meminta sesuatu yang tidak tersedia. 
berdasarkan EDA:

1. jarak seseorang untuk booking sampai saat hari kedatangan berpengaruh terhadap tingkat cancellation, dimana pelanggan yang membooking jauh - jauh hari lebih rentan untuk melakukan cancel
2. Parkir mobil tidak ditindaklanjuti oleh hotel, sedangkan pembatalan perjalanan lainnya berada di luar kendali hotel. dalam hal apa pun.
3. Pembatalan juga di pengaruhi dari permintaan spesial yang terkadang tidak dapat di penuhi oleh hotel seperti kamar yang memiliki akses langsung ke kolam renang, pemadangan yang kamar miliki, sampai mungkin permintaan lain yang tidak disebutkan

### Model Overview: ### 

![image](https://github.com/PurwadhikaDev/DeltaGroup_JC_DS_OL_12_C_FinalProject/assets/151637860/84a4a5f7-1976-4018-9b35-28549f972074)

Berdasarkan hasil classification report (models comparison) dari model kita, kita dapat menyimpulkan/mengambil konklusi bahwa model Xgboost memiliki score yang paling baik di antara yang lainnya dengan nilai 0.628 dalam menentukan precision.

Setelah melalui Cross Validation dan Hyperparameter Tuning, model XGBoost terpilih sebagai model terbaik untuk memprediksi hotel booking. 

Classification Report Default XGBOOST : 

               precision    recall  f1-score   support

           0       0.80      0.90      0.85     12512
           1       0.61      0.42      0.50      4720
    accuracy                           0.77     17232
    macro avg      0.71      0.66      0.67     17232
    weighted avg   0.75      0.77      0.75     17232

Classification Report Tuned XGBOOST : 

               precision    recall  f1-score   support

           0       0.80      0.92      0.85     12512
           1       0.64      0.38      0.48      4720
    accuracy                           0.77     17232
    macro avg      0.72      0.65      0.67     17232
    weighted avg   0.75      0.77      0.75     17232

Setelah di uji berdasarkan Error di temui bahwa variabel request_car_parking berperan paling dominan dalam menentukan seseorang akan melakukan cancel atau book, diikuti oleh variabel special_request, lead_time, dan seterusnya

![image](https://github.com/PurwadhikaDev/DeltaGroup_JC_DS_OL_12_C_FinalProject/assets/151637860/7301b1bc-74e2-4110-9ba0-86dd858140eb)


## Kesimpulan
* Dari hasil analisis yang kita temuin menghasilkan kesimpulan bahwa sebenarnya ada beberapa faktor seseorang akan melakukan cancel terhadap pesanannya, ada berbagai macam hal yang mungkin diluar dari kemampuan yang dapat kita ketahui berdasarkan hal tersebut kita tidak bisa memaksakan seseorang untuk terus melanjutkan bookingnya.

* Antisipasi yang bisa kita lakukan adalah melakukan strategy OverBooking yaitu dimana kita bisa menyewakan kamar di luar kapasitas yang hotel miliki secara lebih hati - hati dan efisien, strategy ini juga lebih menguntungkan karena hotel mampu mengantisipasi cancel dan hotel yang memilki sistem non refund juga di untungkan karena keuntungan yang di dapat saat seseorang melakukan cancel


## Tableau Dashboard
Untuk memudahkan melihat data secara visual disini juga dibuat dashboard menggunakan Tableau, yang dapat membuka link dibawah ini:

[Tableau Link](https://public.tableau.com/app/profile/rizki.nugraha6656/viz/HotelBookingProject_17115228727400/Dashboard1)
