# LAPORAN PRAKTIKUM PERTEMUAN 3
## Use Case Diagram dan Use Case Description
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io |
| **Studi kasus** | LAB (peminjaman peralatan) dan SIA (pengajuan KRS) |
| **Tanggal** | [16-10-2026 ] |

---

## 1. Tujuan Pembelajaran
1. Menuliskan batas sistem, aktor, kebutuhan, aturan bisnis, dan asumsi.
2. Menentukan use case berdasarkan tujuan aktor, bukan nama tombol, tabel, atau langkah teknis.
3. Membuat use case diagram yang konsisten dengan daftar kebutuhan.
4. Menyusun use case description (pemicu, prasyarat, alur utama, alur alternatif, pascakondisi).
5. Menunjukkan keterlacakan setiap use case ke kebutuhan.
6. Memperbaiki model berdasarkan review dan mendokumentasikan perubahan pada versi berikutnya.

## 2. Landasan Teori

### 2.1 Use Case Diagram
Use case diagram memvisualisasikan perilaku sistem dari sudut pandang aktor: fungsi apa yang disediakan sistem dan siapa yang dapat menjalankannya. Diagram dibuat pada awal pengembangan dan memberi gambaran ringkas relasi antara sistem dan aktor. Diagram menunjukkan fungsi dan hubungan, **tidak** menunjukkan urutan tindakan, respons sistem, atau kegagalan. Hal itu dijelaskan pada use case description.

### 2.2 Aktor, Use Case, dan Batas Sistem
- **Aktor**: peran eksternal yang berinteraksi dengan sistem; dapat berupa manusia atau sistem lain. Tidak setiap nama orang atau bagian organisasi otomatis menjadi aktor.
- **Use case**: perilaku sistem yang memberi hasil bernilai bagi aktor. Nama memakai kata kerja dan objek (misal *Ajukan peminjaman*), bukan data saja (*Peminjaman*) atau rincian antarmuka (*Klik tombol simpan*).
- **Batas sistem**: aktor di luar, use case di dalam.

### 2.3 Simbol Use Case Diagram
| Simbol | Keterangan |
|---|---|
| Actor | Orang, sistem, atau proses yang berinteraksi |
| Use case | Elips; fungsi yang ditampilkan sistem |
| Collaboration | Elips putus-putus; kumpulan elemen yang bekerja sama |
| Include | Garis putus-putus, panah terbuka, label «include» |
| Extend | Garis putus-putus, panah terbuka, label «extend» |
| Association | Garis utuh tanpa panah |
| Generalization | Segitiga kosong (belum dipakai pada pertemuan ini) |
| Batas sistem | Persegi panjang berjudul |

### 2.4 Relasi «include»
Menyatakan perilaku suatu use case disertakan dalam use case lain dan **selalu terjadi**. Panah dari use case penyerta ke use case yang disertakan. Contoh: *Ajukan peminjaman* «include» *Periksa ketersediaan*. Hasil pemeriksaan boleh "tersedia" atau "tidak tersedia", tetapi kegagalan hasil tidak berarti pemeriksaannya opsional. Include bukan sekadar tanda "harus terjadi sebelumnya": kondisi seperti sudah masuk (login) ditulis sebagai **prasyarat**, bukan include.

### 2.5 Relasi «extend»
Menambahkan perilaku ke use case dasar pada **extension point** tertentu bila **condition** terpenuhi. Use case dasar harus tetap bermakna tanpa tambahan itu. Panah dari use case tambahan ke use case dasar. Perilaku bersyarat tidak selalu harus dipisah sebagai extend; validasi gagal atau penolakan dapat dijelaskan sebagai alur alternatif.

### 2.6 Perbandingan Include dan Extend
| Aspek | «include» | «extend» |
|---|---|---|
| Tujuan | Menyertakan perilaku yang diperlukan pada titik pemanggilan | Menambah perilaku pada extension point |
| Arah panah | Penyerta → disertakan | Tambahan → dasar |
| Contoh | Pemeriksaan pada setiap pengajuan | Pencetakan bila dipilih |
| Use case dasar | Memerlukan perilaku yang disertakan | Tetap bermakna tanpa tambahan |
| Dokumentasi penting | Letak pemanggilan dan hasil | Extension point, kondisi, dan perilaku tambahan |

Keduanya bukan penunjuk urutan seperti pada activity diagram.

### 2.7 Use Case Description (Tabel 3.3)
ID dan nama; sumber kebutuhan; tujuan; aktor utama; aktor pendukung; pemicu; prasyarat; alur utama; alur alternatif atau pengecualian (dengan rujukan nomor langkah); pascakondisi berhasil; pascakondisi gagal; aturan bisnis atau asumsi.

## 3. Studi Kasus LAB: Peminjaman Peralatan

### 3.1 Skenario
*Mahasiswa mengajukan peminjaman dengan memilih alat, jumlah, dan rentang waktu. Sistem memeriksa ketersediaan. Jika tersedia dan data lengkap, sistem menyimpan pengajuan berstatus Menunggu keputusan. Pada konfirmasi, mahasiswa dapat memilih mencetak bukti. Petugas mengelola data peralatan serta menyetujui atau menolak pengajuan. Kepala laboratorium melihat laporan peminjaman.*

### 3.2 Kebutuhan
| ID | Kebutuhan |
|---|---|
| LAB-R01 | Mahasiswa dapat melihat ketersediaan peralatan |
| LAB-R02 | Petugas dapat mengelola data peralatan |
| LAB-R03 | Mahasiswa dapat mengajukan peminjaman; sistem memeriksa ketersediaan sebelum menyimpan |
| LAB-R04 | Mahasiswa dapat mencetak bukti pada konfirmasi jika memilihnya |
| LAB-R05 | Petugas dapat menetapkan persetujuan atau penolakan |
| LAB-R06 | Kepala laboratorium dapat melihat laporan peminjaman |

**Batas dan aturan:** sistem mencatat dan menyediakan informasi (perpindahan fisik alat di luar perangkat lunak); pengguna terautentikasi; pengajuan berstatus Menunggu keputusan, bukan otomatis Disetujui; pengajuan dengan alat tidak tersedia tidak disimpan sebagai berhasil; pencetakan bukan syarat keberhasilan; persetujuan petugas belum dimodelkan sebagai reservasi stok; pengambilan, pengembalian, kondisi alat, dan denda belum dianalisis.

### 3.3 Aktor dan Katalog Use Case
| Aktor | Tujuan |
|---|---|
| Mahasiswa | Melihat ketersediaan, mengajukan peminjaman, mencetak bukti |
| Petugas Laboratorium | Mengelola peralatan dan memproses keputusan |
| Kepala Laboratorium | Melihat laporan peminjaman |

| ID | Nama use case | Peran dalam model |
|---|---|---|
| LAB-UC01 | Lihat Ketersediaan Peralatan | Fungsi utama mahasiswa |
| LAB-UC02 | Kelola Data Peralatan | Fungsi utama petugas |
| LAB-UC03 | Ajukan Peminjaman | Fungsi utama mahasiswa |
| LAB-UC04 | Periksa Ketersediaan | Perilaku yang disertakan UC03 |
| LAB-UC05 | Cetak Bukti Pengajuan | Tambahan bersyarat pada UC03 |
| LAB-UC06 | Proses Keputusan Peminjaman | Fungsi utama petugas |
| LAB-UC07 | Lihat Laporan Peminjaman | Fungsi utama kepala laboratorium |

*Lihat Ketersediaan* menyediakan informasi bagi pengguna, sedangkan *Periksa Ketersediaan* memvalidasi alat, jumlah, dan rentang waktu dalam pengajuan; keduanya tidak disamakan.

### 3.4 Keputusan Relasi
| Relasi | Alasan |
|---|---|
| LAB-UC03 «include» LAB-UC04 | Pemeriksaan menjadi bagian validasi pengajuan dan selalu dijalankan |
| LAB-UC05 «extend» LAB-UC03; extension point *Bukti pengajuan tersedia*; condition *[mahasiswa memilih cetak]* | Pengajuan tetap berhasil tanpa pencetakan |

### 3.5 Hubungan pada Diagram
| Sumber | Hubungan | Tujuan |
|---|---|---|
| Mahasiswa | Asosiasi | LAB-UC01 |
| Mahasiswa | Asosiasi | LAB-UC03 |
| Mahasiswa | Asosiasi | LAB-UC05 |
| Petugas Laboratorium | Asosiasi | LAB-UC02 |
| Petugas Laboratorium | Asosiasi | LAB-UC06 |
| Kepala Laboratorium | Asosiasi | LAB-UC07 |
| LAB-UC03 | «include» | LAB-UC04 |
| LAB-UC05 | «extend» | LAB-UC03 |

### 3.6 Use Case Description LAB-UC03 Ajukan Peminjaman
| Elemen | Isi |
|---|---|
| Tujuan | Menghasilkan pengajuan peminjaman yang tersimpan |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | LAB-R03 dan LAB-R04 |
| Pemicu | Mahasiswa memilih fungsi pengajuan peminjaman |
| Prasyarat | Mahasiswa terautentikasi; data peralatan tersedia |
| Pascakondisi berhasil | Pengajuan tersimpan dengan nomor dan status Menunggu keputusan |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan |
| Include | LAB-UC04 Periksa ketersediaan |
| Extension point | Bukti pengajuan tersedia, pada langkah 6 |
| Extend | LAB-UC05 jika [mahasiswa memilih cetak] |

| Langkah | Tindakan mahasiswa | Respons sistem |
|:--:|---|---|
| 1 | Membuka pengajuan | Menampilkan formulir |
| 2 | Memilih alat, jumlah, rentang waktu, dan tujuan | Menampung isian |
| 3 | Mengirim pengajuan | Memeriksa kelengkapan data |
| 4 | — | Menjalankan LAB-UC04 |
| 5 | — | Jika tersedia, menyimpan pengajuan dan memberi nomor |
| 6 | Melihat konfirmasi | Menampilkan nomor dan status; mencapai extension point |
| 7 | Mengakhiri pengajuan | Menutup proses pengajuan |

### 3.7 Hasil dan Berkas
`P03_2406048_LAB_notasi_usecase_v01.drawio`/`.png`, `P03_2406048_LAB_deskripsi_v01.md`, `P03_LAB_skenario_v01.md`, `P03_2406048_LAB_model_analisis_v01.md`.

## 4. Tugas SIA: Pengajuan KRS

### 4.1 Skenario
*Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.*

### 4.2 Kebutuhan, Batas, dan Asumsi
| ID | Kebutuhan |
|---|---|
| SIA-R03 | Mahasiswa dapat mengajukan KRS |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS |

Kode dimulai dari R03 agar SIA-R01 dan SIA-R02 (Pertemuan 2) tetap punya identitas berbeda. Asumsi: pengguna terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia; validasi gagal berarti pengajuan belum tersimpan; unduh bukti bukan syarat keberhasilan; KRS tersimpan belum berarti disetujui; pembayaran, nilai, dan basis data di luar tugas. Admin Akademik tidak ditambahkan hanya karena ada pada tugas P2.

### 4.3 Katalog Use Case
| ID | Nama | Aktor | Sumber |
|---|---|---|---|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01 |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02 |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 |
| SIA-UC04 | Validasi KRS | (disertakan UC03) | SIA-R04 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R05 |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06 |

### 4.4 Relasi dan Hubungan Diagram
| Sumber | Hubungan | Tujuan | Alasan |
|---|---|---|---|
| Mahasiswa | Asosiasi | SIA-UC01, UC03, UC05 | Fungsi yang dijalankan mahasiswa |
| Admin Akademik | Asosiasi | SIA-UC02 | Mengelola jadwal |
| Dosen Wali | Asosiasi | SIA-UC06 | Memproses keputusan KRS |
| SIA-UC03 | «include» | SIA-UC04 | Validasi (kelengkapan, prasyarat, benturan jadwal) selalu dijalankan pada setiap pengajuan |
| SIA-UC05 | «extend» | SIA-UC03 | Condition [mahasiswa memilih unduh]; extension point *Bukti pengajuan KRS tersedia*; pengajuan tetap berhasil tanpa unduh |

### 4.5 Use Case Description SIA-UC03 Ajukan KRS
| Elemen | Isi |
|---|---|
| Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05 |
| Tujuan | Menghasilkan pengajuan KRS yang tersimpan |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi Ajukan KRS |
| Prasyarat | Mahasiswa terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia |
| Pascakondisi berhasil | Pengajuan tersimpan berstatus menunggu persetujuan dosen wali |
| Pascakondisi gagal | Tidak ada pengajuan KRS yang tersimpan |
| Include | SIA-UC04 Validasi KRS |
| Extension point / Extend | Bukti pengajuan KRS tersedia / SIA-UC05 jika [mahasiswa memilih unduh] |

Alur utama: mahasiswa membuka fungsi dan sistem menampilkan mata kuliah yang ditawarkan; mahasiswa memilih mata kuliah dan mengirim pengajuan; sistem menjalankan SIA-UC04; bila valid, sistem menyimpan pengajuan dan menampilkan konfirmasi. Alternatif: validasi gagal menghasilkan pesan kesalahan dan pengajuan tidak tersimpan; bila mahasiswa memilih unduh, sistem menyiapkan bukti (extend SIA-UC05).

Deskripsi SIA-UC04 (validasi), SIA-UC05 (unduh bukti), dan SIA-UC06 (persetujuan atau penolakan dengan catatan keputusan) disusun dengan template yang sama.

### 4.6 Uji Konsistensi Tiga Situasi
| Situasi | Menurut diagram | Menurut deskripsi | Konsisten |
|---|---|---|:--:|
| Validasi berhasil, tidak mengunduh | Include jalan, extend tidak aktif | Tersimpan tanpa bukti | Ya |
| Validasi gagal | Include jalan, hasil gagal | Pengajuan tidak tersimpan | Ya |
| Validasi berhasil, memilih unduh | Include jalan, extend aktif | Tersimpan dan bukti dapat diunduh | Ya |

### 4.7 Hasil dan Berkas
`P03_2406048_SIA_notasi_usecase_v01.drawio`/`.png`, `P03_2406048_SIA_deskriosi_v01.md`, `P03_SIA_skenario_v01.md`, `P03_2406048_SIA_model_analisis_v01.md`.

## 5. Pemeriksaan (Checklist)
- ✓ Setiap aktor mempunyai interaksi yang jelas.
- ✓ Use case sesuai kebutuhan dan berada di dalam batas sistem.
- ✓ Include mengarah ke perilaku yang disertakan; extend mengarah ke use case dasar.
- ✓ Extension point berada pada use case dasar; condition tercantum pada diagram dan deskripsi.
- ✓ Pengajuan tetap berhasil tanpa perilaku tambahan.
- ✓ Prasyarat dibedakan dari include; alur alternatif menjelaskan kegagalan dan hasil akhirnya.
- ✓ Diagram dan deskripsi memakai nama serta ID yang sama.
- ✓ Sumber dapat dibuka kembali; ekspor sesuai sumber terkini.
- ✓ Kebutuhan yang belum dimodelkan ditandai, bukan dianggap selesai.

## 6. Kendala dan Solusi
| No | Kendala | Solusi |
|:--:|---|---|
| 1 | Sulit membedakan include dan extend | Memakai tes dari jobsheet: include untuk perilaku yang selalu terjadi (pemeriksaan ketersediaan dan validasi KRS), extend untuk perilaku opsional bersyarat (cetak dan unduh bukti) |
| 2 | Arah panah include dan extend sempat terbalik | Aturan dihafalkan: include dari penyerta ke yang disertakan, extend dari tambahan ke dasar; panah dicek ulang pada diagram |
| 3 | Tabel model analisis (Markdown) kolomnya bergeser karena nama aktor yang terdiri dari dua kata terpisah | Teks tabel dirapikan dan nama aktor ditulis dalam satu sel; sebaiknya diperiksa ulang pada pratinjau Markdown |
| 4 | Menentukan kapan sesuatu menjadi use case dan kapan hanya alur alternatif | Memakai prinsip dari jobsheet: validasi gagal dan penolakan cukup sebagai alur alternatif, sedangkan extend perlu alasan pemodelan yang jelas |
| 5 | Berkas deskripsi SIA sempat salah ketik pada nama (`deskriosi`) | Nama berkas diperbaiki agar konsisten dengan pola penamaan |

## 7. Kesimpulan
Use case diagram dan use case description berhasil disusun untuk kasus LAB (7 use case) dan SIA (6 use case) dengan keterlacakan ke kebutuhan. Relasi include dipakai untuk perilaku yang selalu terjadi (pemeriksaan ketersediaan dan validasi KRS), sedangkan extend dipakai untuk perilaku bersyarat (cetak bukti dan unduh bukti) lengkap dengan condition dan extension point. Pengujian konsistensi tiga situasi menunjukkan diagram dan deskripsi saling sesuai.

## 8. Referensi
1. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
2. OMG. (2017). *Unified Modeling Language, Version 2.5.1*.
3. Dokumentasi draw.io. https://www.drawio.com/docs/
