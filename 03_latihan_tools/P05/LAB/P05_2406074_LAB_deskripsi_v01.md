# Deskripsi lengkap use case kumulatif LAB P05

Dokumen ini melengkapi deskripsi LAB P05 dengan seluruh 12 use case kumulatif LAB-UC01 sampai LAB-UC12 dari P02 sampai P04. Use case yang diwarisi dari P02 dan P03 disertakan bersama use case P04 agar seluruh katalog tersedia dalam satu dokumen. LAB-UC03 dan LAB-UC11 juga menjadi skenario fokus P05. Batas kebutuhan dan relasi mengikuti diagram kumulatif P04.


## LAB-UC01 — Lihat Ketersediaan Peralatan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC01 — Lihat Ketersediaan Peralatan |
| Sumber kebutuhan | LAB-R01, LAB-R07 |
| Tujuan | Mengetahui informasi ketersediaan peralatan. |
| Aktor utama | Peminjam (Mahasiswa atau Dosen). |
| Aktor pendukung | Sistem menyediakan informasi ketersediaan. |
| Pemicu | Peminjam memilih Lihat Ketersediaan Peralatan. |
| Prasyarat | Pengguna terautentikasi dan berhak mengakses fungsi sesuai perannya. |
| Pascakondisi berhasil | Informasi ketersediaan peralatan ditampilkan. |
| Pascakondisi gagal | Tidak ada perubahan data; sistem menyampaikan jika informasi belum tersedia. |

**Alur utama:** Peminjam meminta informasi ketersediaan; sistem menampilkan informasi yang tersedia. **Alternatif:** Jika informasi belum tersedia, sistem menyampaikan kondisi tersebut. Mahasiswa dan Dosen mewarisi UC01 dari aktor umum Peminjam.

## LAB-UC02 — Kelola Data Peralatan (use case umum)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC02 — Kelola Data Peralatan |
| Sumber kebutuhan | LAB-R02, LAB-R08 |
| Tujuan | Memelihara data peralatan laboratorium melalui tambah, ubah, atau hapus. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem membaca dan menyimpan data peralatan. |
| Pemicu | Petugas memilih fungsi Kelola Data Peralatan. |
| Prasyarat | Petugas terautentikasi dan memiliki hak akses sesuai peran. |
| Generalization | LAB-UC08 Tambah Data Peralatan, LAB-UC09 Ubah Data Peralatan, dan LAB-UC10 Hapus Data Peralatan adalah bentuk khusus UC02. |
| Pascakondisi berhasil | Operasi pengelolaan yang dipilih tersimpan. |
| Pascakondisi gagal | Data peralatan tidak berubah. |

**Alur umum:** Petugas memilih salah satu operasi khusus, sistem menampilkan data/formulir yang relevan, Petugas memberikan data yang diperlukan, lalu sistem menyimpan dan mengonfirmasi hasil operasi. Detail perilaku pembeda masing-masing operasi dijelaskan di UC08–UC10.

## LAB-UC03 — Ajukan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC03 — Ajukan Peminjaman |
| Sumber kebutuhan | LAB-R03, LAB-R04, LAB-R07 |
| Tujuan | Menyimpan pengajuan peminjaman yang lengkap dan peralatannya tersedia. |
| Aktor utama | Peminjam (Mahasiswa atau Dosen). |
| Aktor pendukung | Sistem memeriksa ketersediaan melalui LAB-UC04. |
| Pemicu | Peminjam memilih Ajukan Peminjaman. |
| Prasyarat | Pengguna terautentikasi; data peralatan tersedia. |
| Include | LAB-UC04 Periksa Ketersediaan, wajib dilakukan sebelum penyimpanan. |
| Extension point | Bukti pengajuan tersedia setelah pengajuan berhasil tersimpan. |
| Extend | LAB-UC05 Cetak Bukti Pengajuan jika [Mahasiswa memilih cetak]. |
| Collaboration | LAB-CO01 Ajukan Peminjaman merealisasikan UC03. |
| Pascakondisi berhasil | Pengajuan tersimpan dengan status Menunggu Keputusan. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

**Alur utama:** 1. Peminjam memilih peralatan, jumlah, dan rentang waktu. 2. Peminjam mengirim pengajuan. 3. Sistem memeriksa kelengkapan data. 4. Sistem menjalankan LAB-UC04. 5. Jika lengkap dan tersedia, sistem menyimpan pengajuan berstatus Menunggu Keputusan. 6. Sistem menampilkan konfirmasi dan menyediakan bukti pengajuan.

**Alur alternatif:** A1 pada langkah 3: data tidak lengkap; sistem menampilkan kekurangan dan tidak menyimpan pengajuan berhasil. A2 pada langkah 4: peralatan/jumlah tidak tersedia; sistem menyampaikan hasil dan tidak menyimpan pengajuan berhasil. A3 pada langkah 6: LAB-UC05 dijalankan hanya jika [Mahasiswa memilih cetak]; tanpa pilihan cetak, pengajuan tetap berhasil. Extend ini hanya berlaku untuk aktor Mahasiswa.

## LAB-UC04 — Periksa Ketersediaan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC04 — Periksa Ketersediaan |
| Sumber kebutuhan | LAB-R03 |
| Tujuan | Menentukan apakah peralatan, jumlah, dan rentang waktu pengajuan tersedia. |
| Aktor utama | Sistem; use case ini di-include oleh LAB-UC03. |
| Aktor pendukung | Peminjam memberikan kriteria pengajuan melalui UC03. |
| Pemicu | UC03 mencapai langkah pemeriksaan ketersediaan. |
| Prasyarat | Peralatan, jumlah, dan rentang waktu sudah disampaikan ke sistem. |
| Pascakondisi berhasil | Hasil tersedia dikembalikan kepada UC03; pengajuan belum disimpan oleh UC04. |
| Pascakondisi gagal | Hasil tidak tersedia dikembalikan kepada UC03; pengajuan tidak dinyatakan berhasil. |

**Alur utama:** Sistem memeriksa ketersediaan berdasarkan kriteria dan mengembalikan hasil tersedia. **Alternatif:** Jika alat atau jumlah tidak tersedia pada rentang waktu tersebut, sistem mengembalikan hasil tidak tersedia kepada UC03.

## LAB-UC05 — Cetak Bukti Pengajuan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC05 — Cetak Bukti Pengajuan |
| Sumber kebutuhan | LAB-R04 |
| Tujuan | Menyediakan bukti untuk pengajuan yang telah tersimpan agar dapat dicetak. |
| Aktor utama | Mahasiswa. |
| Aktor pendukung | Sistem menyiapkan bukti pengajuan. |
| Pemicu | Mahasiswa memilih cetak pada konfirmasi pengajuan. |
| Prasyarat | UC03 berhasil dan bukti pengajuan tersedia. |
| Relasi | `extend` UC03 pada extension point Bukti pengajuan tersedia dengan condition [Mahasiswa memilih cetak]. |
| Pascakondisi berhasil | Bukti pengajuan disiapkan untuk dicetak. |
| Pascakondisi tidak dijalankan | Jika Mahasiswa tidak memilih cetak, UC05 tidak dijalankan dan pengajuan tetap berhasil. |

**Alur utama:** Mahasiswa memilih Cetak Bukti Pengajuan; sistem menyiapkan bukti dari pengajuan yang tersimpan. **Alternatif:** Jika Mahasiswa tidak memilih cetak, alur dasar UC03 berakhir sukses tanpa menjalankan UC05.

## LAB-UC06 — Proses Keputusan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC06 — Proses Keputusan Peminjaman |
| Sumber kebutuhan | LAB-R05 |
| Tujuan | Mencatat keputusan Petugas atas pengajuan peminjaman. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem menampilkan pengajuan dan menyimpan keputusan. |
| Pemicu | Petugas memilih pengajuan untuk diproses. |
| Prasyarat | Pengajuan tersedia untuk diproses dan Petugas memiliki hak akses. |
| Pascakondisi berhasil | Keputusan Setujui atau Tolak tercatat. |
| Pascakondisi gagal | Tidak ada keputusan baru yang tercatat. |

**Alur utama:** Petugas memilih pengajuan; sistem menampilkan rincian; Petugas menetapkan Setujui atau Tolak; sistem menyimpan dan menampilkan hasil. **Alternatif:** Jika pengajuan tidak tersedia untuk diproses, sistem menyampaikan bahwa keputusan tidak dapat dicatat. Persetujuan tidak diasumsikan menjadi reservasi teknis stok.

## LAB-UC07 — Lihat Laporan Peminjaman

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC07 — Lihat Laporan Peminjaman |
| Sumber kebutuhan | LAB-R06 |
| Tujuan | Melihat laporan peminjaman yang disediakan sistem. |
| Aktor utama | Kepala Laboratorium. |
| Aktor pendukung | Sistem menyajikan laporan. |
| Pemicu | Kepala Laboratorium memilih Lihat Laporan Peminjaman. |
| Prasyarat | Kepala Laboratorium terautentikasi dan memiliki hak akses sesuai peran. |
| Pascakondisi berhasil | Laporan peminjaman ditampilkan. |
| Pascakondisi gagal | Tidak ada perubahan data; sistem menyampaikan jika laporan belum tersedia. |

**Alur utama:** Kepala Laboratorium meminta laporan; sistem menampilkan laporan peminjaman yang tersedia. **Alternatif:** Jika data laporan belum tersedia, sistem menyampaikan bahwa laporan belum tersedia. Ekspor atau unduh laporan tidak ditambahkan.

## LAB-UC08 — Tambah Data Peralatan (khusus UC02)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC08 — Tambah Data Peralatan |
| Sumber kebutuhan | LAB-R08 |
| Tujuan | Menambahkan data peralatan baru. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem memvalidasi dan menyimpan data. |
| Pemicu | Petugas memilih operasi tambah pada UC02. |
| Prasyarat | Petugas berhak mengelola data peralatan. |
| Generalization | UC08 mewarisi alur umum Kelola Data Peralatan (UC02). |
| Pascakondisi berhasil | Data peralatan baru tersimpan. |
| Pascakondisi gagal | Data peralatan baru tidak tersimpan. |

**Perilaku umum:** Rujuk UC02 untuk pemilihan operasi dan pengelolaan data. **Perilaku pembeda:** Petugas mengisi data peralatan baru; sistem memvalidasi dan menyimpan sebagai data baru. **Alternatif:** Jika data tidak dapat diproses, sistem menolak penambahan dan menyampaikan alasan.

## LAB-UC09 — Ubah Data Peralatan (khusus UC02)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC09 — Ubah Data Peralatan |
| Sumber kebutuhan | LAB-R08 |
| Tujuan | Memperbarui data peralatan yang dipilih. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem memvalidasi dan menyimpan perubahan. |
| Pemicu | Petugas memilih operasi ubah pada UC02. |
| Prasyarat | Petugas berhak mengelola data peralatan; data peralatan yang akan diubah tersedia. |
| Generalization | UC09 mewarisi alur umum Kelola Data Peralatan (UC02). |
| Pascakondisi berhasil | Perubahan data peralatan tersimpan. |
| Pascakondisi gagal | Data lama tetap tersimpan tanpa perubahan. |

**Perilaku umum:** Rujuk UC02 untuk pemilihan operasi dan pengelolaan data. **Perilaku pembeda:** Petugas memilih peralatan dan mengirim data perubahan; sistem menyimpan data peralatan yang diperbarui. **Alternatif:** Jika data perubahan tidak dapat diproses, sistem menolak penyimpanan.

## LAB-UC10 — Hapus Data Peralatan (khusus UC02)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC10 — Hapus Data Peralatan |
| Sumber kebutuhan | LAB-R08 |
| Tujuan | Menghapus data peralatan yang memenuhi syarat. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem memeriksa syarat dan mencatat hasil. |
| Pemicu | Petugas memilih operasi hapus pada UC02. |
| Prasyarat | Petugas berhak mengelola data peralatan; data peralatan terpilih tersedia. |
| Generalization | UC10 mewarisi alur umum Kelola Data Peralatan (UC02). |
| Aturan khusus | Data hanya dapat dihapus jika peralatan tidak sedang dipinjam dan tidak memiliki pengajuan aktif. |
| Pascakondisi berhasil | Data peralatan terhapus. |
| Pascakondisi gagal | Data peralatan tetap ada. |

**Perilaku umum:** Rujuk UC02 untuk pemilihan operasi dan pengelolaan data. **Perilaku pembeda:** Sistem memeriksa aturan hapus; jika kedua syarat terpenuhi, Petugas mengonfirmasi dan sistem menghapus data. **Alternatif:** Jika peralatan sedang dipinjam atau memiliki pengajuan aktif, sistem menolak penghapusan dan menyampaikan alasan.

## LAB-UC11 — Catat Pengembalian Peralatan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC11 — Catat Pengembalian Peralatan |
| Sumber kebutuhan | LAB-R09, LAB-R11 |
| Tujuan | Mencatat pengembalian alat dan memperbarui status peminjaman. |
| Aktor utama | Petugas Laboratorium. |
| Aktor pendukung | Sistem memeriksa status dan menjalankan LAB-UC12. |
| Pemicu | Petugas memilih fungsi pencatatan pengembalian dan memilih peminjaman. |
| Prasyarat | Peminjaman terpilih berstatus Dipinjam. |
| Include | LAB-UC12 Periksa Kondisi Peralatan wajib dilakukan dalam pencatatan pengembalian. |
| Collaboration | LAB-CO02 Catat Pengembalian Peralatan merealisasikan UC11. |
| Pascakondisi berhasil | Pengembalian dan tanggal kembali tercatat; status peminjaman menjadi Selesai; kondisi alat tercatat. |
| Pascakondisi gagal | Tidak ada pengembalian baru tersimpan; status peminjaman tidak berubah. |

**Alur utama:** 1. Petugas memilih peminjaman. 2. Sistem menampilkan data peminjaman dan statusnya. 3. Petugas mengonfirmasi alat dan jumlah yang kembali. 4. Sistem memeriksa status Dipinjam dan kesesuaian jumlah. 5. Sistem menjalankan UC12 untuk memeriksa dan mencatat kondisi. 6. Petugas menyimpan pencatatan. 7. Sistem mencatat tanggal kembali dan kondisi, mengubah status menjadi Selesai, lalu menampilkan konfirmasi.

**Alur alternatif:** Jika status bukan Dipinjam atau jumlah tidak sesuai, sistem menolak penyimpanan dan menampilkan alasan; tidak ada perubahan tercatat. Kondisi Rusak Ringan atau Rusak Berat tetap dicatat dan tidak otomatis menimbulkan denda. Pengembalian fisik alat berlangsung di luar sistem.

## LAB-UC12 — Periksa Kondisi Peralatan

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | LAB-UC12 — Periksa Kondisi Peralatan |
| Sumber kebutuhan | LAB-R10 |
| Tujuan | Mencatat kondisi alat yang dikembalikan sebagai bagian UC11. |
| Aktor utama | Petugas Laboratorium melalui UC11. |
| Aktor pendukung | Sistem menyediakan pilihan dan menyimpan nilai kondisi. |
| Pemicu | UC11 mencapai langkah pemeriksaan kondisi. |
| Prasyarat | Peminjaman berstatus Dipinjam dan alat yang kembali sudah dikonfirmasi. |
| Relasi | `include` oleh LAB-UC11. |
| Nilai kondisi | Baik, Rusak Ringan, atau Rusak Berat. |
| Pascakondisi berhasil | Nilai kondisi tercatat pada data pengembalian. |
| Pascakondisi gagal | Nilai kondisi belum tercatat; pencatatan pengembalian belum disimpan. |

**Alur utama:** Sistem menampilkan pilihan kondisi; Petugas memilih Baik, Rusak Ringan, atau Rusak Berat; sistem mencatat pilihan pada data pengembalian. **Alternatif:** Jika Petugas belum memilih kondisi, sistem meminta nilai kondisi sebelum pengembalian disimpan.
