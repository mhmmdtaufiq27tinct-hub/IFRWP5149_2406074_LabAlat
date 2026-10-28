#### Skenario berikut merupakan bahan latihan yang ditetapkan untuk jobsheet, bukan hasil pengumpulan kebutuhan laboratorium nyata.
#### Skenario ini melanjutkan potongan model Pertemuan 3.
#### Selain mahasiswa, dosen juga meminjam peralatan laboratorium untuk kegiatan praktikum dan penelitian.
#### Mahasiswa dan dosen sama-sama dapat melihat ketersediaan peralatan dan mengajukan peminjaman.
#### Petugas laboratorium mengelola data peralatan: menambah peralatan baru, mengubah data peralatan, dan menghapus data peralatan yang tidak lagi dipakai.
#### Setelah peminjaman disetujui dan alat diambil, petugas mencatat pengembalian peralatan. Pada saat mencatat pengembalian, petugas memeriksa dan mencatat kondisi peralatan.
#### Dua use case utama pada potongan model ini, Ajukan Peminjaman dan Catat Pengembalian Peralatan, ditunjukkan realisasinya oleh collaboration yang bersesuaian.
#### Seluruh fungsi Pertemuan 3 tetap berlaku dan tetap digambar: pemeriksaan ketersediaan di dalam pengajuan, pencetakan bukti pengajuan oleh mahasiswa, proses keputusan peminjaman oleh petugas, dan laporan peminjaman untuk kepala laboratorium.
#### Diagram Pertemuan 4 adalah diagram Pertemuan 3 yang ditambah, bukan diagram baru yang menggantikannya.

## Batas sistem dan aturan
* Sistem mencatat dan menyediakan informasi; perpindahan fisik alat tidak terjadi di dalam perangkat lunak (tetap dari Pertemuan 3).
* Pengguna telah terautentikasi dan memiliki hak akses sesuai peran (tetap dari Pertemuan 3).
* Pengembalian hanya dapat dicatat untuk peminjaman berstatus Dipinjam. Peminjaman yang masih Menunggu Keputusan atau Ditolak tidak dapat dicatat pengembaliannya.
* Kondisi peralatan pada pengembalian dicatat dengan salah satu nilai: Baik, Rusak Ringan, atau Rusak Berat.
* Hapus Data Peralatan hanya untuk peralatan yang tidak sedang dipinjam dan tidak memiliki pengajuan aktif.
* Keterlambatan dan denda belum dimodelkan pada pertemuan ini. Tuliskan sebagai pertanyaan terbuka pada berkas kebutuhan, jangan mengarang aturan denda.
* Kriteria penerimaan model: semua kebutuhan LAB-R01 sampai LAB-R11 mempunyai representasi pada diagram kumulatif, arah generalization dan realization benar, dan diagram konsisten dengan deskripsinya.

## Tentukan Aktor
| Aktor | Kedudukan | Tujuan terhadap sistem |
|:---:|:---|:---|
| Peminjam | Umum (general), baru pada Pertemuan 4 | Peran umum bagi peminjam peralatan. Mewariskan fungsinya kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Peminjam, tetap dari Pertemuan 3 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri. |
| Dosen | Khusus dari Peminjam, baru pada Pertemuan 4 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam). |
| Petugas | Laboratorium Tetap dari Pertemuan 3 | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat engembalian peralatan. |
| Kepala Laboratorium | Tetap dari Pertemuan 3 | Melihat laporan peminjaman. |

## Susun Katalog Usecase
| ID | Nama use case | Peran dalam model | Sumber Kebutuhan |
|:---:|:---|:---|:---|
| LAB-UC01 | Lihat ketersediaan peralatan | Fungsi utama mahasiswa | LAB-R01, LABR07 |
| LAB-UC02 | Kelola data peralatan | Fungsi utama petugas | LAB-R02, LABR08 |
| LAB-UC03 | Ajukan peminjaman | Fungsi utama mahasiswa | LAB-R03, LABR07 |
| LAB-UC04 | Periksa ketersediaan | Perilaku yang disertakan UC03 | LAB-R03 |
| LAB-UC05 | Cetak bukti pengajuan | Tambahan bersyarat pada UC03 | LAB-R04 |
| LAB-UC06 | Proses keputusan peminjaman | Fungsi utama petugas | LAB-R05 |
| LAB-UC07 | Lihat laporan peminjaman | Fungsi utama kepala laboratorium | LAB-R06 |
| LAB-UC08 | Tambah Data Peralatan | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC09 | Ubah Data Peralatan | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC10 | Hapus Data Peralatan | Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-UC02 | LAB-R09 |
| LAB-UC12 | Periksa Kondisi Peralatan | Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC11 | LAB-R10 |

## Tetapkan generalization aktor
* Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah bentuk khusus dari Peminjam. Alasan: keduanya berbagi fungsi yang sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman.
* Asosiasi ke LAB-UC01 dan LAB-UC03 digambar satu kali, yaitu dari Peminjam. Jangan menggambar garis yang sama dari Mahasiswa dan dari Dosen.
* Asosiasi Mahasiswa ke LAB-UC05 Cetak Bukti Pengajuan tidak ikut dipindahkan dan tidak dihapus, karena fungsi itu khusus mahasiswa. Asosiasi ini menjadi contoh asosiasi tambahan milik aktor khusus.
* Periksa arah panah pada gambar: ujung segitiga kosong harus menempel pada Peminjam, bukan pada Mahasiswa dan bukan pada Dosen. Karena Peminjam digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas; keduanya berakhir pada Peminjam.

## Perbandingan diagram Pertemuan 3 dan diagram Pertemuan 4
| Kelompok | Isi |
|:---:|:---|
| Tetap sama dari Pertemuan 3 | Aktor Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium; use case LAB-UC01 sampai LAB-UC07; relasi «include» LAB-UC03 ke LAB-UC04; relasi «extend» LABUC05 ke LAB-UC03 lengkap dengan condition [mahasiswa memilih cetak] dan extension point Bukti pengajuan tersedia; asosiasi Petugas Laboratorium ke LAB-UC02 dan LAB-UC06; asosiasi Kepala Laboratorium ke LAB-UC07; asosiasi Mahasiswa ke LAB-UC05. |
| Berubah karena generalization aktor | Asosiasi ke LAB-UC01 dan LAB-UC03 yang pada Pertemuan 3 digambar dari Mahasiswa kini digambar satu kali dari Peminjam. Fungsi mahasiswa tidak hilang: mahasiswa mewarisinya dari Peminjam. Inilah satu-satunya perubahan garis pada diagram lama, dan alasannya adalah aturan generalization, bukan penghapusan fungsi. |
| Ditambah pada Pertemuan 4 | Aktor Peminjam dan Dosen; dua generalization aktor; usecase LAB-UC08, LAB-UC09, LAB-UC10 beserta tiga generalization use case ke LAB-UC02; use case LAB-UC11 dan LAB-UC12 beserta relasi «include» di antara keduanya dan asosiasi Petugas Laboratorium ke LAB-UC11; collaboration LAB-CO01 dan LAB-CO02 beserta dua relasi realization. |

## Tetapkan generalization use case
* LAB-UC08, LAB-UC09, dan LAB-UC10 adalah bentuk khusus dari LABUC02 Kelola Data Peralatan. Alasan: ketiganya adalah bentuk khusus pengelolaan data peralatan.
* Tuliskan untuk setiap use case khusus satu kalimat perilaku pembedanya. Tambah menghasilkan data peralatan baru. Ubah menghasilkan data peralatan yang berubah. Hapus menghasilkan data peralatan yang terhapus dengan syarat pada aturan studi kasus.

## Tetapkan collaboration dan realization
| ID | Nama collaboration (sama dengan nama use case) | Use case yang direalisasikan |
|:---:|:---|:---|
| LAB-CO01 | Ajukan Peminjaman | LAB-UC03: Ajukan Peminjaman |
| LAB-CO02 | Catat Pengembalian Peralatan | LAB-UC11: Catat Pengembalian Peralatan |

## Alur utama
| Langkah | Tindakan petugas | Respons sistem |
|:---:|:---|:---|
| 1 | Memilih peminjaman yang akan dikembalikan | Menampilkan data peminjaman terpilih dan statusnya |
| 2 | Mengonfirmasi alat yang kembali dan jumlahnya | Menampung konfirmasi petugas |
| 3 | Tidak ada Memeriksa status peminjaman harus Dipinjam |
| 4 | Tidak ada Menjalankan LAB-UC12: memeriksa dan mencatat kondisi peralatan |
| 5 | Menyimpan pencatatan pengembalian | Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi Selesai |
| 6 | Melihat konfirmasi | Menampilkan ringkasan pengembalian |

## Alur alternatif atau pengecualian
* A1: Status bukan Dipinjam (pada langkah 3): sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku; tidak ada data yang disimpan.
* A2: Kondisi Rusak Ringan atau Rusak Berat (pada langkah 4): sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan, dan pengembalian tetap tercatat. Kerusakan tidak otomatis menimbulkan denda pada model ini.
* A3: Jumlah alat yang kembali tidak sesuai (pada langkah 2): sistem meminta petugas memeriksa kembali isian sebelum penyimpanan; pencatatan tidak disimpan sampai jumlah sesuai atau dikoreksi.
