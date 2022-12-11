# SIG_Performing-Spatial-Joins

*Tutorial Performing Spatial Joins

1. Download terlebih dahulu file nybb_19a.zip dan V_SSS_SEGMENTRATING_1.zip

2. Buka QGIS3 lalu klik new project temukan file nybb_19a.zip dan pilih layer nybb_19a/nybbb.shp dan seret ke kanvas. Ini merupakan lapisan poligon yang mewakili batas wilayah kota New York (*Gambar 1*)

3. Selanjutnya, kita cari file V_SSS_SEGMENTRATING_1.zip dan pilih layer dot_V_SSS_SEGMENTRATING_1_20190129.shp dan tambahkan ke kanvas. Ini merupakan lapisan garis dari semua jalan di kota (*Gambar 2*)

4. Selanjutnya kita lihat atribut yang tersedia untuk setiap fitur lapisan dot_V_SSS_SEGMENTRATING_1_20190129. Klik kanan dan Open Attribute Table (*Gambar 3*)

5. Kita akan melihat atribut yang disebut Rating_B yang memiliki nilai dalam rentang 0-10 yang mewakili peringkat segmen jalan. Atribut RatingWord memiliki peringkat deskriptif. Kita dapat menggunakan kolom Rating_B untuk menghitung rating rata-rata (*Gambar 4*)

6. Kita telah memperhatikan bahwa beberapa fitur memiliki peringkat NR. Ini adalah segmen yang tidak diberi peringkat. Memasukkan mereka ke dalam analisis kami tidak akan benar. Sebelum kita melakukan penggabungan spasial, mari kita siapkan Filter untuk mengecualikan rekaman ini, Klik kanan layer dot_V_SSS_SEGMENTRATIING_1_20190129 dan pilih Filter (*Gambar 5*)

7. Pada Queru Builder, ketikkan ekspresi berikut "RatingWord" != 'NR' untuk memilih semua rekaman yang tidak diberi peringkat NR. Lalu klik OK (*Gambar 6*)

8. Kita akan melihat lapisan dot_V_SSS_SEGMENTRATING_1_20190129 sekarang memiliki ikon filter yang menunjukkan bahwa ada filter aktif yang diterakan pada lapisan ini. Sekarang kita bisa melakukan penggabungan spasial menggunakan layer ini. Klik Processing lalu pilih Toolbox (*Gambar 7*)

9. Cari dan temukan Vector general lalu pilih Join attribute by location (summary). Klik dua kali untuk menampilkannya (*Gambar 8*)

10. Pada Join attribute by location (summary) ini, pilih nybb sebagai Join to features in. Lapisan jalan dot_V_SSS_SEGMENTRATING_1_20190129 akan menjadi lapisan gabung. Kita bisa membiarkan predikat Geometri ke persimpangan default. Klik tombol ... di sebelah Fields to sumarize (*Gambar 9*)

11. Pilih Rating_B dan klik OK (*Gambar 10*)

12. Begitu juga selanjutnya klik tombol ... di sebelah Summaries to calculate (*Gambar 11*)

13. Pilih mean sebagai operator ringkasan dan klik OK. Sekarang kita siap untuk memulai pemrosesan dan klik Run (*Gambar 12*)

14. Algoritme pemrosesan akan bekerja melalui fitur dan menerapkan gaungan spasial. Verifikasi bahwa pekerjaan pemrosesan berhasil dan klik close (*Gambar 13*)

15. Kembali pada layar utama, kita bisa melihat layer Joined layer baru ditambahkan pada kanvas. Open the attribute, kita akan melihat kolom baru Rating_B_mean ditambahkan ke input layer borough dengan rating mean semua jalan bersinggungan dengan fitur tersebut (*Gambar 14*)

16. Sekarang kita bisa melakukan operasi terbalik. Terkadang analisis kita memerlukan atribut dari lapisan lain berdasarkan hubungan spasial tetapi tidak menghitung ringkasan apa pun. Kita dapat menggunakan atribut gabungan dengan algoritma lokasi untuk analisis. Tugasnya menambahkan nama borough ke setiap ditur di layer jalan berdasarkan poligon borough mana yang bersinggungan dengannya. Sebelum kita menjalankan algoritma ini, mari hapus filter dari lapisan dot_V_SSS_SEGMENTRATING_1_20190129. Klik ikon filter dan tekan Clear di pembuat kueri, lalu klik OK (*Gambar 15*)

17. Matikan layer Joined di panel layers. Cari vector general dan pilih Join attributr by location di Processing Toolbox dan klik dua kali untuk menampilkannya (*Gambar 16*)

18. Pilih dot_V_SSS_SEGMENTRATING_1_20190129 sebagai layer input dan nybb sebagai layer join. kita bisa membiarkan predikat geometri ke persimpangan default. Klik tombol ... di sebelag Fields to add dan memilih BoroName. Klik OK (*Gambar 17* *Gambar 18*)

19. Segmen garis dapat melintasi batas wilayah, jadi kita memilih tipe penggabungan sebagai fitur Crate separate feature for each located feature (one-to-many) lalu klik Run (*Gambar 19*)

20. Setelah pemrosesan selesai, Open the attribute dari layer Joined yan baru ditambahkan. Kita akan melihat bahwa ada atribut BoroName baru yang ditambahkan ke setiap fitur jalan (*Gambar 20*)

21. Hasilnya (*Gambar 21*) 
