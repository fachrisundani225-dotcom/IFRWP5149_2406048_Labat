# LAPORAN PRAKTIKUM PERTEMUAN 6
## Activity Diagram: Dari Skenario ke Alur Aktivitas
### Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149)

| | |
|---|---|
| **Nama** | Fachri Sundani |
| **NIM** | 2406048 |
| **Program Studi** | S1 Teknik Informatika, Institut Teknologi Garut |
| **Kakas** | draw.io |
| **Studi kasus** | LAB (7 activity diagram) dan SIA (Input Nilai sampai Lihat KHS) |
| **Tanggal** | [06-11-2026] |

---

## 1. Tujuan Pembelajaran
1. Menyusun alur utama dari Skenario Normal dengan satu initial node, action berurutan, dan satu atau lebih activity final node tanpa alur terputus.
2. Mengubah Skenario Alternative menjadi decision dengan guard lengkap, lalu mengembalikannya lewat merge atau mengakhirinya pada jalur akhir yang jelas.
3. Memakai fork dan join sebagai pasangan untuk dua proses paralel.
4. Mengelompokkan action ke swimlane sesuai aktor pada tabel skenario.
5. Menelusurkan setiap action ke langkah tabel skenario Pertemuan 5 dan memeriksa dengan checklist.

## 2. Landasan Teori

### 2.1 Pengertian Activity Diagram
Activity diagram adalah diagram UML yang memodelkan alur kegiatan sebuah proses: urutan action, percabangan keputusan, proses paralel, dan pembagian tanggung jawab antar pelaku. Bila use case diagram menunjukkan fungsi yang disediakan sistem dan tabel skenario menguraikannya menjadi langkah Kegiatan dan Respon sistem, activity diagram menggambarkan langkah itu sebagai alur dari awal sampai selesai. Masukannya adalah **tabel skenario**, sehingga setiap action harus dapat ditunjuk sumber langkahnya.

### 2.2 Unsur Activity Diagram (OMG UML 2.5.1)
| Unsur | Bentuk | Makna dan aturan |
|---|---|---|
| Initial node | Lingkaran hitam | Titik awal; tepat satu per diagram |
| Action | Persegi panjang sudut membulat | Satu langkah dari tabel skenario, ditulis kata kerja dan objek |
| Control flow | Panah | Urutan pelaksanaan |
| Decision | Belah ketupat, satu masuk banyak keluar | Percabangan bersyarat; setiap alur keluar wajib punya guard dalam kurung siku |
| Merge | Belah ketupat, banyak masuk satu keluar | Penggabungan cabang kembali ke alur utama |
| Fork | Batang tebal | Membagi alur menjadi proses paralel |
| Join | Batang tebal | Menyatukan proses paralel; alur lanjut setelah semuanya selesai |
| Activity final node | Lingkaran berpusat | Titik akhir; semua jalur bermuara ke sini atau ke merge yang menuju ke sini |
| Swimlane | Kolom partisi | Mengelompokkan action menurut pelaku |

### 2.3 Aturan Menggambar
a. Tepat satu initial node dan minimal satu activity final node; tidak ada action terputus.
b. Setiap decision punya merge pasangan, kecuali cabang yang berakhir di activity final node.
c. Setiap alur keluar decision berlabel guard; guard singkat, saling lepas, dan bersama-sama menutup semua kemungkinan.
d. Fork selalu berpasangan dengan join; proses paralel tidak disatukan dengan merge karena merge tidak menunggu proses lain.
e. Nama action sama dengan bunyi langkah skenario.
f. Action ditempatkan pada swimlane aktor yang melakukannya; action sistem pada swimlane Sistem.
g. Collaboration tidak digambar pada activity diagram.

### 2.4 Pemetaan Tabel Skenario ke Activity Diagram (Tabel 6.2)
| Unsur tabel skenario P5 | Menjadi pada activity diagram |
|---|---|
| Skenario Normal | Alur utama dari initial node ke activity final node |
| Skenario Alternative | Cabang decision dengan guard |
| Langkah include | Action wajib pada alur utama |
| Langkah extend | Cabang decision dengan condition yang sama dengan diagram P4 |
| Kolom Kegiatan | Action pada swimlane aktor |
| Kolom Respon sistem | Action pada swimlane Sistem |
| Skenario Akhir | Activity final node |
| Dua pemeriksaan tidak saling bergantung | Fork dan join |

## 3. Studi Kasus LAB: Tujuh Activity Diagram

Tujuh use case utama (UC01, UC02, UC03, UC05, UC06, UC07, UC11) masing-masing mendapat satu activity diagram. LAB-UC04 dan LAB-UC12 tercakup sebagai action include, sedangkan LAB-UC08, UC09, dan UC10 tercakup sebagai cabang varian pada Activity Kelola Data.

### 3.1 Activity Lihat Ketersediaan Peralatan (LAB-UC01, Tabel 5.3)
Swimlane: Peminjam, Sistem.
Initial node → *Membuka fungsi Lihat Ketersediaan Peralatan* (Peminjam) → *Menampilkan daftar peralatan beserta status ketersediaannya* (Sistem) → decision *Peralatan tersedia?* → [tidak tersedia] *Menampilkan pesan tidak ada peralatan yang tersedia*; [tersedia] langsung → merge → activity final node.

### 3.2 Activity Kelola Data Peralatan (LAB-UC02, UC08, UC09, UC10)
Swimlane: Petugas Laboratorium, Sistem.
Alur bersama: membuka fungsi, menampilkan daftar data, memilih bentuk pengelolaan, lalu decision *Bentuk pengelolaan yang dipilih?*:
- [tambah]: menampilkan formulir data peralatan baru, mengisi data peralatan baru (UC08).
- [ubah]: memilih data yang akan diubah (UC09), menampilkan data saat ini, decision *Data peralatan ditemukan?* ([ditemukan] mengubah data; [tidak ditemukan] pesan data tidak ditemukan).
- [hapus]: memilih data yang akan dihapus (UC10), memeriksa peralatan tidak sedang dipinjam dan tidak memiliki pengajuan aktif, decision *Syarat penghapusan terpenuhi?* ([terpenuhi] mengonfirmasi penghapusan; [tidak terpenuhi] menolak penghapusan dan menampilkan pesan peralatan masih terpakai).

Cabang bermuara ke merge, lalu: memeriksa kelengkapan dan keabsahan data, decision *Data lengkap dan sah?* ([lengkap dan sah] menyimpan perubahan lalu menyimpan dan menampilkan konfirmasi; [tidak lengkap atau tidak sah] menolak penyimpanan dan menampilkan pesan kesalahan data) → activity final node.

### 3.3 Activity Peminjaman (LAB-UC03, Tabel 5.1)
Swimlane: Mahasiswa, Sistem, Petugas Laboratorium (Petugas muncul karena langkah memproses keputusan dijalankan petugas).
*Mengisi formulir pengajuan peminjaman* (Mahasiswa) → *Menyimpan data pengajuan peminjaman* (Sistem) → *Periksa Ketersediaan (dari LAB-UC04)* sebagai action include (Sistem) → decision *Peralatan tersedia?*: [tersedia] *Memproses keputusan peminjaman* (Petugas); [tidak tersedia] *Menerima pemberitahuan pengajuan tidak terpenuhi* (Mahasiswa) → merge → *Mencatat hasil akhir pengajuan* (Sistem) → decision *Mahasiswa memilih cetak bukti?*: [ya, memilih cetak] *Cetak Bukti Pengajuan (dari LAB-UC05)* sebagai cabang extend; [tidak] langsung → merge → activity final node.

### 3.4 Activity Cetak Bukti Pengajuan (LAB-UC05, Tabel 5.5)
Swimlane: Mahasiswa, Sistem. Alur dimulai dari konteks extend (pengajuan sudah tercatat berstatus Menunggu Keputusan, pada extension point *Bukti pengajuan tersedia*).
Initial node → decision *Mahasiswa memilih cetak bukti?* → [ya, memilih cetak] *Menampilkan bukti pengajuan dengan nomor pengajuan dan status Menunggu Keputusan* (Sistem) → *Mengonfirmasi pencetakan* (Mahasiswa) → *Mencetak bukti pengajuan* (Sistem); [tidak] *Menutup konfirmasi tanpa mencetak bukti dan pengajuan tetap tersimpan* (Sistem) → merge → activity final node.

### 3.5 Activity Proses Keputusan Peminjaman (LAB-UC06, Tabel 5.10; tugas mandiri)
Swimlane: Petugas Laboratorium, Sistem. Mahasiswa tidak digambar karena tidak melakukan langkah apa pun pada skenario ini.
*Membuka daftar pengajuan yang berstatus Menunggu Keputusan* (Petugas) → *Menampilkan daftar pengajuan yang berstatus Menunggu Keputusan* (Sistem) → decision *Pengajuan dapat diproses?*: [dapat diproses] *Memilih pengajuan dan menetapkan persetujuan atau penolakan* (Petugas) → decision *Pengajuan disetujui?* ([disetujui] *Mengubah status pengajuan menjadi Disetujui dan menampilkan konfirmasi*; [ditolak] *Mengubah status pengajuan menjadi Ditolak dan menampilkan konfirmasi penolakan*) → merge → activity final node; [tidak dapat diproses] *Menampilkan pesan pengajuan tidak dapat diproses* → activity final node (status tidak berubah).

### 3.6 Activity Pengembalian (LAB-UC11, Tabel 5.12 dan 5.13)
Swimlane: Mahasiswa, Sistem, Petugas Laboratorium.
*Menyerahkan peralatan yang dipinjam* (Mahasiswa) → *Catat Pengembalian Peralatan (LAB-UC11)* (Petugas) → **fork** → dua pemeriksaan paralel pada swimlane Petugas: *Periksa Kondisi Peralatan (dari LAB-UC12): kondisi fisik* dan *Periksa kelengkapan aksesori peralatan (unsur proses baru)* → **join** → decision *Kondisi peralatan baik dan lengkap?*: [baik dan lengkap] *Perbarui status peralatan menjadi tersedia* (Sistem); [rusak atau tidak lengkap] *Catat kerusakan atau kekurangan dan jadwalkan perbaikan* (Petugas) → merge → *Menutup transaksi peminjaman* (Sistem) → activity final node.

**Penandaan unsur baru:** *Periksa kelengkapan aksesori peralatan* adalah kebutuhan proses baru dari jobsheet untuk melatih fork dan join. Unsur ini tidak berasal dari LAB-R01 s.d. R11, tidak ada pada diagram P4, dan tidak ada pada tabel skenario P5, sehingga diberi keterangan *unsur proses baru* agar tidak dikira berasal dari pertemuan sebelumnya.

### 3.7 Activity Lihat Laporan Peminjaman (LAB-UC07, Tabel 5.11)
Swimlane: Kepala Laboratorium, Sistem (satu-satunya activity dengan aktor Kepala Laboratorium).
*Membuka fungsi Lihat Laporan Peminjaman* → *Menampilkan daftar periode laporan* → *Memilih periode laporan* → *Menampilkan laporan peminjaman periode yang dipilih* → decision *Ada data peminjaman?* ([tidak ada] *Menampilkan pesan tidak ada data peminjaman pada periode tersebut*; [ada] langsung) → merge → activity final node. Tidak ada fitur tambahan seperti ekspor atau unduh karena tidak ada pada tabel skenario.

### 3.8 Tugas Mandiri: Perbandingan Activity Keputusan
Diagram digambar tanpa membuka berkas pembanding, diperiksa dengan checklist, lalu dibandingkan dengan berkas pembanding.
- Perbedaan yang ditemukan: [isi]
- Perbaikan yang dilakukan: [isi]

### 3.9 Berkas LAB
Di `04_model_analisis/P06/LAB`: `P06_2406048_LAB_activity_lihat_ketersediaan_v01`, `..._kelola_data_v01`, `..._peminjaman_v01`, `..._cetak_bukti_v01`, `..._keputusan_v01`, `..._pengembalian_v01`, `..._laporan_v01`, masing-masing `.drawio` dan `.png`.

## 4. Tugas SIA: Input Nilai sampai Lihat KHS

### 4.1 Ketentuan
| Unsur wajib | Ketentuan |
|---|---|
| Proses | Input Nilai Mata Kuliah sampai Lihat KHS, diturunkan dari tabel SIA-UC08 dan SIA-UC09 |
| Swimlane | Empat: Dosen, Sistem, Admin Akademik, Mahasiswa |
| Decision | Minimal satu decision kelengkapan nilai dengan guard [lengkap] dan [belum lengkap]; cabang [belum lengkap] kembali ke Dosen lalu bergabung lewat merge |
| Fork dan join | Satu pasang setelah nilai disahkan: menerbitkan KHS pada portal akademik dan mengirim pemberitahuan hasil studi berjalan paralel, disatukan sebelum Mahasiswa melihat KHS |
| Awal dan akhir | Tepat satu initial node dan satu activity final node |
| Keterlacakan | Setiap action tertelusur ke tabel skenario SIA P5 |

### 4.2 Alur Diagram
1. Initial node.
2. Dosen: *Memasukkan nilai mata kuliah*.
3. Sistem: *Menyimpan nilai mata kuliah*.
4. Decision *Nilai sudah lengkap?*: [belum lengkap] Dosen *Melengkapi nilai mata kuliah yang belum lengkap* → merge; [lengkap] → merge.
5. Admin Akademik: *Memeriksa dan mengesahkan nilai*.
6. Sistem: *Menyiapkan publikasi hasil studi*.
7. **Fork** → paralel: Sistem *Menerbitkan KHS pada portal akademik* dan Sistem *Mengirim pemberitahuan hasil studi kepada mahasiswa* → **join**.
8. Mahasiswa: *Melihat KHS*.
9. Activity final node.

### 4.3 Penelusuran ke Tabel Skenario
| Action | Sumber |
|---|---|
| Memasukkan dan menyimpan nilai | SIA-UC08 (langkah menginput dan menyimpan nilai) |
| Decision kelengkapan nilai, melengkapi nilai | Alternatif SIA-UC08 (nilai belum lengkap atau tidak sah) |
| Memeriksa dan mengesahkan nilai, menyiapkan publikasi, menerbitkan KHS, mengirim pemberitahuan | Peralihan nilai menjadi hasil studi terpublikasi (aturan "KHS hanya menampilkan nilai yang sudah dipublikasikan") |
| Melihat KHS | SIA-UC09 |

### 4.4 Activity SIA per Use Case
| Activity | Swimlane | Ringkasan alur dan guard |
|---|---|---|
| Ajukan KRS (SIA-UC03) | Mahasiswa, Sistem | Membuka fungsi → daftar mata kuliah → memilih mata kuliah → mengirim pengajuan → *Validasi KRS (include)* → decision *KRS valid?* ([valid] menyimpan pengajuan berstatus Menunggu Keputusan; [tidak valid] pesan kesalahan validasi) → decision *Mahasiswa memilih unduh bukti?* ([ya, memilih unduh] *Unduh Bukti Pengajuan KRS (extend)*; [tidak]) → final |
| Input Nilai (SIA-UC08) | Dosen, Sistem | Membuka fungsi → daftar mata kuliah dan mahasiswa → memasukkan nilai → menyimpan → decision *Nilai sudah lengkap?* ([lengkap] konfirmasi tersimpan; [belum lengkap] melengkapi nilai) → final |
| Lihat KHS (SIA-UC09) | Mahasiswa, Sistem | Membuka fungsi → daftar semester → memilih semester → decision *KHS tersedia?* ([tersedia] menampilkan KHS; [belum tersedia] pesan KHS belum tersedia) → final |
| Lihat Kalender Akademik, Lihat dan Kelola Jadwal Kuliah, Kelola Data Mahasiswa, Proses Keputusan KRS, Unduh Bukti KRS | Aktor terkait dan Sistem | Disusun dari tabel skenario masing-masing |

Berkas di `04_model_analisis/P06/SIA`, penamaan `P06_2406048_SIA_activity_<nama>_v01.drawio` dan `.png`.

## 5. Pemeriksaan (Checklist)
- ✓ Tepat satu initial node dan minimal satu activity final node; tidak ada action terputus.
- ✓ Setiap decision punya guard pada semua alur keluar; guard saling lepas dan lengkap.
- ✓ Setiap cabang kembali melalui merge atau bermuara ke activity final node dengan keadaan akhir jelas.
- ✓ Fork berpasangan dengan join; proses paralel disatukan oleh join, bukan merge.
- ✓ Setiap action berada pada swimlane aktor yang tepat; respons sistem pada swimlane Sistem.
- ✓ Setiap action tertelusur ke tabel skenario P5 dan bernama sama dengan langkah sumbernya.
- ✓ Include digambar sebagai action wajib; extend sebagai cabang bersyarat dengan condition yang sama ([ya, memilih cetak]).
- ✓ Unsur proses baru (aksesori peralatan) diberi keterangan dan tidak diklaim berasal dari P3, P4, atau P5.
- ✓ Collaboration tidak digambar sebagai action atau swimlane.
- ✓ Kepala Laboratorium tidak muncul pada Activity Peminjaman dan Pengembalian, hanya pada Activity Lihat Laporan.
- ✓ Ketujuh activity LAB tersedia sebagai v01 beserta PNG.
- ✓ Berkas P04 dan dokumen P05 tidak diubah; sumber dapat dibuka dan ekspor sesuai sumber.

## 6. Kendala dan Solusi
| No | Kendala | Solusi |
|:--:|---|---|
| 1 | Sulit menentukan swimlane untuk langkah yang dilakukan sistem dan petugas sekaligus | Kembali ke tabel skenario: kolom Kegiatan menjadi swimlane aktor dan kolom Respon sistem menjadi swimlane Sistem |
| 2 | Lupa memberi guard pada salah satu alur keluar decision | Setiap decision diperiksa satu per satu sampai semua alur keluar berlabel dan guard saling lepas |
| 3 | Garis alur menyilang melewati beberapa swimlane sehingga diagram sulit dibaca | Letak action dan merge diatur ulang, dan titik tekuk garis dirapikan |
| 4 | Ragu antara memakai merge atau join untuk menyatukan alur | Aturan jobsheet: join hanya untuk proses paralel dari fork, merge untuk cabang decision |
| 5 | Pada Activity Pengembalian, action aksesori tidak ada di skenario P5 | Action diberi keterangan *unsur proses baru* sesuai ketentuan jobsheet |
| 6 | Activity Kelola Data memiliki banyak cabang sehingga diagram sangat panjang | Cabang tambah, ubah, hapus disusun berurutan lalu digabung pada satu merge |
| 7 | Diagram SIA harus memuat empat swimlane dan fork–join sekaligus | Alur ditulis dulu sebagai daftar langkah dengan penelusuran ke SIA-UC08 dan SIA-UC09, baru digambar |

## 7. Kesimpulan
Tujuh activity diagram LAB berhasil diturunkan dari tabel skenario Pertemuan 5 dengan swimlane sesuai aktor, decision berguard lengkap, merge, serta fork dan join pada Activity Pengembalian. Pada kasus SIA, activity diagram Input Nilai sampai Lihat KHS dirancang dengan empat swimlane, decision kelengkapan nilai, dan satu pasang fork–join. Keterlacakan dari kebutuhan, use case, skenario, hingga activity diagram terjaga, dan unsur di luar skenario diberi penanda.

## 8. Referensi
1. OMG. (2017). *Unified Modeling Language, Version 2.5.1*.
2. IFRWP5149, Praktikum Analisis dan Desain Berorientasi Objek (RPS), Institut Teknologi Garut, 2026.
3. Jobsheet Praktikum Pertemuan 4 dan 5 IFRWP5149.
4. Fowler, M. *UML Distilled*. Addison-Wesley.
5. Dokumentasi draw.io. https://www.drawio.com/docs/