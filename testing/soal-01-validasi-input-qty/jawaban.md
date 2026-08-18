VALIDASI INPUT QTY TRANSAKSI

Kolom Qty seharusnya hanya menerima angka bulat positif, minimal satu, tidak boleh nol, tidak boleh negatif, dan tidak boleh melebihi stok yang tersedia. Berikut skenario tes yang mencakup kondisi normal maupun kondisi tidak wajar.

| No. | Skenario Pengujian | Input | Hasil yang Diharapkan |
| --- | --- | --- | --- |
| 1 | Qty angka bulat positif, kondisi normal | 1 | Diterima, transaksi bisa dilanjutkan |
| 2 | Qty bernilai nol | 0 | Ditolak, muncul pesan qty minimal satu |
| 3 | Qty bernilai negatif | -5 | Ditolak, muncul pesan qty tidak boleh negatif |
| 4 | Qty berupa huruf | abc | Ditolak, atau huruf memang tidak bisa diketik di kolom itu |
| 5 | Qty berupa angka desimal | 2.5 | Ditolak, muncul pesan qty harus bilangan bulat |
| 6 | Qty melebihi stok yang tersedia | 15, dengan stok tersedia 10 | Ditolak, muncul pesan stok tidak mencukupi |
| 7 | Qty persis sama dengan stok yang tersedia | 10, dengan stok tersedia 10 | Diterima, karena masih dalam batas stok |
| 8 | Kolom qty dikosongkan | kosong | Ditolak, tidak bisa disubmit, atau muncul pesan wajib diisi |

Skenario nomor satu dan tujuh mewakili kondisi normal yang seharusnya diterima sistem, sedangkan skenario lainnya mewakili kondisi tidak wajar yang tetap harus ditangani dengan baik oleh sistem, bukan malah menyebabkan error atau tersimpannya data yang salah.
