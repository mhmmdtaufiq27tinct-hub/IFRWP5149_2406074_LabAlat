# Telaah skenario LAB Pertemuan 5

## Tujuan

Meninjau skenario tekstual dan alur utama/alternatif untuk use case pada model kumulatif LAB. Dokumen ini tidak menambahkan kebutuhan baru.

## LAB-UC03 Ajukan Peminjaman

**Aktor utama:** Peminjam (Mahasiswa atau Dosen)  
**Pemicu:** Peminjam memilih Ajukan Peminjaman.  
**Prasyarat:** Pengguna terautentikasi; data peralatan tersedia.

| Langkah | Kegiatan peminjam | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih peralatan, jumlah, serta rentang waktu | Menampilkan form pengajuan |
| 2 | Mengirim pengajuan | Memeriksa kelengkapan data |
| 3 | — | Menjalankan LAB-UC04 Periksa Ketersediaan |
| 4 | — | Jika tersedia, menyimpan pengajuan berstatus Menunggu keputusan dan menghasilkan nomor pengajuan |
| 5 | Melihat konfirmasi | Menampilkan ringkasan pengajuan dan titik ekstensi bukti tersedia |
| 6 | Memilih cetak bila diinginkan | Menjalankan LAB-UC05 Cetak Bukti Pengajuan hanya pada [mahasiswa memilih cetak] |

**Alternatif:** A1 data tidak lengkap: tampilkan kesalahan, jangan simpan; A2 peralatan tidak tersedia: sampaikan hasil, jangan simpan sebagai pengajuan berhasil; A3 tidak memilih cetak: pengajuan tetap berhasil.  
**Pascakondisi berhasil:** Pengajuan berstatus Menunggu keputusan. **Pascakondisi gagal:** Tidak ada pengajuan baru yang berhasil tersimpan.

## LAB-UC11 Catat Pengembalian Peralatan

**Aktor utama:** Petugas Laboratorium. **Prasyarat:** Peminjaman berstatus Dipinjam.

| Langkah | Kegiatan petugas | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih peminjaman | Menampilkan rincian peminjaman |
| 2 | Mengonfirmasi alat dan jumlah kembali | Memvalidasi jumlah terhadap catatan pinjam |
| 3 | — | Memastikan status Dipinjam |
| 4 | Memeriksa kondisi alat | Menjalankan LAB-UC12 dan mencatat Baik/Rusak Ringan/Rusak Berat |
| 5 | Menyimpan pengembalian | Mencatat tanggal kembali dan mengubah status menjadi Selesai |
| 6 | Melihat konfirmasi | Menampilkan ringkasan pengembalian |

**Alternatif:** Status bukan Dipinjam atau jumlah tidak sesuai: tolak penyimpanan dan tampilkan alasan. Kondisi rusak tetap dicatat; denda tidak disimpulkan. **Pascakondisi berhasil:** Pengembalian tercatat. **Pascakondisi gagal:** Tidak ada perubahan tersimpan.
