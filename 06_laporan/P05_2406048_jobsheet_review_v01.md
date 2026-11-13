# LAPORAN PRAKTIKUM PERTEMUAN 5
## Skenario Use Case: Dari Diagram ke Langkah Kegiatan
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io, Visual Studio Code |
| **Studi kasus** | LAB (telaah 12 tabel skenario) dan SIA (penyusunan 7 tabel skenario) |
| **Tanggal** | [06-11-2026] |

---

## 1. Tujuan Pembelajaran
1. Menyusun tabel skenario dengan struktur lengkap tanpa field kosong.
2. Menulis langkah berurutan, satu aksi per langkah, dengan pemisahan kolom Kegiatan dan Respon sistem serta penomoran berlanjut.
3. Memetakan include menjadi langkah wajib dan extend menjadi cabang bersyarat.
4. Menerapkan generalization aktor dan generalization use case pada penulisan skenario.
5. Menelaah 12 tabel skenario LAB terhadap diagram acuan dan menyusun 7 tabel skenario SIA dengan nama, ID, aktor, dan relasi yang sama persis dengan diagram.

Pada pertemuan ini **tidak ada diagram baru**; diagram acuan adalah diagram kumulatif Pertemuan 4.

## 2. Landasan Teori

### 2.1 Pengertian Skenario Use Case
Skenario use case adalah uraian langkah demi langkah interaksi aktor dan sistem untuk satu use case: apa yang dilakukan aktor, bagaimana sistem menanggapi, pada langkah mana alur bercabang, dan kapan use case selesai. Skenario ditulis sebagai tabel dua kolom: **Kegiatan** (aksi aktor) dan **Respon sistem**.

**Perbedaan dengan artefak lain.** Use case description (P3) merangkum use case secara ringkas, sedangkan skenario merincinya menjadi langkah yang dapat diuji satu per satu; keduanya harus konsisten. Use case diagram (P4) menunjukkan fungsi dan hubungan tanpa urutan; skenario melengkapinya dengan urutan.

### 2.2 Struktur Tabel Skenario
1. Baris **Nama use case**: sama persis dengan diagram.
2. Baris **Aktor**: aktor utama; untuk aktor umum tambahkan catatan aktor khusus yang berlaku.
3. Baris **Tujuan**: hasil yang dicapai aktor, satu kalimat.
4. Baris **Deskripsi**: penjelasan singkat peran aktor dan sistem.
5. Kepala kolom **Kegiatan** dan **Respon sistem**.
6. Bagian **Skenario Normal**: jalur utama yang berjalan sesuai rencana.
7. Bagian **Skenario Alternative**: jalur cabang (data tidak tersedia, isian tidak lengkap, kondisi extend terpenuhi). Penomoran **melanjutkan** Skenario Normal, tidak mengulang dari 1.
8. Baris **Skenario Akhir**: satu kalimat kondisi selesai untuk jalur berhasil dan gagal; bukan langkah bernomor.

### 2.3 Kaidah Penulisan Langkah
a. Satu langkah berisi satu aksi.
b. Kolom Kegiatan hanya aksi aktor; kolom Respon sistem hanya tanggapan sistem.
c. Kalimat aktif singkat diawali kata kerja (memilih, mengisi, menampilkan, memeriksa, menyimpan, menolak).
d. Data disebut eksplisit (nama field, nilai, status, misalnya status Menunggu Keputusan).
e. Setiap cabang alternatif menulis *cabang dari langkah N*.
f. Penomoran berlanjut dari Normal ke Alternative.
g. Skenario Akhir tidak mengulang langkah terakhir.
h. Nama aktor, use case, ID, condition, dan extension point sama persis dengan diagram P4.

### 2.4 Pemetaan Relasi Diagram ke Skenario (Tabel 5)
| Relasi | Cara menulis |
|---|---|
| Include | Langkah rujukan pada Skenario Normal dengan nama, ID, dan tabel use case yang disertakan, tanpa menyalin langkahnya; tidak pernah sebagai alternatif |
| Extend | Cabang bersyarat pada Skenario Alternative dengan condition dan extension point; merujuk ke tabel use case tambahan |
| Generalization aktor | Ditulis satu kali atas nama aktor umum dengan catatan aktor khusus |
| Generalization use case | Tabel umum memuat perilaku bersama; tabel khusus hanya perilaku pembeda dan merujuk ke tabel umum |
| Collaboration dan realization | Tidak diberi langkah dan tabel sendiri; hanya disebut pada keterangan tabel use case yang direalisasikan |

### 2.5 Kesalahan Umum yang Dihindari
Dua aksi dalam satu langkah; aksi aktor di kolom sistem (atau sebaliknya); penomoran alternatif diulang dari 1; include ditulis sebagai alternatif; extend tanpa condition dan extension point; Skenario Akhir sebagai langkah bernomor; mengubah nama, ID, atau aktor dari diagram.

## 3. Studi Kasus LAB: Telaah 12 Tabel Skenario

### 3.1 Contoh Penerapan: Tabel 5.1 LAB-UC03 Ajukan Peminjaman
Aktor: Peminjam (berlaku untuk Mahasiswa dan Dosen).

| No | Kegiatan | Respon sistem |
|:--:|---|---|
| 1 | Peminjam memilih peralatan yang akan dipinjam | |
| 2 | | Sistem menjalankan Periksa Ketersediaan (lihat Tabel skenario LAB-UC04) |
| 3 | Peminjam mengisi tanggal pinjam, tanggal rencana kembali, dan keperluan peminjaman | |
| 4 | | Sistem memeriksa kelengkapan isian dan menampilkan ringkasan pengajuan |
| 5 | Peminjam mengirim pengajuan | |
| 6 | | Sistem menyimpan pengajuan dengan status Menunggu Keputusan dan menampilkan nomor pengajuan |
| 7 | Peralatan yang dipilih tidak tersedia (cabang dari langkah 2) | |
| 8 | | Sistem menampilkan pesan peralatan tidak tersedia; pengajuan tidak dilanjutkan |
| 9 | Isian pengajuan tidak lengkap (cabang dari langkah 4) | |
| 10 | | Sistem menampilkan pesan isian belum lengkap dan meminta melengkapi |
| 11 | Peminjam memilih cetak bukti, condition [mahasiswa memilih cetak], extension point Bukti pengajuan tersedia (extend LAB-UC05) | |
| 12 | | Sistem menampilkan bukti pengajuan dengan nomor pengajuan (Tabel skenario LAB-UC05) |

Skenario Akhir: selesai bila pengajuan tersimpan berstatus Menunggu Keputusan; bila alat tidak tersedia atau isian tidak lengkap, pengajuan tidak tersimpan. Collaboration LAB-CO01 disebut pada keterangan tabel tanpa langkah sendiri.

### 3.2 Hasil Telaah 12 Tabel
| Tabel | Use case | Aktor | Jalur normal | Alternatif | Relasi yang ditelusur |
|---|---|---|---|---|---|
| 5.3 | LAB-UC01 | Peminjam (Mahasiswa, Dosen) | Buka fungsi; sistem tampilkan daftar dan status | Tidak ada alat tersedia: pesan | Asosiasi Peminjam; generalization aktor |
| 5.1 | LAB-UC03 | Peminjam | 6 langkah (lihat 3.1) | Alat tidak tersedia; isian tidak lengkap; cetak bukti | Include UC04; extend UC05; collaboration LAB-CO01 |
| 5.4 | LAB-UC04 | Peminjam (di dalam UC03) | Dipanggil alur pengajuan; sistem periksa jumlah dan status; tersedia lanjut | Tidak tersedia atau jumlah kurang: alur berhenti | Include dari UC03 |
| 5.5 | LAB-UC05 | Mahasiswa | Pilih cetak; tampil bukti; konfirmasi; cetak | Tidak memilih cetak: konfirmasi ditutup, pengajuan tetap tersimpan | Extend ke UC03; asosiasi khusus Mahasiswa |
| 5.6 | LAB-UC02 | Petugas Laboratorium | 8 langkah: buka fungsi, daftar, pilih bentuk, formulir, isi, periksa, simpan, konfirmasi | Data tidak lengkap atau tidak sah: ditolak | Use case umum (generalization) |
| 5.7 | LAB-UC08 | Petugas Laboratorium | Formulir baru; isi; periksa; simpan | Data tidak lengkap | Generalization ke UC02 |
| 5.8 | LAB-UC09 | Petugas Laboratorium | Pilih data; tampil data saat ini; ubah; periksa; simpan | Data tidak ditemukan | Generalization ke UC02 |
| 5.9 | LAB-UC10 | Petugas Laboratorium | Pilih data; periksa tidak dipinjam dan tanpa pengajuan aktif; konfirmasi; hapus | Alat dipinjam atau punya pengajuan aktif: ditolak | Generalization ke UC02 |
| 5.10 | LAB-UC06 | Petugas Laboratorium | Buka daftar Menunggu Keputusan; pilih dan setujui; status Disetujui | Menolak: status Ditolak; pengajuan tidak ditemukan atau status berubah: pesan | Asosiasi (berdiri sendiri) |
| 5.11 | LAB-UC07 | Kepala Laboratorium | Buka fungsi; daftar periode; pilih periode; tampil laporan | Tidak ada data: pesan | Asosiasi tunggal, tanpa relasi lain |
| 5.12 | LAB-UC11 | Petugas Laboratorium | 10 langkah termasuk rujukan Periksa Kondisi (UC12) | Status bukan Dipinjam; kondisi rusak; jumlah tidak sesuai | Include UC12; collaboration LAB-CO02 |
| 5.13 | LAB-UC12 | Petugas Laboratorium (di dalam UC11) | Dipanggil; tampil pilihan kondisi; pilih; catat | Nilai kondisi belum dipilih: diminta memilih | Include dari UC11 |

**Penelusuran Kepala Laboratorium:** aktor ini hanya punya LAB-UC07 dan UC07 tidak punya include, extend, generalization, atau realization, sehingga tabelnya berdiri sendiri.

### 3.3 Hasil
`P05_2406048_LAB_skenario_v04.drawio`, `P05_LAB_skenario_v01.md`, dan logbook `P05_2406048_logbook_v01.md`.

## 4. Tugas SIA: Layanan Hasil Studi

### 4.1 Cakupan
Tugas melanjutkan kasus SIA Pertemuan 4; keterampilan baru hanya penulisan skenario, tanpa menambah use case, aktor, atau kebutuhan di luar diagram SIA P4 (SIA-R07 s.d. SIA-R12).

### 4.2 Tujuh Tabel Skenario
| Tabel | Use case | Aktor | Penerapan aturan | Alternatif utama |
|---|---|---|---|---|
| 1 | SIA-UC07 Lihat Kalender Akademik | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen) | Generalization aktor: satu tabel atas nama aktor umum | Tidak ada agenda pada periode yang dipilih |
| 2 | SIA-UC08 Input Nilai Mata Kuliah | Dosen | Prasyarat dosen pengampu; collaboration SIA-CO01 pada keterangan | Nilai di luar rentang ditolak; bukan pengampu; masa perkuliahan belum berakhir |
| 3 | SIA-UC09 Lihat KHS | Mahasiswa | Hanya nilai terpublikasi ditampilkan; collaboration SIA-CO02 | KHS belum tersedia karena nilai belum dipublikasikan |
| 4 | SIA-UC10 Kelola Data Mahasiswa | Admin Akademik | Skenario umum; langkah bersama dirujuk UC11, UC12, UC13 | Data tidak lengkap atau tidak sah |
| 5 | SIA-UC11 Tambah Data Mahasiswa | Admin Akademik | Hanya perilaku pembeda: data baru tersimpan | Data tidak lengkap |
| 6 | SIA-UC12 Ubah Data Mahasiswa | Admin Akademik | Hanya perilaku pembeda: data berubah | Data tidak ditemukan |
| 7 | SIA-UC13 Hapus Data Mahasiswa | Admin Akademik | Hanya perilaku pembeda: data terhapus dengan syarat | Mahasiswa punya data akademik aktif: ditolak |

*Isi lengkap tiap tabel (langkah normal, langkah alternatif bernomor lanjutan, Skenario Akhir) ada pada berkas `P05_2406048_SIA_skenario_v01.drawio`.*

### 4.3 Aturan Khusus yang Diterapkan
- Mahasiswa dan Dosen mewarisi *Lihat Kalender Akademik* dari Civitas Akademika; asosiasi warisan tidak digambar ulang dan skenario ditulis sekali.
- Nilai hanya dapat diinput dosen pengampu.
- KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa tanpa data akademik aktif.
- Diagram SIA Pertemuan 4 tidak diubah.

### 4.4 Hasil
`P05_2406048_SIA_skenario_v01.drawio` dan `P05_SIA_skenario_v01.md`.

## 5. Pemeriksaan (Checklist)
- ✓ Seluruh field tabel terisi.
- ✓ Langkah berurutan, satu aksi per langkah, penomoran berlanjut tanpa pengulangan.
- ✓ Kolom Kegiatan hanya aksi aktor; kolom Respon sistem hanya tanggapan sistem.
- ✓ Data yang dimasukkan dan ditampilkan disebut eksplisit.
- ✓ Include sebagai langkah rujukan pada Skenario Normal; extend sebagai cabang bersyarat dengan condition dan extension point.
- ✓ Generalization aktor dan use case diterapkan; collaboration hanya disebut pada keterangan tabel.
- ✓ Setiap tabel memiliki Skenario Alternative dan Skenario Akhir.
- ✓ Nama, ID, aktor, condition, dan extension point sama persis dengan diagram P4.
- ✓ Berkas diagram P04 tidak diubah.

## 6. Kendala dan Solusi
[isi kendala dan solusi]

## 7. Kesimpulan
Dua belas tabel skenario LAB berhasil ditelaah terhadap diagram acuan dengan penelusuran relasi, dan tujuh tabel skenario SIA berhasil disusun dengan struktur yang sama. Relasi diagram dipetakan konsisten ke langkah skenario: include menjadi langkah rujukan, extend menjadi cabang bersyarat, generalization menjadi tabel umum dan khusus, dan collaboration hanya disebut pada keterangan. Tabel skenario ini menjadi masukan activity diagram pada Pertemuan 6.

## 8. Referensi
1. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
2. OMG. (2017). *Unified Modeling Language, Version 2.5.1*.
3. Jobsheet Praktikum Pertemuan 3 dan 4 IFRWP5149.