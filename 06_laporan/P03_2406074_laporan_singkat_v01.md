# Laporan Singkat Pertemuan 3

**Nama:** Muhammad Taufiq  
**NIM:** 2406074  
**Kelas:** C

## Ringkasan

Pertemuan 3 menyusun diagram use case dan deskripsi use case untuk dua studi kasus: Sistem Peminjaman Peralatan Laboratorium (LAB) dan Sistem Informasi Akademik (SIA). Diagram kumulatif mempertahankan fungsi Pertemuan 2 dan menambahkan pengajuan, validasi, keputusan, dan perilaku bukti bersyarat.

## Artefak

| Kasus | Artefak utama | Cakupan |
|:--|:--|:--|
| LAB | `03_latihan_tools/P03/LAB/` | Use case melihat ketersediaan, mengelola peralatan, mengajukan peminjaman, memeriksa ketersediaan, mencetak bukti, memproses keputusan, dan melihat laporan. |
| SIA | `03_latihan_tools/P03/SIA/` | Use case jadwal kuliah, pengajuan KRS, validasi, unduh bukti, keputusan dosen wali, dan pengelolaan jadwal. |

## Catatan konsistensi

Pada SIA, UC01 melihat jadwal dan UC06 mengelola jadwal adalah fungsi mandiri, bukan ekstensi dari persetujuan KRS. Validasi KRS menjadi perilaku wajib dalam pengajuan; unduh bukti menjadi perilaku pilihan setelah pengajuan tersimpan. KRS yang tersimpan berstatus menunggu keputusan.

Pada LAB, periksa ketersediaan menjadi bagian wajib dari pengajuan. Cetak bukti hanya berjalan jika mahasiswa memilihnya setelah konfirmasi. Pengajuan yang berhasil berstatus Menunggu keputusan.

## Pemeriksaan

Nama aktor, ID use case, relasi include/extend, kondisi extend, dan alur deskripsi diselaraskan dengan skenario masing-masing. Sumber diagram dapat diedit dalam format draw.io. Ekspor PNG dipertahankan sebagai pratinjau.
