# Model analisis use case LAB P03

## Batas model

Model P03 merupakan pengembangan kumulatif dari LAB P02. LAB-UC01 Lihat Ketersediaan Peralatan dan LAB-UC02 Kelola Data Peralatan tetap dipertahankan. P03 menambahkan pengajuan peminjaman, pemeriksaan ketersediaan, bukti pengajuan, keputusan petugas, dan laporan peminjaman (LAB-R03–LAB-R06). Model ini berfokus pada informasi serta pencatatan melalui sistem, bukan perpindahan fisik peralatan.

Mahasiswa mengajukan peminjaman dengan memilih peralatan, jumlah, dan rentang waktu. Sistem memeriksa ketersediaan sebelum menyimpan pengajuan yang lengkap dengan status Menunggu Keputusan. Setelah pengajuan tersimpan, mahasiswa dapat memilih mencetak bukti. Petugas Laboratorium mengelola data peralatan dan menetapkan keputusan Setujui atau Tolak. Kepala Laboratorium melihat laporan peminjaman.

## Aktor

| Aktor | Interaksi dengan sistem |
|:--|:--|
| Mahasiswa | LAB-UC01 Lihat Ketersediaan Peralatan; LAB-UC03 Ajukan Peminjaman; LAB-UC05 Cetak Bukti Pengajuan. |
| Petugas Laboratorium | LAB-UC02 Kelola Data Peralatan; LAB-UC06 Proses Keputusan Peminjaman. |
| Kepala Laboratorium | LAB-UC07 Lihat Laporan Peminjaman. |

Sistem bukan aktor eksternal. Sistem menjalankan pemeriksaan ketersediaan sebagai perilaku yang disertakan dalam LAB-UC03.

## Katalog use case

| ID | Nama | Asal/peran pada P03 |
|:--|:--|:--|
| LAB-UC01 | Lihat Ketersediaan Peralatan | Dipertahankan dari P02; fungsi Mahasiswa. |
| LAB-UC02 | Kelola Data Peralatan | Dipertahankan dari P02; fungsi Petugas Laboratorium. |
| LAB-UC03 | Ajukan Peminjaman | Baru pada P03; fungsi Mahasiswa untuk mengajukan alat, jumlah, dan rentang waktu. |
| LAB-UC04 | Periksa Ketersediaan | Baru pada P03; perilaku wajib yang di-include UC03. |
| LAB-UC05 | Cetak Bukti Pengajuan | Baru pada P03; perilaku opsional yang meng-extend UC03. |
| LAB-UC06 | Proses Keputusan Peminjaman | Baru pada P03; fungsi Petugas Laboratorium untuk mencatat Setujui atau Tolak. |
| LAB-UC07 | Lihat Laporan Peminjaman | Baru pada P03; fungsi Kepala Laboratorium. |

## Hubungan pada diagram

| Sumber | Hubungan | Tujuan |
|:--|:--|:--|
| Mahasiswa | Asosiasi | LAB-UC01 Lihat Ketersediaan Peralatan |
| Mahasiswa | Asosiasi | LAB-UC03 Ajukan Peminjaman |
| Mahasiswa | Asosiasi | LAB-UC05 Cetak Bukti Pengajuan |
| Petugas Laboratorium | Asosiasi | LAB-UC02 Kelola Data Peralatan |
| Petugas Laboratorium | Asosiasi | LAB-UC06 Proses Keputusan Peminjaman |
| Kepala Laboratorium | Asosiasi | LAB-UC07 Lihat Laporan Peminjaman |
| LAB-UC03 Ajukan Peminjaman | `include` | LAB-UC04 Periksa Ketersediaan |
| LAB-UC05 Cetak Bukti Pengajuan | `extend` | LAB-UC03 Ajukan Peminjaman pada extension point –Bukti pengajuan tersedia–, condition [Mahasiswa memilih cetak] |

### Alasan relasi

- **Include UC03 ke UC04:** ketersediaan alat, jumlah, dan rentang waktu harus diperiksa setiap kali sistem memproses pengajuan. Jika alat tidak tersedia, pengajuan tidak tersimpan sebagai pengajuan berhasil.
- **Extend UC05 ke UC03:** pencetakan hanya berlangsung jika Mahasiswa memilihnya pada konfirmasi setelah pengajuan tersimpan. Pengajuan tetap berhasil tanpa mencetak bukti. Extension point adalah –Bukti pengajuan tersedia–.
- **Asosiasi Mahasiswa ke UC05:** hak mencetak bukti pada skenario ini secara khusus diberikan kepada Mahasiswa.

## Pemetaan kebutuhan ke use case

| ID kebutuhan | Kebutuhan | Use case yang memenuhi |
|:--|:--|:--|
| LAB-R01 | Mahasiswa dapat melihat ketersediaan peralatan. | LAB-UC01 |
| LAB-R02 | Petugas Laboratorium dapat mengelola data peralatan. | LAB-UC02 |
| LAB-R03 | Mahasiswa dapat mengajukan peminjaman; ketersediaan diperiksa sebelum pengajuan disimpan. | LAB-UC03, LAB-UC04 |
| LAB-R04 | Mahasiswa dapat mencetak bukti pada konfirmasi pengajuan jika memilihnya. | LAB-UC03, LAB-UC05 |
| LAB-R05 | Petugas dapat menetapkan persetujuan atau penolakan pengajuan. | LAB-UC06 |
| LAB-R06 | Kepala Laboratorium dapat melihat laporan peminjaman. | LAB-UC07 |

## Aturan dan asumsi analisis

- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Sistem menyediakan informasi dan mencatat transaksi; pengambilan atau penyerahan alat secara fisik dilakukan di luar sistem.
- Pengajuan yang diterima sistem berstatus Menunggu Keputusan. Pengajuan tidak otomatis disetujui.
- Data pengajuan harus lengkap dan alat/jumlah harus tersedia pada rentang waktu yang diminta agar pengajuan tersimpan sebagai berhasil.
- Cetak bukti bersifat opsional dan tidak menentukan keberhasilan pengajuan.
- Keputusan Setujui atau Tolak dicatat oleh Petugas Laboratorium. Persetujuan belum dimodelkan sebagai reservasi teknis stok.
- Pengambilan, pengembalian, pemeriksaan kondisi, keterlambatan, dan denda belum dimodelkan pada P03. Kebutuhan tersebut tidak disimpulkan dari alur ini.
- LAB-UC02 masih merupakan use case umum kelola data peralatan; pemisahan operasi tambah, ubah, dan hapus belum menjadi bagian model P03.

## Konsistensi model

Semua kebutuhan LAB-R01–LAB-R06 direpresentasikan oleh katalog use case. Setiap use case memiliki aktor yang sesuai, pemeriksaan ketersediaan merupakan bagian wajib dari pengajuan, dan pencetakan bukti tetap opsional. Diagram, skenario P03, serta deskripsi use case P03 sebaiknya mempertahankan ID, nama, aktor, status Menunggu Keputusan, serta kondisi include/extend yang sama.
