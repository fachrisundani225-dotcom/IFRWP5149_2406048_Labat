### Elemen SIA-UC08: Input Nilai Mata Kuliah

| Elemen | Deskripsi |
|---|---|
| ID dan Nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber Kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah mahasiswa tersimpan oleh dosen pengampu. |
| Aktor Utama | Dosen |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah yang diampunya. |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah terpilih; masa perkuliahan mata kuliah telah berakhir. |
| Pascakondisi Berhasil | Nilai mahasiswa yang diisi tersimpan dengan status Belum Dipublikasikan. |
| Pascakondisi Gagal | Tidak ada nilai baru yang tersimpan; data nilai tidak berubah. |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |

**Alur utama**

| Langkah | Tindakan dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang diampu | Memeriksa dosen adalah pengampu dan masa perkuliahan telah berakhir; menampilkan daftar mahasiswa peserta |
| 2 | Mengisi nilai tiap mahasiswa | Menampung isian nilai |
| 3 | Memilih simpan | Memeriksa seluruh nilai berada dalam rentang yang sah |
| 4 | Tidak ada | Menyimpan nilai dengan status Belum Dipublikasikan |
| 5 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

**Alur alternatif atau pengecualian**
- A1: Dosen bukan pengampu (pada langkah 1): sistem menolak akses dan menampilkan pesan bahwa dosen bukan pengampu mata kuliah tersebut. Pascakondisi gagal berlaku.
- A2: Masa perkuliahan belum berakhir (pada langkah 1): sistem menolak input dan menampilkan status masa perkuliahan. Pascakondisi gagal berlaku.
- A3: Nilai di luar rentang yang sah (pada langkah 3): sistem menolak penyimpanan, menandai isian yang salah, dan meminta koreksi. Tidak ada nilai disimpan sampai semua nilai sah.