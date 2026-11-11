# Spesifikasi hubungan diagram use case SIA Pertemuan 3

| Sumber | Hubungan | Tujuan |
|:--|:--|:--|
| Mahasiswa | Asosiasi | SIA-UC01 Lihat Jadwal Kuliah |
| Mahasiswa | Asosiasi | SIA-UC02 Ajukan KRS |
| Mahasiswa | Asosiasi | SIA-UC04 Unduh Bukti Pengajuan |
| Admin Akademik | Asosiasi | SIA-UC06 Kelola Jadwal Kuliah |
| Dosen Wali | Asosiasi | SIA-UC05 Proses Persetujuan atau Penolakan KRS |
| SIA-UC02 Ajukan KRS | «include» | SIA-UC03 Validasi KRS |
| SIA-UC04 Unduh Bukti Pengajuan | «extend» [mahasiswa memilih unduh] | SIA-UC02 Ajukan KRS; extension point: bukti tersedia setelah tersimpan |

Lihat jadwal dan kelola jadwal adalah fungsi mandiri sesuai SIA-R01 dan SIA-R02. Keduanya tidak bergantung pada persetujuan KRS. Persetujuan/penolakan adalah fungsi dosen wali yang dipicu oleh pengajuan tersimpan, bukan relasi extend terhadap dirinya sendiri.
