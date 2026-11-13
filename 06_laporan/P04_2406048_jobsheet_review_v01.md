# LAPORAN PRAKTIKUM PERTEMUAN 4
## Use Case Diagram Lanjutan: Generalization dan Collaboration
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io |
| **Studi kasus** | LAB (pengembalian peralatan) dan SIA (layanan hasil studi) |
| **Tanggal** | [09-10-2026] |

---

## 1. Tujuan Pembelajaran
1. Menyusun hierarki generalization aktor (satu aktor umum, minimal dua aktor khusus) dengan arah panah benar.
2. Menyusun generalization use case (satu umum, minimal dua khusus).
3. Menempatkan minimal dua collaboration yang bernama sama persis dengan use case yang direalisasikan, dihubungkan dengan realization.
4. Membuat diagram kumulatif yang mempertahankan seluruh diagram Pertemuan 3 lalu menambah elemen baru.
5. Menyusun satu use case description baru yang konsisten dengan diagram.
6. Menunjukkan keterlacakan elemen baru ke kebutuhan.

## 2. Landasan Teori

### 2.1 Pengembangan Kumulatif
Diagram Pertemuan 4 tidak digambar dari lembar kosong dan tidak menggantikan diagram Pertemuan 3. Seluruh aktor, use case, dan relasi Pertemuan 3 dipertahankan, lalu elemen baru ditambahkan di atasnya. Berkas P03 tidak ditimpa; pekerjaan dilakukan pada salinan berkas P04. Generalization dan collaboration hanya dipakai bila skenario memerlukannya, bukan agar diagram tampak lengkap.

### 2.2 Generalization Aktor
Satu aktor bersifat umum dan aktor lain bersifat khusus. Aktor khusus **mewarisi seluruh asosiasi** aktor umum dan boleh punya asosiasi tambahan yang hanya berlaku baginya (tidak diwariskan ke aktor khusus lain). Aturan menggambar: (1) segitiga kosong menunjuk aktor umum, panah digambar dari aktor khusus; (2) asosiasi warisan digambar satu kali dari aktor umum; (3) aktor umum adalah nama peran, bukan nama orang atau aktor bayangan; (4) hierarki satu tingkat; (5) bila dua peran tidak berbagi fungsi, gambar asosiasi langsung.

Tiga pertanyaan penentu: apakah dua peran memakai fungsi yang sama persis; apakah kesamaan itu bertahan selama pengembangan; apakah nama peran umum membuat diagram lebih jelas. Generalization layak dipakai bila ketiganya dijawab ya.

### 2.3 Generalization Use Case
Use case khusus mewarisi tujuan, aktor terkait, dan perilaku dasar use case umum, lalu menambah atau merinci perilaku pembeda. Hasilnya harus sejenis dengan hasil use case umum. Contoh: *Tambah*, *Ubah*, dan *Hapus Data* sah sebagai bentuk khusus *Kelola Data*, tetapi *Lihat Laporan* bukan bentuk khusus *Kelola Data* karena tujuannya berbeda. Generalization menyatakan hubungan **jenis**, sedangkan include dan extend menyatakan hubungan **pelaksanaan**; satu pasang use case hanya memakai satu jenis relasi.

### 2.4 Collaboration dan Realization
Use case menyatakan perilaku yang teramati dari luar sistem. Perilaku itu diwujudkan oleh **collaboration**, yaitu sekumpulan elemen dan peran yang bekerja sama. Digambar sebagai elips garis putus-putus. Aturan: aktor tidak pernah dihubungkan langsung ke collaboration; collaboration bukan use case tambahan dan memakai ID tersendiri (LAB-CO, SIA-CO); namanya sama persis dengan use case yang direalisasikan; satu collaboration merealisasikan satu use case; tidak digambar untuk semua use case. Realization digambar dari collaboration menuju use case (garis putus-putus, segitiga kosong). Isi collaboration (peran elemen dan pertukaran pesan) menjadi bahan diagram interaksi pada pertemuan berikutnya.

### 2.5 Perbandingan Empat Relasi (Tabel 4.2)
| Relasi | Makna | Arah | Garis |
|---|---|---|---|
| «include» | Perilaku selalu disertakan | Penyerta → disertakan | Putus-putus, panah terbuka |
| «extend» | Perilaku tambahan bila kondisi terpenuhi | Tambahan → dasar | Putus-putus, panah terbuka |
| Generalization | Elemen khusus mewarisi elemen umum | Khusus → umum | Utuh, segitiga kosong |
| Realization | Collaboration mewujudkan use case | Collaboration → use case | Putus-putus, segitiga kosong |

### 2.6 Use Case Description Lanjutan
Memakai template yang sama dengan Pertemuan 3, ditambah baris **Generalization** dan baris **Collaboration** (ID dan nama collaboration yang merealisasikan). Deskripsi ditulis untuk use case, bukan untuk collaboration.

## 3. Studi Kasus LAB: Pengembalian Peralatan

### 3.1 Skenario
*Dosen juga meminjam peralatan. Mahasiswa dan dosen sama-sama dapat melihat ketersediaan dan mengajukan peminjaman. Petugas menambah, mengubah, dan menghapus data peralatan. Setelah peminjaman disetujui dan alat diambil, petugas mencatat pengembalian dan memeriksa serta mencatat kondisi peralatan. Dua use case utama (Ajukan Peminjaman dan Catat Pengembalian Peralatan) direalisasikan oleh collaboration.*

### 3.2 Kebutuhan Baru dan Aturan
| ID | Kebutuhan |
|---|---|
| LAB-R01 s.d. R06 | Tetap berlaku dari Pertemuan 3 |
| LAB-R07 | Mahasiswa dan Dosen, sebagai Peminjam, dapat melihat ketersediaan dan mengajukan peminjaman |
| LAB-R08 | Petugas mengelola data peralatan dalam bentuk tambah, ubah, hapus |
| LAB-R09 | Petugas mencatat pengembalian untuk peminjaman berstatus Dipinjam |
| LAB-R10 | Sistem memeriksa dan mencatat kondisi peralatan pada pengembalian |
| LAB-R11 | Model menunjukkan collaboration untuk Ajukan Peminjaman dan Catat Pengembalian Peralatan |

Aturan: pengembalian hanya untuk status Dipinjam; kondisi bernilai Baik, Rusak Ringan, atau Rusak Berat; hapus data hanya untuk alat yang tidak sedang dipinjam dan tanpa pengajuan aktif; **keterlambatan dan denda belum dimodelkan** (dicatat sebagai pertanyaan terbuka).

### 3.3 Aktor
| Aktor | Kedudukan |
|---|---|
| Peminjam | Umum (baru); mewariskan fungsinya ke Mahasiswa dan Dosen |
| Mahasiswa | Khusus dari Peminjam; tetap punya asosiasi sendiri ke LAB-UC05 |
| Dosen | Khusus dari Peminjam (baru) |
| Petugas Laboratorium | Tetap |
| Kepala Laboratorium | Tetap |

### 3.4 Katalog Gabungan Use Case
| ID | Nama | Peran dalam model | Sumber |
|---|---|---|---|
| LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap; fungsi Peminjam | R01, R07 |
| LAB-UC02 | Kelola Data Peralatan | Tetap; use case umum bagi UC08–UC10 | R02, R08 |
| LAB-UC03 | Ajukan Peminjaman | Tetap; fungsi Peminjam; menyertakan UC04; direalisasikan LAB-CO01 | R03, R07 |
| LAB-UC04 | Periksa Ketersediaan | Tetap; disertakan UC03 | R03 |
| LAB-UC05 | Cetak Bukti Pengajuan | Tetap; extend ke UC03 | R04 |
| LAB-UC06 | Proses Keputusan Peminjaman | Tetap | R05 |
| LAB-UC07 | Lihat Laporan Peminjaman | Tetap | R06 |
| LAB-UC08 | Tambah Data Peralatan | Baru; khusus dari UC02 | R08 |
| LAB-UC09 | Ubah Data Peralatan | Baru; khusus dari UC02 | R08 |
| LAB-UC10 | Hapus Data Peralatan | Baru; khusus dari UC02 | R08 |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru; direalisasikan LAB-CO02 | R09 |
| LAB-UC12 | Periksa Kondisi Peralatan | Baru; disertakan UC11 | R10 |

Perilaku pembeda: *Tambah* menghasilkan data peralatan baru; *Ubah* menghasilkan data yang berubah; *Hapus* menghasilkan data terhapus dengan syarat pada aturan studi kasus.

### 3.5 Collaboration
| ID | Nama (sama dengan use case) | Use case yang direalisasikan |
|---|---|---|
| LAB-CO01 | Ajukan Peminjaman | LAB-UC03 |
| LAB-CO02 | Catat Pengembalian Peralatan | LAB-UC11 |

Alasan: keduanya use case utama pada potongan model ini; collaboration untuk use case lain tidak digambar.

### 3.6 Perbandingan Diagram Pertemuan 3 dan 4
| Kelompok | Isi |
|---|---|
| Tetap | Aktor Mahasiswa, Petugas, Kepala Laboratorium; UC01–UC07; include UC03→UC04; extend UC05→UC03 beserta condition dan extension point; asosiasi Petugas ke UC02 dan UC06; Kepala ke UC07; Mahasiswa ke UC05 |
| Berubah | Asosiasi UC01 dan UC03 dipindah dari Mahasiswa ke Peminjam (aturan generalization, bukan penghapusan fungsi) |
| Ditambah | Aktor Peminjam dan Dosen; dua generalization aktor; UC08–UC12; tiga generalization use case; include UC11→UC12; asosiasi Petugas ke UC11; LAB-CO01 dan LAB-CO02 dengan dua realization |

### 3.7 Spesifikasi 17 Hubungan
| No | Sumber | Hubungan | Tujuan |
|:--:|---|---|---|
| 1 | Peminjam | Association | LAB-UC01 |
| 2 | Peminjam | Association | LAB-UC03 |
| 3 | Mahasiswa | Association (khusus) | LAB-UC05 |
| 4 | Mahasiswa | Generalization | Peminjam |
| 5 | Dosen | Generalization | Peminjam |
| 6 | Petugas Laboratorium | Association | LAB-UC02 |
| 7 | Petugas Laboratorium | Association | LAB-UC06 |
| 8 | Petugas Laboratorium | Association | LAB-UC11 |
| 9 | Kepala Laboratorium | Association | LAB-UC07 |
| 10 | LAB-UC03 | «include» | LAB-UC04 |
| 11 | LAB-UC05 | «extend» | LAB-UC03 |
| 12 | LAB-UC08 | Generalization | LAB-UC02 |
| 13 | LAB-UC09 | Generalization | LAB-UC02 |
| 14 | LAB-UC10 | Generalization | LAB-UC02 |
| 15 | LAB-UC11 | «include» | LAB-UC12 |
| 16 | LAB-CO01 | Realization | LAB-UC03 |
| 17 | LAB-CO02 | Realization | LAB-UC11 |

### 3.8 Use Case Description LAB-UC11 Catat Pengembalian Peralatan
| Elemen | Isi |
|---|---|
| Sumber kebutuhan | LAB-R09 dan LAB-R10 |
| Tujuan | Pengembalian tercatat; status peminjaman dan kondisi peralatan terbarui |
| Aktor utama | Petugas Laboratorium |
| Pemicu | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang dikembalikan |
| Prasyarat | Petugas terautentikasi; peminjaman berstatus Dipinjam |
| Pascakondisi berhasil | Pengembalian tercatat dengan tanggal kembali dan kondisi; status menjadi Selesai |
| Pascakondisi gagal | Tidak ada pengembalian baru tercatat; status tidak berubah |
| Include | LAB-UC12 Periksa Kondisi Peralatan |
| Collaboration | LAB-CO02 Catat Pengembalian Peralatan |

| Langkah | Tindakan petugas | Respons sistem |
|:--:|---|---|
| 1 | Memilih peminjaman yang dikembalikan | Menampilkan data peminjaman dan statusnya |
| 2 | Mengonfirmasi alat dan jumlahnya | Menampung konfirmasi petugas |
| 3 | — | Memeriksa status harus Dipinjam |
| 4 | — | Menjalankan LAB-UC12 (memeriksa dan mencatat kondisi) |
| 5 | Menyimpan pencatatan | Menyimpan tanggal kembali dan kondisi; status menjadi Selesai |
| 6 | Melihat konfirmasi | Menampilkan ringkasan pengembalian |

Alternatif: **A1** status bukan Dipinjam (langkah 3): pencatatan ditolak dan status saat ini ditampilkan; **A2** kondisi Rusak Ringan atau Rusak Berat (langkah 4): tetap tersimpan dan kondisi ditandai pada data peralatan, tanpa denda; **A3** jumlah tidak sesuai (langkah 2): petugas diminta memeriksa kembali sebelum penyimpanan.

### 3.9 Tahap Penggambaran Diagram
1. Salin diagram P3 sebagai basis P4 (P3 tidak diubah).
2. Generalization aktor: tambah Peminjam dan Dosen, pindahkan asosiasi UC01 dan UC03 ke Peminjam, gambar dua panah generalization.
3. Generalization use case: tambah UC08, UC09, UC10 dan tiga panah ke UC02.
4. Pengembalian: tambah UC11 dan UC12, asosiasi Petugas ke UC11, include UC11→UC12.
5. Collaboration: tambah dua elips putus-putus dan dua realization.
6. Verifikasi 17 hubungan; tidak ada asosiasi warisan digambar ulang; tidak ada garis aktor ke collaboration.

Berkas: `P04_2406048_LAB_notasi_usecase_v01.drawio`/`.png`, `P04_2406048_LAB_deskripsi_v01.md`, `P04_LAB_kebutuhan_v01.md`, `P04_LAB_skenario_v01.md`, `P04_2406048_LAB_model_analisis_v01.md`.

## 4. Tugas SIA: Layanan Hasil Studi

### 4.1 Skenario
*Mahasiswa dan dosen adalah Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat KHS untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: tambah, ubah, hapus. Dua use case utama (Input Nilai dan Lihat KHS) direalisasikan collaboration.*

### 4.2 Kebutuhan dan Aturan
| ID | Kebutuhan |
|---|---|
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tambah, ubah, hapus |
| SIA-R12 | Model menunjukkan collaboration untuk Input Nilai Mata Kuliah dan Lihat KHS |

Aturan: kalender akademik adalah agenda resmi institusi, bukan jadwal kuliah; nilai hanya dapat diinput dosen pengampu; KHS hanya menampilkan nilai terpublikasi; hapus data mahasiswa hanya untuk yang tidak punya data akademik aktif; pengajuan KRS tetap menjadi bagian diagram kumulatif.

### 4.3 Katalog Gabungan
| ID | Nama | Aktor / peran |
|---|---|---|
| SIA-UC01–UC06 | Lihat/Kelola Jadwal, Ajukan KRS, Validasi KRS, Unduh Bukti, Proses Keputusan KRS | Tetap dari P2 dan P3 |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen; direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa; direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik; use case umum |
| SIA-UC11 | Tambah Data Mahasiswa | Khusus dari UC10 |
| SIA-UC12 | Ubah Data Mahasiswa | Khusus dari UC10 |
| SIA-UC13 | Hapus Data Mahasiswa | Khusus dari UC10 |

### 4.4 Spesifikasi Hubungan
| No | Sumber | Hubungan | Tujuan |
|:--:|---|---|---|
| 1 | Civitas Akademika | Association | SIA-UC07 |
| 2 | Mahasiswa | Association (tetap) | SIA-UC01 |
| 3 | Mahasiswa | Association (tetap) | SIA-UC03 |
| 4 | Mahasiswa | Association (tetap) | SIA-UC05 |
| 5 | Mahasiswa | Association (baru, khusus) | SIA-UC09 |
| 6 | Dosen | Association | SIA-UC08 |
| 7 | Admin Akademik | Association (tetap) | SIA-UC02 |
| 8 | Admin Akademik | Association | SIA-UC10 |
| 9 | Dosen Wali | Association (tetap) | SIA-UC06 |
| 10 | Mahasiswa | Generalization | Civitas Akademika |
| 11 | Dosen | Generalization | Civitas Akademika |
| 12 | SIA-UC11 | Generalization | SIA-UC10 |
| 13 | SIA-UC12 | Generalization | SIA-UC10 |
| 14 | SIA-UC13 | Generalization | SIA-UC10 |
| 15 | SIA-UC03 | «include» (tetap) | SIA-UC04 |
| 16 | SIA-UC05 | «extend» (tetap), [mahasiswa memilih unduh], extension point *Bukti pengajuan KRS tersedia* | SIA-UC03 |
| 17 | SIA-CO01 | Realization | SIA-UC08 |
| 18 | SIA-CO02 | Realization | SIA-UC09 |

### 4.5 Use Case Description SIA-UC08 Input Nilai Mata Kuliah
| Elemen | Isi |
|---|---|
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah mahasiswa tersimpan oleh dosen pengampu |
| Aktor utama | Dosen |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah yang diampunya |
| Prasyarat | Dosen terautentikasi; dosen adalah pengampu; masa perkuliahan telah berakhir |
| Pascakondisi berhasil | Nilai tersimpan dengan status Belum Dipublikasikan |
| Pascakondisi gagal | Tidak ada nilai baru tersimpan; data nilai tidak berubah |
| Collaboration | SIA-CO01 Input Nilai Mata Kuliah |

| Langkah | Tindakan dosen | Respons sistem |
|:--:|---|---|
| 1 | Memilih mata kuliah yang diampu | Memeriksa pengampu dan masa perkuliahan; menampilkan daftar mahasiswa |
| 2 | Mengisi nilai tiap mahasiswa | Menampung isian nilai |
| 3 | Memilih simpan | Memeriksa nilai dalam rentang yang sah |
| 4 | — | Menyimpan nilai berstatus Belum Dipublikasikan |
| 5 | Melihat konfirmasi | Menampilkan ringkasan nilai |

Alternatif: **A1** dosen bukan pengampu (langkah 1) → akses ditolak; **A2** masa perkuliahan belum berakhir (langkah 1) → input ditolak; **A3** nilai di luar rentang sah (langkah 3) → penyimpanan ditolak, isian yang salah ditandai.

Berkas: `P04_2406048_SIA_usecase_v01.drawio`/`.png`, `P04_2406048_SIA_deskripsi_v01.md`, `P04_SIA_kebutuhan_v01.md`, `P04_SIA_skenario_v01.md`, `P04_2406048_SIA_model_analisis_v01.md`.

## 5. Pemeriksaan (Checklist LAB dan SIA)
- ✓ Seluruh elemen Pertemuan 3 tetap ada dan tidak berubah nama.
- ✓ Kepala Laboratorium hanya terhubung ke LAB-UC07, tanpa relasi lain.
- ✓ Asosiasi warisan digambar satu kali dari aktor umum; asosiasi khusus tetap dari aktor khusus.
- ✓ Segitiga kosong generalization menunjuk elemen umum.
- ✓ Collaboration berupa elips putus-putus, namanya sama dengan use case, tidak terhubung ke aktor.
- ✓ Realization dari collaboration menuju use case.
- ✓ Aktor di luar dan use case serta collaboration di dalam batas sistem.
- ✓ Setiap elemen baru tertelusur ke LAB-R07 s.d. R11 atau SIA-R07 s.d. R12.
- ✓ Berkas P03 tidak ditimpa; sumber dapat dibuka; ekspor sesuai sumber.
- ✓ Keterlambatan dan denda ditandai sebagai pertanyaan terbuka.

## 6. Kendala dan Solusi
| No | Kendala | Solusi |
|:--:|---|---|
| 1 | Arah segitiga generalization sempat salah (menunjuk aktor khusus) | Segitiga kosong dipasang pada ujung yang menempel ke aktor atau use case umum |
| 2 | Asosiasi UC01 dan UC03 sempat digambar dua kali (dari Mahasiswa dan Dosen) | Garis duplikat dihapus; asosiasi digambar sekali dari Peminjam, sedangkan asosiasi khusus Mahasiswa ke UC05 dipertahankan |
| 3 | Collaboration sempat terlihat seperti use case biasa | Garis elips diubah menjadi putus-putus, namanya disamakan dengan use case, dan ID LAB-CO / SIA-CO dicatat terpisah |
| 4 | Diagram menjadi padat dan garis saling bersilang setelah elemen baru ditambahkan | Posisi aktor dan use case diatur ulang secara bertahap, mengikuti lima tahap penggambaran |
| 5 | Menjaga agar elemen Pertemuan 3 tidak berubah | Pekerjaan dilakukan pada salinan berkas P04 dan berkas P03 tidak ditimpa |
| 6 | Keterlambatan dan denda tidak ada aturannya | Dicatat sebagai pertanyaan terbuka pada berkas kebutuhan, tidak dikarang sebagai aturan |

## 7. Kesimpulan
Diagram kumulatif LAB (5 aktor, 12 use case, 2 collaboration, 17 hubungan) dan SIA (18 hubungan) berhasil dibuat dengan mempertahankan hasil Pertemuan 3. Generalization aktor dipakai pada Peminjam dan Civitas Akademika, generalization use case pada pengelolaan data (peralatan dan mahasiswa), dan collaboration dipakai untuk merealisasikan use case utama. Use case description LAB-UC11 dan SIA-UC08 konsisten dengan diagram.

## 8. Referensi
1. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
2. OMG. (2017). *Unified Modeling Language, Version 2.5.1*.
3. Jobsheet Praktikum Pertemuan 3 IFRWP5149.
4. Dokumentasi draw.io. https://www.drawio.com/docs/