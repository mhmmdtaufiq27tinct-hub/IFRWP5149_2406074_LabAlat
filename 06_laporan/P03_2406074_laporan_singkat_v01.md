# Laporan Singkat Pertemuan 3

**Nama:** Muhammad Taufiq  
**NIM:** 2406074  
**Kelas:** C

## Ringkasan

Pertemuan 3 menyusun diagram use case dan deskripsi use case untuk LAB dan SIA. LAB mempertahankan fungsi P02 dan menambahkan pengajuan, validasi ketersediaan, keputusan, serta bukti opsional. Diagram SIA P03 berfokus pada pengajuan KRS; fungsi jadwal P02 tidak disalin ke diagram ini dan kembali dimasukkan dalam model kumulatif P04.

## Artefak

| Kasus | Artefak utama | Cakupan |
|:--|:--|:--|
| LAB | `03_latihan_tools/P03/LAB/` | Deskripsi lengkap untuk LAB-UC01–LAB-UC07 sesuai diagram P03. |
| SIA | `03_latihan_tools/P03/SIA/` dan `04_model_analisis/P03/SIA/` | Deskripsi dan diagram P03 untuk SIA-UC03–SIA-UC06; use case jadwal P02 tidak disalin ke diagram ini. |

## Catatan konsistensi

Pada SIA, P03 berfokus pada kebutuhan KRS SIA-R03–SIA-R06 dan tidak menambahkan UC01/UC02 atau Admin Akademik dari P02 ke diagramnya. UC03 meng-include UC04 Validasi KRS; UC05 Unduh Bukti Pengajuan KRS meng-extend UC03 jika dipilih setelah pengajuan tersimpan. KRS yang tersimpan berstatus menunggu keputusan. P04 menggabungkan kembali use case jadwal dari P02 ke model kumulatif.

Pada LAB, periksa ketersediaan menjadi bagian wajib dari pengajuan. Cetak bukti hanya berjalan jika mahasiswa memilihnya setelah konfirmasi. Pengajuan yang berhasil berstatus Menunggu keputusan.

## Pemeriksaan

Nama aktor, ID use case, relasi include/extend, kondisi extend, dan alur deskripsi diselaraskan dengan skenario masing-masing. Sumber diagram dapat diedit dalam format draw.io. Ekspor PNG dipertahankan sebagai pratinjau.
