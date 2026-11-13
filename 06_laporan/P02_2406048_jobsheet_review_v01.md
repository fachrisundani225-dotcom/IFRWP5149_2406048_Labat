# LAPORAN PRAKTIKUM PERTEMUAN 2
## Unified Modeling Language (UML)
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io |
| **Studi kasus** | LAB (Peminjaman dan Pengembalian Peralatan Laboratorium) dan SIA (Sistem Informasi Akademik) |
| **Tanggal** | [09-10-2026] |

---

## 1. Tujuan Pembelajaran
1. Menempatkan simbol aktor, use case, batas sistem, dan asosiasi pada diagram sederhana.
2. Menggunakan nama aktor dan fungsi secara konsisten dengan skenario.
3. Mengisi identitas artefak melalui template metadata Pertemuan 1.
4. Menyimpan berkas sumber dan ekspor dengan nama, lokasi, dan versi yang konsisten.
5. Memperbaiki kesalahan notasi dan dokumentasi berdasarkan review, lalu mencatat perubahannya.

## 2. Landasan Teori

### 2.1 Sejarah UML
Pada Oktober 1994 James Rumbaugh (pengembang OMT) bergabung dengan Rational Corp. tempat Grady Booch (pengembang OOD) bekerja. Keduanya menyatukan metode mereka menjadi Unified Method 0.8 (Oktober 1995). Ivar Jacobson, pengembang OOSE dan pencetus use case, bergabung, dan kolaborasi ketiganya menghasilkan UML 0.9 (Juni 1996). OMG mengeluarkan Request For Proposal pada 1996 sehingga lahir UML 1.0, kemudian UML 1.1 dengan delapan diagram. Versi berkembang ke 1.3, 1.4, 1.5, 2.0 (2005), dan 2.x. Standar normatif yang dipakai pada praktikum ini adalah OMG UML 2.5.1.

### 2.2 Pengertian dan Fungsi UML
UML adalah bahasa pemodelan sistem atau perangkat lunak untuk menjelaskan dan menggambarkan analisis serta desain berorientasi objek, dari level abstrak hingga implementasi. UML berperan dalam dokumentasi prototipe, pengujian, rencana proyek, desain, kode sumber, kebutuhan, dan arsitektur.

### 2.3 Building Block UML
**a. Benda (things)**
| Benda | Penjelasan |
|---|---|
| Class | Kelompok objek dengan atribut, hubungan semantik, dan operasi |
| Interface | Kumpulan spesifikasi operasi, digambar sebagai lingkaran |
| Collaboration | Kumpulan elemen yang bekerja sama; elips garis putus-putus |
| Use case | Uraian perilaku yang dilakukan aktor dan direalisasikan collaboration; elips garis utuh |
| Node | Elemen fisik saat sistem dijalankan; digambar seperti kubus |

**b. Hubungan (relationship)**
| Hubungan | Penjelasan |
|---|---|
| Dependency | Hubungan semantik; perubahan satu elemen memengaruhi elemen lain; panah putus-putus |
| Association | Hubungan struktural antar objek; garis dengan nama dan label |
| Generalization | Hubungan umum dan khusus (induk dan anak) |
| Realization | Hubungan antara spesifikasi dan perwujudannya (misal collaboration dan use case) |

**c. Diagram.** use case, activity, sequence, communication (collaboration pada versi 1.x), class, state machine, component, deployment, interaction overview, object, package, dan timing.

### 2.4 Notasi Use Case yang Dipakai (Tabel 2.1)
| Unsur | Bentuk | Makna |
|---|---|---|
| Actor | Figur orang | Orang, sistem, atau proses yang berinteraksi dengan sistem |
| Use case | Elips | Fungsi yang ditampilkan sistem, bernama kata kerja |
| Association | Garis utuh tanpa panah | Hubungan partisipasi aktor dan use case |
| Batas sistem | Persegi panjang berjudul | Sistem yang dibahas |

### 2.5 Prinsip Konsistensi
1. Nama sistem sama pada skenario, diagram, dan metadata.
2. Aktor di luar batas sistem; use case di dalam batas sistem.
3. Aktor hanya dihubungkan dengan fungsi yang disebut dalam skenario.
4. Dua use case tidak dihubungkan sebagai urutan kegiatan.
5. Tidak menambahkan fungsi atau aturan bisnis yang tidak disediakan.
6. Artefak laboratorium dan akademik dipisah.
7. Include, extend, dan generalization belum dipakai pada pertemuan ini.

Garis asosiasi menunjukkan **partisipasi**, bukan alur kegiatan. Urutan kegiatan dijelaskan pada use case description atau activity diagram.

## 3. Studi Kasus LAB

### 3.1 Skenario dan Kebutuhan
*Mahasiswa melihat informasi ketersediaan peralatan melalui sistem. Petugas laboratorium mengelola data peralatan. Pertemuan ini hanya menggambarkan hubungan kedua peran dengan fungsi tersebut.*

| ID | Aktor | Fungsi |
|---|---|---|
| LAB-R01 | Mahasiswa | Lihat ketersediaan peralatan |
| LAB-R02 | Petugas laboratorium | Kelola data peralatan |

### 3.2 Langkah Pengerjaan
1. Membaca skenario dan menandai dua peran serta dua fungsi.
2. Mencatat tabel kebutuhan pada `01_skenario/P02_LAB_skenario_v01.md`.
3. Membuat diagram kosong di draw.io dan menyimpan sebagai `P02_2406048_LAB_notasi_usecase_v01.drawio`.
4. Mengaktifkan pustaka UML dan UML 2.5 (More Shapes, Apply).
5. Menggambar batas sistem berjudul *Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus*.
6. Meletakkan Mahasiswa (kiri) dan Petugas Laboratorium (kanan) di luar batas sistem.
7. Meletakkan elips *Lihat ketersediaan peralatan* dan *Kelola data peralatan* di dalam batas sistem.
8. Menghubungkan Mahasiswa ke *Lihat ketersediaan peralatan* dan Petugas ke *Kelola data peralatan* dengan garis utuh tanpa panah; kedua elips tidak dihubungkan.
9. Mengisi metadata (ID artefak LAB-P02-UC, jenis Use case diagram, status LATIHAN NOTASI, sumber LAB-R01 dan LAB-R02).
10. Menyimpan, menutup dan membuka ulang sumber, lalu mengekspor PNG dengan nama dan versi yang sama.

### 3.3 Hasil
`P02_2406048_LAB_notasi_usecase_v01.drawio`, `P02_2406048_LAB_notasi_usecase_v01.png`, `P02_LAB_skenario_v01.md`.

## 4. Tugas SIA: Pemeriksaan dan Perbaikan Notasi

### 4.1 Skenario dan Kebutuhan
*Mahasiswa melihat jadwal kuliah melalui Sistem Informasi Akademik. Admin akademik mengelola jadwal kuliah. Mahasiswa tidak mengelola jadwal, dan admin tidak dihubungkan dengan fungsi melihat jadwal sebagai pengguna mahasiswa.*

| ID | Aktor | Fungsi |
|---|---|---|
| SIA-R01 | Mahasiswa | Lihat jadwal kuliah |
| SIA-R02 | Admin Akademik | Kelola jadwal kuliah |

### 4.2 Langkah Pengerjaan
1. Mencatat SIA-R01 dan SIA-R02 pada `P02_SIA_skenario_v01.md`.
2. Menyiapkan diagram awal yang sengaja keliru dan menyimpannya sebagai `P02_2406048_SIA_perbaikan_notasi_v01.drawio` dengan status DIAGRAM AWAL UNTUK KOREKSI.
3. Menemukan kesalahan dan mengisi tabel temuan.
4. Memperbaiki diagram dan menyimpan sebagai `P02_2406048_SIA_notasi_v01.drawio`.
5. Meminta pemeriksa mencocokkan hasil dengan skenario, menuliskan empat koreksi, satu alasan mengapa asosiasi bukan alur proses, dan hasil uji buka ulang sumber.

### 4.3 Tabel Temuan dan Perbaikan
| No | Temuan | Perbaikan | Alasan |
|:--:|---|---|---|
| 1 | Aktor Mahasiswa di dalam batas sistem | Dipindahkan ke luar batas sistem | Aktor adalah peran eksternal, bukan bagian sistem |
| 2 | *Lihat jadwal kuliah* digambar sebagai kotak biasa | Diubah menjadi elips | Use case digambar sebagai elips |
| 3 | Mahasiswa dihubungkan ke *Kelola jadwal kuliah* | Garis dihapus; Admin Akademik dihubungkan | Mahasiswa tidak mengelola jadwal menurut skenario |
| 4 | Judul memakai sistem laboratorium | Diganti *Sistem Informasi Akademik* | Judul harus sesuai kasus agar artefak tidak tertukar |

Hubungan akhir: Mahasiswa — Lihat jadwal kuliah; Admin Akademik — Kelola jadwal kuliah; keduanya di dalam batas Sistem Informasi Akademik.

**Mengapa garis asosiasi bukan alur proses:** asosiasi hanya menyatakan aktor berpartisipasi pada suatu fungsi. Urutan kegiatan tidak dinyatakan oleh garis itu, sehingga menghubungkan dua elips akan menyiratkan urutan yang tidak dimaksudkan.

### 4.4 Hasil
`P02_2406048_SIA_perbaikan_notasi_v01.drawio`/`.png`, `P02_2406048_SIA_notasi_v01.drawio`/`.png`, `P02_SIA_skenario_v01.md`.

## 5. Pemeriksaan (Checklist LAB dan SIA)
- ✓ Judul diagram sesuai kasus.
- ✓ Semua aktor di luar batas sistem.
- ✓ Semua use case berbentuk elips dan berada di dalam batas sistem.
- ✓ Nama fungsi sesuai skenario.
- ✓ Asosiasi menghubungkan peran dan fungsi yang tepat.
- ✓ Tidak ada garis urutan antarfungsi.
- ✓ Metadata lengkap dan tidak tertukar antar kasus.
- ✓ Nama berkas dan nomor versi konsisten.
- ✓ Sumber dapat dibuka dan disunting; ekspor sesuai sumber terkini.

## 6. Kendala dan Solusi
[isi kendala dan solusi]

## 7. Kesimpulan
Notasi dasar use case diagram (aktor, use case, batas sistem, dan asosiasi) berhasil diterapkan pada kasus LAB dan diperbaiki pada kasus SIA. Empat kesalahan notasi pada diagram SIA berhasil ditemukan dan dikoreksi beserta alasannya. Konsistensi nama, penempatan elemen, dan versi berkas dijaga sehingga artefak kedua kasus tidak tertukar.

## 8. Referensi
1. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
2. OMG. (2017). *Unified Modeling Language, Version 2.5.1*.
3. Dokumentasi draw.io. https://www.drawio.com/docs/