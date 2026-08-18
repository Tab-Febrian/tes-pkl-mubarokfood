PERHITUNGAN DISKON BERJENJANG

Total belanja pada kasus ini adalah Rp 480.000, dan pembeli juga menggunakan satu voucher potongan senilai Rp 30.000. Kalau dilihat hanya dari nominal belanjanya saja, transaksi ini sebenarnya masuk ke tier diskon berjenjang 10 persen, karena berada di rentang Rp 300.000 sampai Rp 499.999. Namun aturan toko menyatakan bahwa diskon berjenjang tidak berlaku apabila pembeli menggunakan voucher terpisah, sehingga sistem harus menentukan dulu jalur mana yang dipakai.

Urutan pengecekannya sebagai berikut. Pertama, sistem menghitung total belanja, yaitu Rp 480.000. Kedua, sistem memeriksa apakah transaksi ini menggunakan voucher atau tidak. Apabila tidak menggunakan voucher, sistem akan melanjutkan ke pengecekan tier diskon berjenjang, dan karena nominalnya masuk rentang 300 ribu sampai 499 ribu, pembeli akan mendapat diskon 10 persen, sehingga totalnya menjadi 480.000 dikurangi 48.000 sama dengan Rp 432.000. Namun apabila transaksi menggunakan voucher, sistem akan langsung memakai potongan dari voucher tersebut dan mengabaikan perhitungan diskon berjenjang sama sekali, sehingga totalnya menjadi 480.000 dikurangi 30.000 sama dengan Rp 450.000.

Karena pada kasus ini pembeli menggunakan voucher senilai Rp 30.000, maka jalur yang berlaku adalah jalur kedua. Dengan demikian, total akhir yang harus dibayar pembeli adalah Rp 450.000.

Berikut pseudocode yang menggambarkan logika perhitungannya.

    function hitungTotalBayar(totalBelanja, pakaiVoucher, nilaiVoucher):
        jika pakaiVoucher sama dengan benar:
            totalAkhir = totalBelanja dikurangi nilaiVoucher
        jika tidak:
            jika totalBelanja kurang dari 100000:
                diskon = 0
            atau jika totalBelanja sampai 299999:
                diskon = 5 persen dikali totalBelanja
            atau jika totalBelanja sampai 499999:
                diskon = 10 persen dikali totalBelanja
            jika tidak:
                diskon = 15 persen dikali totalBelanja
            totalAkhir = totalBelanja dikurangi diskon
        kembalikan totalAkhir

    contoh kasus:
    hitungTotalBayar(totalBelanja=480000, pakaiVoucher=true, nilaiVoucher=30000)
    hasilnya totalAkhir = 480000 dikurangi 30000 sama dengan 450000

Sebagai perbandingan saja, apabila pembeli itu tidak menggunakan voucher, diskon 10 persen akan berlaku dan totalnya menjadi Rp 432.000. Namun karena pembeli tersebut menggunakan voucher, yang berlaku adalah perhitungan voucher, sehingga hasil akhirnya tetap Rp 450.000.
