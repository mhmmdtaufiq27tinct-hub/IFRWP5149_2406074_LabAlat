# Deskripsi use case kumulatif SIA P04

Dokumen ini mencakup SIA-UC01 sampai SIA-UC13 sesuai diagram kumulatif P04. UC01-UC02 meneruskan fungsi P02, UC03-UC06 mempertahankan use case KRS P03, sedangkan UC07-UC13 melengkapi kebutuhan P04. ID, nama, aktor, dan relasi UC03-UC06 tetap selaras dengan deskripsi P03.

## SIA-UC01 — Lihat Jadwal Kuliah

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC01 — Lihat Jadwal Kuliah |
| Sumber kebutuhan | SIA-R01 (P02) |
| Tujuan | Melihat jadwal kuliah yang tersedia. |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi Lihat Jadwal Kuliah. |
| Prasyarat | Mahasiswa terautentikasi; informasi jadwal tersedia di sistem. |
| Alur utama | Mahasiswa meminta jadwal; sistem menampilkan jadwal kuliah yang tersedia. |
| Alternatif/pengecualian | Jika jadwal belum tersedia, sistem menyampaikan informasi tersebut. |
| Pascakondisi | Jadwal ditampilkan; tidak ada perubahan data. |

## SIA-UC02 — Kelola Jadwal Kuliah

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC02 — Kelola Jadwal Kuliah |
| Sumber kebutuhan | SIA-R02 (P02) |
| Tujuan | Mengelola informasi jadwal kuliah. |
| Aktor utama | Admin Akademik |
| Pemicu | Admin Akademik memilih fungsi Kelola Jadwal Kuliah. |
| Prasyarat | Admin Akademik terautentikasi dan memiliki hak akses. |
| Alur utama | Admin Akademik memilih jadwal untuk dikelola, sistem menampilkan informasi jadwal, Admin mengirim pengelolaan, lalu sistem menyimpan dan menampilkan hasil. |
| Alternatif/pengecualian | Jika data tidak dapat diproses, sistem menolak penyimpanan dan menyampaikan alasan. |
| Pascakondisi berhasil | Pengelolaan jadwal tersimpan. |
| Pascakondisi gagal | Data jadwal tidak berubah. |

## SIA-UC03 — Ajukan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC03 — Ajukan KRS |
| Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05 (P03) |
| Tujuan | Menyimpan pengajuan KRS yang lolos validasi untuk menunggu keputusan Dosen Wali. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menjalankan SIA-UC04 Validasi KRS. |
| Pemicu | Mahasiswa memilih Ajukan KRS. |
| Prasyarat | Mahasiswa terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia. |
| Include | SIA-UC04 Validasi KRS selalu dijalankan sebagai bagian pengajuan. |
| Extension point | Bukti pengajuan tersedia setelah KRS berhasil tersimpan. |
| Pascakondisi berhasil | KRS tersimpan dengan status Menunggu persetujuan Dosen Wali. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

**Alur utama:** Mahasiswa memilih mata kuliah dan mengirim pengajuan. Sistem menjalankan UC04. Jika valid, sistem menyimpan KRS dengan status Menunggu persetujuan Dosen Wali dan menampilkan konfirmasi.

**Alternatif:** Jika validasi gagal, sistem menampilkan alasan dan tidak menyimpan pengajuan berhasil. Setelah pengajuan tersimpan, UC05 dijalankan hanya jika [Mahasiswa memilih unduh]; tanpa pilihan unduh, pengajuan tetap berhasil.

## SIA-UC04 — Validasi KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC04 — Validasi KRS |
| Sumber kebutuhan | SIA-R04 (P03) |
| Tujuan | Menentukan apakah pengajuan memenuhi pemeriksaan KRS yang ditetapkan. |
| Aktor utama | Sistem sebagai perilaku yang di-include oleh UC03. |
| Aktor pendukung | Mahasiswa mengirim data pengajuan melalui UC03. |
| Pemicu | UC03 mencapai langkah validasi. |
| Prasyarat | Data pengajuan telah dikirim dan tersedia untuk diperiksa. |
| Alur utama | Sistem memeriksa kelengkapan data, prasyarat mata kuliah, dan benturan jadwal, lalu mengembalikan hasil valid kepada UC03 jika seluruh pemeriksaan lolos. |
| Alternatif/pengecualian | Jika satu atau lebih pemeriksaan gagal, sistem mengembalikan alasan kegagalan kepada UC03. |
| Pascakondisi | Hasil validasi diberikan kepada UC03; UC04 tidak menyimpan pengajuan. |

## SIA-UC05 — Unduh Bukti Pengajuan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC05 — Unduh Bukti Pengajuan KRS |
| Sumber kebutuhan | SIA-R05 (P03) |
| Tujuan | Memperoleh bukti pengajuan KRS yang telah tersimpan. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menyediakan bukti pengajuan. |
| Pemicu | Mahasiswa memilih unduh pada konfirmasi pengajuan. |
| Prasyarat | UC03 berhasil dan bukti pengajuan tersedia. |
| Relasi | `extend` UC03 pada extension point bukti tersedia, dengan kondisi [Mahasiswa memilih unduh]. |
| Alur utama | Mahasiswa memilih Unduh Bukti Pengajuan KRS; sistem menyediakan bukti dari pengajuan yang tersimpan. |
| Alternatif/pengecualian | Jika Mahasiswa tidak memilih unduh, UC05 tidak dijalankan dan pengajuan tetap berhasil. |
| Pascakondisi | Bukti disediakan untuk diunduh; data KRS tidak berubah. |

## SIA-UC06 — Proses Keputusan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC06 — Proses Keputusan KRS |
| Sumber kebutuhan | SIA-R06 (P03) |
| Tujuan | Mencatat persetujuan atau penolakan atas KRS yang menunggu keputusan. |
| Aktor utama | Dosen Wali |
| Aktor pendukung | Sistem menyimpan dan menampilkan keputusan. |
| Pemicu | Dosen Wali memilih pengajuan KRS untuk diproses. |
| Prasyarat | Pengajuan KRS tersimpan dan berstatus menunggu keputusan. |
| Alur utama | Dosen Wali memilih pengajuan; sistem menampilkan rincian; Dosen Wali memilih Setujui atau Tolak dan memasukkan catatan; sistem menyimpan keputusan serta catatan, lalu menampilkan hasil. |
| Alternatif/pengecualian | Jika pengajuan tidak lagi menunggu keputusan, sistem menampilkan status terkini dan tidak menimpa keputusan yang sudah ada. |
| Pascakondisi berhasil | Status keputusan dan catatan Dosen Wali tercatat. |
| Pascakondisi gagal | Tidak ada keputusan baru yang tersimpan. |

## SIA-UC07 — Lihat Kalender Akademik

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC07 — Lihat Kalender Akademik |
| Sumber kebutuhan | SIA-R07 (P04) |
| Tujuan | Melihat informasi kalender akademik institusi. |
| Aktor utama | Civitas Akademika (aktor umum); Mahasiswa dan Dosen mewarisi akses ini. |
| Pemicu | Aktor memilih Lihat Kalender Akademik. |
| Prasyarat | Aktor terautentikasi; informasi kalender tersedia. |
| Alur utama | Aktor meminta kalender akademik; sistem menampilkan informasi kalender yang tersedia. |
| Alternatif/pengecualian | Jika kalender belum tersedia, sistem menyampaikan informasi tersebut. |
| Pascakondisi | Kalender ditampilkan; tidak ada perubahan data. |

## SIA-UC08 — Input Nilai Mata Kuliah

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC08 — Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 (P04) |
| Tujuan | Mencatat nilai mahasiswa untuk mata kuliah yang diampu Dosen. |
| Aktor utama | Dosen |
| Pemicu | Dosen memilih Input Nilai Mata Kuliah. |
| Prasyarat | Dosen mengampu mata kuliah yang dipilih dan masa perkuliahan telah berakhir. |
| Aturan | Nilai harus berada dalam rentang yang sah; penyimpanan nilai tidak otomatis memublikasikannya. |
| Collaboration | SIA-CO01 Input Nilai Mata Kuliah merealisasikan UC08. |
| Alur utama | Dosen memilih mata kuliah dan mahasiswa, memasukkan nilai, lalu mengirim input. Sistem memeriksa rentang dan menyimpan nilai yang sah. |
| Alternatif/pengecualian | Jika Dosen bukan pengampu atau masa perkuliahan belum berakhir, input tidak diproses. Jika nilai di luar rentang sah, sistem menolak nilai dan menampilkan alasan. |
| Pascakondisi berhasil | Nilai yang sah tercatat dan belum otomatis dipublikasikan. |
| Pascakondisi gagal | Nilai tidak tersimpan. |

## SIA-UC09 — Lihat KHS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC09 — Lihat KHS |
| Sumber kebutuhan | SIA-R09 (P04) |
| Tujuan | Melihat Kartu Hasil Studi untuk semester yang dipilih. |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi Lihat KHS dan semester. |
| Prasyarat | Mahasiswa terautentikasi. |
| Aturan | KHS hanya menampilkan nilai yang sudah dipublikasikan. |
| Collaboration | SIA-CO02 Lihat KHS merealisasikan UC09. |
| Alur utama | Mahasiswa memilih semester; sistem menampilkan KHS dengan nilai yang telah dipublikasikan. |
| Alternatif/pengecualian | Jika belum ada nilai yang dipublikasikan untuk semester tersebut, sistem menyampaikan KHS belum tersedia. |
| Pascakondisi | KHS ditampilkan bila tersedia; tidak ada perubahan data. |

## SIA-UC10 — Kelola Data Mahasiswa (use case umum)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC10 — Kelola Data Mahasiswa |
| Sumber kebutuhan | SIA-R10 (P04) |
| Tujuan | Menjadi perilaku umum untuk pengelolaan data mahasiswa. |
| Aktor utama | Admin Akademik |
| Pemicu | Admin Akademik memilih fungsi Kelola Data Mahasiswa. |
| Prasyarat | Admin Akademik terautentikasi dan memiliki hak akses. |
| Generalization | UC11 Tambah, UC12 Ubah, dan UC13 Hapus Data Mahasiswa adalah spesialisasi UC10. |
| Alur umum | Admin memilih operasi dan data terkait; sistem memproses operasi khusus sesuai UC11, UC12, atau UC13 dan menampilkan hasil. |
| Pascakondisi berhasil | Perubahan sesuai operasi khusus tersimpan. |
| Pascakondisi gagal | Data tidak berubah jika operasi ditolak. |

## SIA-UC11 — Tambah Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC11 — Tambah Data Mahasiswa |
| Sumber kebutuhan | SIA-R11 (P04) |
| Tujuan | Menambahkan data mahasiswa baru. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10). |
| Pemicu | Admin memilih operasi tambah pada UC10. |
| Prasyarat | Admin memiliki hak mengelola data mahasiswa. |
| Perilaku khusus | Admin mengisi data mahasiswa baru; sistem memvalidasi dan menyimpan data sebagai catatan baru. |
| Alternatif/pengecualian | Jika data tidak dapat diproses, sistem menolak penambahan dan menyampaikan alasan. |
| Pascakondisi berhasil | Data mahasiswa baru tersimpan. |
| Pascakondisi gagal | Data baru tidak tersimpan. |

## SIA-UC12 — Ubah Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC12 — Ubah Data Mahasiswa |
| Sumber kebutuhan | SIA-R11 (P04) |
| Tujuan | Memperbarui data mahasiswa yang dipilih. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10). |
| Pemicu | Admin memilih operasi ubah pada UC10. |
| Prasyarat | Admin memiliki hak akses dan data mahasiswa yang dipilih tersedia. |
| Perilaku khusus | Admin mengirim perubahan; sistem memvalidasi dan menyimpan data yang diperbarui. |
| Alternatif/pengecualian | Jika data perubahan tidak dapat diproses, sistem menolak penyimpanan. |
| Pascakondisi berhasil | Perubahan data mahasiswa tersimpan. |
| Pascakondisi gagal | Data lama tetap tersimpan tanpa perubahan. |

## SIA-UC13 — Hapus Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC13 — Hapus Data Mahasiswa |
| Sumber kebutuhan | SIA-R11 (P04) |
| Tujuan | Menghapus data mahasiswa yang memenuhi syarat. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10). |
| Pemicu | Admin memilih operasi hapus pada UC10. |
| Prasyarat | Admin memiliki hak akses dan data mahasiswa yang dipilih tersedia. |
| Aturan khusus | Data hanya dapat dihapus jika tidak memiliki data akademik aktif. |
| Perilaku khusus | Sistem memeriksa aturan penghapusan; jika terpenuhi, penghapusan diproses dan hasil ditampilkan. |
| Alternatif/pengecualian | Jika masih ada data akademik aktif, sistem menolak penghapusan dan menyampaikan alasan. |
| Pascakondisi berhasil | Data mahasiswa terhapus. |
| Pascakondisi gagal | Data mahasiswa tetap ada. |
