# Deskripsi use case kumulatif LAB P03

Deskripsi mencakup seluruh use case LAB-UC01–LAB-UC07 pada diagram kumulatif P03. LAB-UC01 dan LAB-UC02 dipertahankan dari P02. Batas studi kasus berlaku: sistem menangani informasi dan pencatatan; perpindahan fisik alat, pengambilan, pengembalian, kondisi, denda, serta reservasi stok teknis tidak dimodelkan.

## LAB-UC01 — Lihat ketersediaan Peralatan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC01 — Lihat ketersediaan Peralatan |
| Sumber kebutuhan | LAB-R01 (P02) |
| Tujuan | Mengetahui informasi ketersediaan peralatan. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada. |
| Pemicu | Mahasiswa memilih fungsi Lihat Ketersediaan Peralatan. |
| Prasyarat | Mahasiswa telah terautentikasi; data peralatan tersedia bagi sistem. |
| Alur utama | 1. Mahasiswa meminta informasi ketersediaan. 2. Sistem menampilkan informasi ketersediaan peralatan. |
| Alur alternatif/pengecualian | Jika informasi belum tersedia, sistem menyampaikan bahwa informasi ketersediaan belum tersedia. |
| Pascakondisi berhasil | Informasi ketersediaan ditampilkan. |
| Pascakondisi gagal | Tidak ada perubahan data; sistem menyampaikan informasi belum tersedia. |

## LAB-UC02 — Kelola data peralatan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC02 — Kelola data peralatan |
| Sumber kebutuhan | LAB-R02 (P02) |
| Tujuan | Memelihara data peralatan laboratorium. |
| Aktor utama | Petugas Laboratorium |
| Aktor pendukung | Tidak ada. |
| Pemicu | Petugas memilih fungsi Kelola Data Peralatan. |
| Prasyarat | Petugas telah terautentikasi dan memiliki hak akses sesuai peran. |
| Alur utama | 1. Petugas memilih data peralatan yang akan dikelola. 2. Sistem menampilkan data terpilih. 3. Petugas mengirim perubahan data. 4. Sistem menyimpan perubahan dan menampilkan hasil. |
| Alur alternatif/pengecualian | Jika data yang dikirim tidak dapat diproses, sistem menolak penyimpanan dan menyampaikan alasan. |
| Pascakondisi berhasil | Data peralatan yang dikelola tersimpan. |
| Pascakondisi gagal | Data peralatan tidak berubah. |

Operasi tambah, ubah, dan hapus belum dipisah pada model P03; generalization operasi tersebut baru ditambahkan pada P04.

## LAB-UC03 — Ajukan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC03 — Ajukan Peminjaman |
| Sumber kebutuhan | LAB-R03, LAB-R04 (perilaku cetak bersyarat). |
| Tujuan | Menyimpan pengajuan peminjaman yang lengkap dan peralatannya tersedia. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menjalankan LAB-UC04 Periksa Ketersediaan. |
| Pemicu | Mahasiswa memilih Ajukan Peminjaman. |
| Prasyarat | Mahasiswa terautentikasi; data peralatan tersedia. |
| Include | LAB-UC04 Periksa Ketersediaan, wajib dilakukan sebelum pengajuan disimpan. |
| Extension point | Bukti pengajuan tersedia setelah pengajuan berhasil tersimpan. |
| Extend | LAB-UC05 Cetak Bukti Pengajuan jika [mahasiswa memilih cetak]. |
| Alur utama | 1. Mahasiswa memilih peralatan, jumlah, dan rentang waktu. 2. Mahasiswa mengirim pengajuan. 3. Sistem memeriksa kelengkapan data. 4. Sistem menjalankan LAB-UC04. 5. Jika tersedia dan lengkap, sistem menyimpan pengajuan berstatus Menunggu keputusan. 6. Sistem menampilkan konfirmasi dan menyediakan bukti pengajuan. |
| Alur alternatif/pengecualian | A1 pada langkah 3: data tidak lengkap; sistem menampilkan kekurangan dan tidak menyimpan pengajuan berhasil. A2 pada langkah 4: alat/jumlah tidak tersedia; sistem menyampaikan hasil dan tidak menyimpan pengajuan berhasil. A3 pada langkah 6: jika [mahasiswa memilih cetak], jalankan LAB-UC05; jika tidak memilih, pengajuan tetap berhasil. |
| Pascakondisi berhasil | Pengajuan tersimpan dengan status Menunggu keputusan. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

## LAB-UC04 — Periksa Ketersediaan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC04 — Periksa Ketersediaan |
| Sumber kebutuhan | LAB-R03 |
| Tujuan | Menentukan apakah pilihan peralatan, jumlah, dan rentang waktu tersedia untuk pengajuan. |
| Aktor utama | Sistem (perilaku yang disertakan oleh LAB-UC03). |
| Aktor pendukung | Mahasiswa memberikan kriteria melalui LAB-UC03. |
| Pemicu | LAB-UC03 mencapai langkah pemeriksaan ketersediaan. |
| Prasyarat | Pilihan peralatan, jumlah, dan rentang waktu telah dikirim. |
| Alur utama | 1. Sistem memeriksa ketersediaan sesuai kriteria pengajuan. 2. Sistem mengembalikan hasil tersedia kepada LAB-UC03. |
| Alur alternatif/pengecualian | Jika peralatan atau jumlah tidak tersedia pada rentang waktu tersebut, sistem mengembalikan hasil tidak tersedia kepada LAB-UC03. |
| Pascakondisi berhasil | Hasil pemeriksaan tersedia diberikan kepada use case pemanggil; pemeriksaan ini sendiri tidak menyimpan pengajuan. |
| Pascakondisi gagal | Hasil tidak tersedia diberikan kepada use case pemanggil; pengajuan tidak dinyatakan berhasil. |

## LAB-UC05 — Cetak Bukti Pengajuan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC05 — Cetak Bukti Pengajuan |
| Sumber kebutuhan | LAB-R04 |
| Tujuan | Menghasilkan bukti untuk pengajuan yang telah tersimpan. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menyediakan bukti pengajuan. |
| Pemicu | Mahasiswa memilih cetak pada konfirmasi pengajuan. |
| Prasyarat | LAB-UC03 berhasil; bukti pengajuan tersedia. |
| Relasi | `extend` LAB-UC03 pada extension point bukti tersedia dengan kondisi [mahasiswa memilih cetak]. |
| Alur utama | 1. Mahasiswa memilih Cetak Bukti Pengajuan. 2. Sistem menyiapkan bukti dari pengajuan tersimpan untuk dicetak. |
| Alur alternatif/pengecualian | Jika mahasiswa tidak memilih cetak, LAB-UC05 tidak dijalankan dan pengajuan tetap berhasil. |
| Pascakondisi berhasil | Bukti pengajuan disediakan untuk pencetakan. |
| Pascakondisi gagal | Pengajuan tetap tersimpan; tidak ada bukti yang dicetak bila pilihan cetak tidak dilakukan. |

## LAB-UC06 — Proses Keputusan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC06 — Proses Keputusan Peminjaman |
| Sumber kebutuhan | LAB-R05 |
| Tujuan | Mencatat keputusan petugas atas pengajuan peminjaman. |
| Aktor utama | Petugas Laboratorium |
| Aktor pendukung | Sistem menyimpan keputusan. |
| Pemicu | Petugas memilih pengajuan untuk diproses. |
| Prasyarat | Petugas terautentikasi; pengajuan tersedia untuk diproses. |
| Alur utama | 1. Petugas memilih pengajuan. 2. Sistem menampilkan rincian pengajuan. 3. Petugas menetapkan keputusan Setujui atau Tolak. 4. Sistem menyimpan keputusan dan menampilkan hasil. |
| Alur alternatif/pengecualian | Jika pengajuan tidak tersedia untuk diproses, sistem menyampaikan bahwa keputusan tidak dapat dicatat. |
| Pascakondisi berhasil | Keputusan persetujuan atau penolakan tercatat. |
| Pascakondisi gagal | Tidak ada keputusan baru yang tersimpan. |

Keputusan tidak disimpulkan sebagai reservasi stok teknis; hal tersebut berada di luar batas skenario P03.

## LAB-UC07 — Lihat Laporan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC07 — Lihat Laporan Peminjaman |
| Sumber kebutuhan | LAB-R06 |
| Tujuan | Melihat laporan peminjaman yang disediakan sistem. |
| Aktor utama | Kepala Laboratorium |
| Aktor pendukung | Sistem menyajikan laporan. |
| Pemicu | Kepala Laboratorium memilih fungsi Lihat Laporan Peminjaman. |
| Prasyarat | Kepala Laboratorium terautentikasi dan memiliki hak akses sesuai peran. |
| Alur utama | 1. Kepala Laboratorium meminta laporan peminjaman. 2. Sistem menampilkan laporan peminjaman yang tersedia. |
| Alur alternatif/pengecualian | Jika data laporan belum tersedia, sistem menyampaikan bahwa laporan belum tersedia. |
| Pascakondisi berhasil | Laporan peminjaman ditampilkan. |
| Pascakondisi gagal | Tidak ada perubahan data; sistem menyampaikan bahwa laporan belum tersedia. |
