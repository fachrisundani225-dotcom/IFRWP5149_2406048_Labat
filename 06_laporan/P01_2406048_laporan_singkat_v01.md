# LAPORAN PRAKTIKUM PERTEMUAN 1
## Pengenalan Lingkungan Praktikum dan Kakas Pemodelan UML
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io (diagrams.net), Visual Studio Code, Git dan GitHub |
| **Studi kasus** | Orientasi kasus S-ORI-01 (berlaku untuk LAB dan SIA) |
| **Tanggal** | [02_10_2026] |

---

## 1. Tujuan Pembelajaran
1. Membuat workspace sesuai struktur yang ditetapkan dan menunjukkan lokasi berkasnya.
2. Membuka kakas UML, membuat kanvas, menempatkan elemen latihan, menghubungkannya, dan menyimpan berkas sumber.
3. Membuka kembali berkas sumber untuk membuktikan diagram tetap dapat disunting.
4. Mengisi logbook yang mencatat kakas, pekerjaan, pemeriksaan, kendala, dan tindak lanjut.

## 2. Landasan Teori

### 2.1 UML dan Kakas Pemodelan
UML (Unified Modeling Language) adalah bahasa pemodelan untuk menggambarkan analisis dan desain sistem berorientasi objek. draw.io, Visual Paradigm, dan StarUML adalah kakas untuk menggambar atau mengelola model. Kemampuan mengoperasikan menu kakas tidak sama dengan kemampuan membenarkan isi model. Karena itu Pertemuan 1 hanya menguji operasi kakas, sedangkan ketepatan model diperiksa bertahap pada pertemuan berikutnya.

### 2.2 Berkas Sumber dan Berkas Ekspor
Pada draw.io, format `.drawio` adalah berkas sumber yang menyimpan seluruh diagram dan dapat dibuka kembali. Gambar ekspor (PNG atau SVG) berguna untuk peninjauan tetapi tidak boleh menjadi satu-satunya berkas yang dikumpulkan. Menu *Save As* menyimpan sumber, sedangkan *Export as* menghasilkan gambar. Kegagalan membuka kembali sumber dianggap temuan penting meskipun gambar ekspornya baik.

### 2.3 Elemen Dasar Activity Diagram
Latihan memakai tiga unsur activity diagram:
| Unsur | Fungsi |
|---|---|
| Initial node (node awal) | Titik awal alur |
| Action (aktivitas) | Satu langkah kegiatan |
| Activity final node (node akhir) | Titik akhir alur |

Ketiganya dihubungkan oleh alur kontrol (control flow) berupa panah berarah.

### 2.4 SOP Workspace dan Penamaan
- Satu folder induk berpola `IFRWP5149_<NIM>_LabAlat`, tidak membuat beberapa folder induk seperti *final* atau *final_baru*.
- Subfolder sesuai template; README berisi identitas, kasus, kakas, daftar isi folder, dan status.
- Diagram latihan disimpan di `03_latihan_tools`, bukan di folder model analisis, agar tidak dianggap model tervalidasi.
- Pola nama: `P<dua digit>_<NIM>_<jenis_artefak>_v<dua digit>.<ekstensi>`. Versi mulai dari v01 dan naik ke v02 hanya setelah ada perubahan isi yang dicatat di logbook. Berkas ekspor memakai versi yang sama dengan sumbernya.
- Template metadata memuat: ID artefak, judul, pertemuan, sumber skenario, jenis dan status, kakas, pembuat, versi dan tanggal, asumsi atau pertanyaan, pemeriksaan, dan riwayat revisi.

## 3. Konteks Kasus: S-ORI-01
Studi kasus semester ini adalah Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus (LAB), disertai tugas pada Sistem Informasi Akademik (SIA). Untuk latihan alat dipakai skenario orientasi **S-ORI-01**: mahasiswa membuka daftar peralatan dan melihat informasi ketersediaan.

| Aspek | Ketentuan latihan |
|---|---|
| Aktor konteks | Mahasiswa/peminjam |
| Batas sistem | Sistem informasi laboratorium; perangkat fisik dan serah-terima tidak dimodelkan |
| Aturan bisnis | Belum ditetapkan; tidak boleh mengarang alur persetujuan atau denda |
| Kriteria penerimaan | Berkas sumber ada, dapat dibuka kembali, memuat elemen dan penghubung yang diminta, dan bertanda "latihan, belum divalidasi" |

Pertanyaan yang belum diputuskan (misalnya apakah daftar hanya dapat dilihat setelah masuk dan bagaimana ketersediaan dihitung) dicatat sebagai pertanyaan, bukan sebagai aturan.

## 4. Pelaksanaan

### 4.1 Setup Workspace (berlaku untuk LAB dan SIA)
1. Membuat folder induk `IFRWP5149_2406048_LabAlat` dengan subfolder `00_administrasi`, `01_skenario`, `02_template`, `03_latihan_tools`, `04_model_analisis`, `05_model_desain`, `06_laporan`.
2. Membuat `README.md`, `S-ORI-01_orientasi_kasus_v01.md`, template metadata, dan logbook Pertemuan 1.
3. Menginisialisasi repository Git dan membuat commit awal (*siapkan workspaces IFRWP5149*).
4. Memeriksa bahwa berkas dapat dibuka dari folder proyek, bukan hanya dari daftar *recent files*.

### 4.2 Latihan Diagram UML Sederhana
Activity diagram S-ORI-01 dengan tepat empat elemen berurutan:

node awal → *Buka daftar peralatan* → *Lihat informasi ketersediaan* → node akhir

Langkah: membuat diagram kosong dan memberi judul *Latihan kakas — S-ORI-01*; memilih bentuk dari pustaka activity; meletakkan empat elemen; mengubah dua label aktivitas; menambah tiga penghubung berarah yang benar-benar terhubung ke elemen; menyimpan sumber; mengekspor PNG; menutup dan membuka ulang berkas, memindahkan satu elemen, menyimpan, lalu mengekspor ulang agar sumber dan hasil ekspor sama. Diagram diberi catatan *Belum divalidasi sebagai model proses*.

## 5. Hasil
| Artefak | Berkas | Fungsi |
|---|---|---|
| Folder proyek dan README | `README.md` | Membuktikan workspace tertata |
| Orientasi kasus | `S-ORI-01_orientasi_kasus_v01.md` | Mencatat skenario latihan, batas, dan pertanyaan |
| Template metadata | `template_metadata_artefak_v01.md` | Kesiapan dokumentasi artefak |
| Diagram latihan | `P01_2406048_latihan_activity_v01.drawio` dan `.png` | Bukti penggunaan fitur dasar kakas |
| Logbook | `P01_2406048_logbook_v01.md` | Rekam prosedur dan pemeriksaan |
| Laporan singkat | `P01_2406048_laporan_singkat_v01.md` | Ringkasan hasil dan kendala |

## 6. Pemeriksaan (Checklist)
- ✓ Folder induk memakai NIM dan nama kasus yang benar.
- ✓ README menjelaskan identitas, kakas, dan status latihan.
- ✓ Logbook serta template metadata tersedia dan dapat dibaca.
- ✓ Diagram memuat empat elemen, tiga alur penghubung, dan label terbaca.
- ✓ Diagram diberi status belum divalidasi; tidak ada aturan bisnis tambahan yang diklaim sebagai fakta.
- ✓ Berkas sumber dapat dibuka kembali dan disunting.
- ✓ Gambar ekspor sesuai versi terakhir sumber.
- ✓ Nama dan nomor versi sumber serta ekspor konsisten.
- ✓ Arsip pengumpulan dapat dibuka dan tidak memuat kredensial atau data pribadi nyata.

## 7. Kendala dan Solusi
[isi kendala dan solusi]

## 8. Kesimpulan
Workspace praktikum untuk kasus LAB dan SIA telah disiapkan dengan struktur, aturan penamaan, dan versi yang konsisten. Fitur dasar draw.io (membuat kanvas, menempatkan elemen, menghubungkan, menyimpan sumber, mengekspor, dan membuka ulang) berhasil dipraktikkan. Diagram latihan berstatus belum divalidasi sehingga tidak dianggap model analisis, dan folder `04_model_analisis` dan `05_model_desain` sengaja dibiarkan kosong pada pertemuan ini.

## 9. Referensi
1. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
2. Dokumentasi draw.io. https://www.drawio.com/docs/
3. OMG. (2017). *Unified Modeling Language, Version 2.5.1*. https://www.omg.org/spec/UML/2.5.1/About-UML/