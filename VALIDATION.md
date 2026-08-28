# UX + Formula Validation — Kalkulatur v1.3

## Referensi workbook
Workbook `Kalkulator PPN DPP PPH23.xlsx` menggunakan formula:
- Harga Barang = 100/111 × Harga Jual
- DPP = Harga Barang × 11/12
- PPN = Harga Barang × 11%
- PPh23 = Harga Barang × 2%
- Jumlah Bersih = Harga Jual − PPN − PPh23

Nilai tersimpan di workbook untuk contoh:
- Harga Jual Rp4.500.000 → Harga Barang 4.054.054,054054054; DPP 3.716.216,216216216; PPN 445.945,945945946; PPh23 81.081,081081081; Jumlah Bersih 3.972.972,972972973.
- Harga Jual Rp5.250.000 → Harga Barang 4.729.729,729729730; DPP 4.335.585,585585586; PPN 520.270,270270270; PPh23 94.594,594594595; Jumlah Bersih 4.635.135,135135135.

## Skenario yang diuji
Semua angka ditampilkan dibulatkan ke rupiah; perhitungan internal menggunakan desimal.

| ID | Skenario | Hasil utama | Status |
|---|---|---|---|
| S1 | Inclusive Rp4.500.000, PPh23 ON | Barang 4.054.054; DPP 3.716.216; PPN 445.946; PPh23 81.081; Net 3.972.973 | PASS — sama dengan workbook |
| S2 | Inclusive Rp5.250.000, PPh23 ON | Barang 4.729.730; DPP 4.335.586; PPN 520.270; PPh23 94.595; Net 4.635.135 | PASS — sama dengan workbook |
| S3 | Inclusive Rp10.000.000, PPh23 OFF | Barang 9.009.009; DPP 8.258.258; PPN 990.991; PPh23 0; Net 9.009.009 | PASS |
| S4 | Exclusive Rp5.250.000, PPh23 ON | Barang 5.250.000; DPP 4.812.500; PPN 577.500; PPh23 105.000; Net 5.722.500 | PASS — sesuai formula exclusive aplikasi |
| S5 | Exclusive Rp5.250.000, PPh23 OFF | Barang 5.250.000; DPP 4.812.500; PPN 577.500; PPh23 0; Net 5.827.500 | PASS |
| S6 | 3 item: 4,5 jt inclusive/on + 5,25 jt inclusive/off + 3 jt exclusive/on | Total Barang 11.783.784; DPP 10.801.802; PPN 1.296.216; PPh23 141.081; Net 11.972.703 | PASS |
| S7 | Exclusive Rp10.000.000, PPh23 OFF | Barang 10.000.000; DPP 9.166.667; PPN 1.100.000; PPh23 0; Net 11.100.000 | PASS |
| S8 | 2 item: 8 jt inclusive/on + 2 jt exclusive/on | Total Barang 9.207.207; DPP 8.439.940; PPN 1.012.793; PPh23 184.144; Net 9.243.063 | PASS |

## UX validation
- Mode harga jelas: `Sudah termasuk PPN` vs `Belum termasuk PPN`.
- Opsi `Hitung PPh23 2%` tersedia sehingga user tidak dipaksa mengurangi PPh23 pada transaksi yang tidak dikenai/dipotong.
- Istilah hasil dapat dibuka melalui `Arti istilah` tanpa memenuhi layar utama.
- Label PPN tetap `PPN 12%` sesuai keputusan UI produk, tetapi penjelasan transparan bahwa formula workbook memakai `Harga Barang × 11%`.
- Hasil mobile berbentuk kartu dan desktop berbentuk tabel.
- Copy/share/CSV/PDF mempertahankan mode harga dan status PPh23.

## Catatan penting
Mode `Sudah termasuk PPN` adalah replika formula workbook.
Mode `Belum termasuk PPN` adalah formula aplikasi yang sebelumnya disepakati untuk kebutuhan produk; mode ini tidak terdapat sebagai formula terpisah di workbook asli.

Dokumen ini adalah validasi implementasi produk, bukan opini atau nasihat perpajakan. Validitas perlakuan pajak aktual tetap perlu dikonfirmasi dengan ketentuan perpajakan yang berlaku dan konteks transaksi.
