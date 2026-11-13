# Model analisis use case SIA P03

## Batas model

Diagram P03 berfokus pada kebutuhan KRS SIA-R03–SIA-R06. Fungsi jadwal dan aktor Admin Akademik dari P02 tidak ditambahkan ke diagram P03; keduanya kembali dicantumkan pada diagram kumulatif P04.

## Aktor

| Aktor | Interaksi |
|:--|:--|
| Mahasiswa | SIA-UC03 Ajukan KRS; SIA-UC05 Unduh Bukti Pengajuan KRS. |
| Dosen Wali | SIA-UC06 Proses Keputusan KRS. |

## Katalog use case

| ID | Nama |
|:--|:--|
| SIA-UC03 | Ajukan KRS |
| SIA-UC04 | Validasi KRS |
| SIA-UC05 | Unduh Bukti Pengajuan KRS |
| SIA-UC06 | Proses Keputusan KRS |

## Hubungan diagram

| Sumber | Hubungan | Tujuan |
|:--|:--|:--|
| Mahasiswa | Asosiasi | SIA-UC03 Ajukan KRS |
| Mahasiswa | Asosiasi | SIA-UC05 Unduh Bukti Pengajuan KRS |
| Dosen Wali | Asosiasi | SIA-UC06 Proses Keputusan KRS |
| SIA-UC03 Ajukan KRS | `include` | SIA-UC04 Validasi KRS |
| SIA-UC05 Unduh Bukti Pengajuan KRS | `extend` [mahasiswa memilih unduh] | SIA-UC03 Ajukan KRS; extension point: bukti tersedia setelah pengajuan tersimpan |

Pengajuan berhasil tetap utuh tanpa unduh bukti. SIA-UC01 Lihat Jadwal Kuliah dan SIA-UC02 Kelola Jadwal Kuliah bukan bagian diagram P03; keduanya merupakan fungsi P02 dan dimasukkan kembali ke model kumulatif P04.
