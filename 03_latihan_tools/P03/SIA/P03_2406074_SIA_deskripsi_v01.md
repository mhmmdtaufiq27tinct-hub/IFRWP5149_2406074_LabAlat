# Deskripsi use case SIA P03

Deskripsi ini mencakup seluruh use case SIA-UC03–SIA-UC06 dalam diagram P03. SIA-UC01 Lihat Jadwal Kuliah dan SIA-UC02 Kelola Jadwal Kuliah adalah fungsi P02 dan tidak menjadi aktor/use case pada diagram tugas P03.

## SIA-UC03 — Ajukan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC03 — Ajukan KRS |
| Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05 |
| Tujuan | Menyimpan pengajuan KRS yang lolos validasi untuk menunggu keputusan Dosen Wali. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menjalankan SIA-UC04 Validasi KRS. |
| Pemicu | Mahasiswa memilih Ajukan KRS. |
| Prasyarat | Mahasiswa terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia. |
| Include | SIA-UC04 Validasi KRS selalu dijalankan sebagai bagian pengajuan. |
| Extension point | Bukti pengajuan tersedia setelah KRS berhasil tersimpan. |
| Pascakondisi berhasil | KRS tersimpan dengan status Menunggu persetujuan Dosen Wali. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

**Alur utama:** 1. Mahasiswa memilih mata kuliah. 2. Mahasiswa mengirim pengajuan. 3. Sistem menjalankan SIA-UC04. 4. Jika valid, sistem menyimpan KRS dengan status menunggu persetujuan dan menampilkan konfirmasi. **Alur alternatif:** Pada langkah 3, jika validasi gagal, sistem menampilkan alasan dan tidak menyimpan pengajuan berhasil. Setelah langkah 4, SIA-UC05 dijalankan hanya pada condition [mahasiswa memilih unduh]; tanpa unduhan, pengajuan tetap berhasil.

## SIA-UC04 — Validasi KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC04 — Validasi KRS |
| Sumber kebutuhan | SIA-R04 |
| Tujuan | Menentukan apakah pengajuan memenuhi pemeriksaan KRS yang ditetapkan. |
| Aktor utama | Sistem (perilaku yang di-include oleh SIA-UC03). |
| Aktor pendukung | Mahasiswa mengirimkan data pengajuan melalui SIA-UC03. |
| Pemicu | SIA-UC03 mencapai langkah validasi. |
| Prasyarat | Data pengajuan telah dikirim dan tersedia untuk diperiksa. |
| Pascakondisi berhasil | Hasil valid diberikan kepada SIA-UC03; use case ini tidak menyimpan pengajuan. |
| Pascakondisi gagal | Alasan validasi gagal diberikan kepada SIA-UC03; pengajuan tidak dinyatakan berhasil. |

**Alur utama:** Sistem memeriksa kelengkapan data, prasyarat mata kuliah, dan benturan jadwal; jika seluruh pemeriksaan lolos, sistem mengembalikan hasil valid. **Alur alternatif:** Jika satu atau lebih pemeriksaan gagal, sistem mengembalikan alasan kegagalan kepada SIA-UC03.

## SIA-UC05 — Unduh Bukti Pengajuan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC05 — Unduh Bukti Pengajuan KRS |
| Sumber kebutuhan | SIA-R05 |
| Tujuan | Memperoleh bukti pengajuan KRS yang telah tersimpan. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menyediakan bukti pengajuan. |
| Pemicu | Mahasiswa memilih unduh pada konfirmasi pengajuan. |
| Prasyarat | SIA-UC03 berhasil; bukti pengajuan tersedia. |
| Relasi | `extend` SIA-UC03 pada extension point bukti tersedia, dengan condition [mahasiswa memilih unduh]. |
| Pascakondisi berhasil | Bukti pengajuan disediakan untuk diunduh. |
| Pascakondisi tidak dijalankan | Jika Mahasiswa tidak memilih unduh, SIA-UC05 tidak dijalankan dan keberhasilan SIA-UC03 tidak berubah. |

**Alur utama:** Mahasiswa memilih Unduh Bukti Pengajuan KRS; sistem menyediakan bukti dari pengajuan yang tersimpan. **Alur alternatif:** Condition extend tidak terpenuhi jika Mahasiswa tidak memilih unduh; tidak ada unduhan dan pengajuan tetap berhasil.

## SIA-UC06 — Proses Keputusan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC06 — Proses Keputusan KRS |
| Sumber kebutuhan | SIA-R06 |
| Tujuan | Mencatat persetujuan atau penolakan atas KRS yang menunggu keputusan. |
| Aktor utama | Dosen Wali |
| Aktor pendukung | Sistem menyimpan dan menampilkan keputusan. |
| Pemicu | Dosen Wali memilih pengajuan KRS untuk diproses. |
| Prasyarat | Pengajuan KRS tersimpan dan berstatus menunggu keputusan. |
| Pascakondisi berhasil | Status keputusan dan catatan Dosen Wali tercatat sebagai disetujui atau ditolak. |
| Pascakondisi gagal | Tidak ada keputusan baru yang tersimpan. |

**Alur utama:** 1. Dosen Wali memilih pengajuan. 2. Sistem menampilkan rincian KRS. 3. Dosen Wali memilih Setujui atau Tolak. 4. Dosen Wali memasukkan catatan keputusan. 5. Sistem menyimpan keputusan dan catatan. 6. Sistem menampilkan hasil keputusan. **Alur alternatif:** Jika pengajuan tidak lagi menunggu keputusan, sistem menampilkan status terkini dan tidak menimpa keputusan yang sudah ada.
