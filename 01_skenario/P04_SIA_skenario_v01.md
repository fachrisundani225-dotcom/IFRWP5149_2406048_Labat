Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yangdapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang iampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

Aktor


| Aktor             | Kedudukan                                              | Tujuan terhadap Sistem |
|-------------------|--------------------------------------------------------|------------------------|
| Civitas Akademika | Umum (general), baru P4                                | Peran umum warga akademik; mewariskan fungsi melihat kalender akademik kepada Mahasiswa dan Dosen. |
| Mahasiswa         | Khusus dari Civitas Akademika (aktor tetap dari P2/P3) | Melihat kalender akademik (diwarisi); melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan KRS (asosiasi langsung P2/P3, tetap); melihat KHS (asosiasi langsung, baru). |
| Dosen             | Khusus dari Civitas Akademika, baru P4                 | Melihat kalender akademik (diwarisi); menginput nilai mata kuliah yang diampu. |
| Admin Akademik    | Tetap dari P2/P3                                       | Mengelola jadwal kuliah (P2); mengelola data mahasiswa (baru). |
| Dosen Wali        | Tetap dari P3                                          | Memproses keputusan KRS. |

Katalog use case gabungan


| D        | Nama use case             | Aktor terkait     | Sumber kebutuhan | Status   | Peran dalam model                 |
|----------|---------------------------|-------------------|------------------|----------|-----------------------------------|
| SIA-UC01 | Lihat Jadwal Kuliah       | Mahasiswa         | SIA-R01 (P2)     | Tetap    | –                                 |
| SIA-UC02 | Kelola Jadwal Kuliah      | Admin Akademik    | SIA-R02 (P2)     | Tetap    | –                                 |
| SIA-UC03 | Ajukan KRS                | Mahasiswa         | SIA-R03 (P3)     | Tetap    | menyertakan SIA-UC04              |
| SIA-UC04 | Validasi KRS              | – (disertakan)    | SIA-R04 (P3)     | Tetap    | perilaku yang disertakan SIA-UC03 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa         | SIA-R05 (P3)     | Tetap    | «extend» pada SIA-UC03            |
| SIA-UC06 | Proses Keputusan KRS      | Dosen Wali        | SIA-R06 (P3)     | Tetap    | –                                 |
| SIA-UC07 | Lihat Kalender Akademik   | Civitas Akademika | SIA-R07          | **Baru** | fungsi aktor umum                 |
| SIA-UC08 | Input Nilai Mata Kuliah   | Dosen             | SIA-R08          | **Baru** | direalisasikan SIA-CO01           |
| SIA-UC09 | Lihat KHS                 | Mahasiswa         | SIA-R09          | **Baru** | direalisasikan SIA-CO02           |
| SIA-UC10 | Kelola Data Mahasiswa     | Admin Akademik    | SIA-R10          | **Baru** | use case UMUM bagi UC11–UC13      |
| SIA-UC11 | Tambah Data Mahasiswa     | (via UC10)        | SIA-R11          | **Baru** | KHUSUS dari SIA-UC10              |
| SIA-UC12 | Ubah Data Mahasiswa       | (via UC10)        | SIA-R11          | **Baru** | KHUSUS dari SIA-UC10              |
| SIA-UC13 | Hapus Data Mahasiswa      | (via UC10)        | SIA-R11          | **Baru** | KHUSUS dari SIA-UC10              |


| ID       | Nama collaboration (= nama use case) | Use case yang direalisasikan     |
|----------|--------------------------------------|----------------------------------|
| SIA-CO01 | Input Nilai Mata Kuliah              | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS                            | SIA-UC09 Lihat KHS               |