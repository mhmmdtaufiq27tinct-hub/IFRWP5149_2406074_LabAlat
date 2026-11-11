# Laporan Singkat Pertemuan 6

**Nama:** Muhammad Taufiq  
**NIM:** 2406074  
**Kelas:** C

## Ringkasan

Skenario LAB Pertemuan 5 diterjemahkan menjadi activity diagram dengan swimlane aktor dan Sistem. Berkas sumber draw.io tersedia di `03_latihan_tools/P06/LAB/` untuk peminjaman, pengembalian, keputusan, ketersediaan, pengelolaan data, laporan, dan cetak bukti.

## Aturan pemodelan

Setiap diagram memiliki satu initial node dan sekurangnya satu activity final. Decision memakai guard yang mencakup semua kemungkinan dan cabangnya berakhir jelas. Perilaku include digambar sebagai action wajib. Extend cetak bukti hanya muncul pada cabang [ya, memilih cetak]. Action ditempatkan pada swimlane pelakunya; respons berada di swimlane Sistem.

## Pemeriksaan

Nama action ditelusurkan ke skenario P05. Pemeriksaan kondisi peralatan pada pengembalian adalah unsur tambahan yang diwajibkan P06 dan tidak diklaim berasal dari P03–P05. Collaboration adalah struktur pemodelan, bukan action atau swimlane.
