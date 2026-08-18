PEMBAYARAN GABUNGAN BEBERAPA METODE (SPLIT PAYMENT)

Total tagihan pada kasus ini adalah Rp 250.000, dan kasir memasukkan pembayaran secara bertahap, yaitu tunai Rp 100.000, kemudian kartu Rp 100.000, lalu tunai lagi Rp 60.000.

Pada input pertama, tunai Rp 100.000, total yang sudah dibayar menjadi Rp 100.000. Sistem memeriksa bahwa nominal itu masih kurang dari Rp 250.000, sehingga statusnya masih Belum Lunas dengan sisa tagihan Rp 150.000. Pada input kedua, kartu Rp 100.000, total yang sudah dibayar menjadi Rp 200.000, masih kurang dari Rp 250.000, sehingga status masih tetap Belum Lunas dengan sisa tagihan Rp 50.000. Pada input ketiga, tunai Rp 60.000, total yang sudah dibayar menjadi Rp 260.000, yang sudah melebihi Rp 250.000, sehingga statusnya berubah menjadi Lunas.

Jadi setiap kali kasir memasukkan satu metode pembayaran baru, sistem selalu menjumlahkan ulang seluruh nominal yang sudah masuk lalu membandingkannya dengan total tagihan. Selama totalnya masih kurang, status tetap Belum Lunas. Begitu totalnya sama dengan atau melebihi tagihan, status langsung berubah menjadi Lunas.

Mengenai kelebihan bayar sebesar Rp 10.000, karena total yang dibayar yaitu Rp 260.000 lebih besar dari tagihan Rp 250.000, maka selisihnya adalah Rp 10.000. Selisih ini tidak ditambahkan ke salah satu metode pembayaran yang sudah diinput, artinya nominal tunai maupun kartu yang sudah tercatat tidak diubah, melainkan disimpan sebagai data terpisah, misalnya sebagai kembalian, lalu ditampilkan kepada kasir agar dikembalikan secara tunai kepada pembeli.

Berikut pseudocode yang menggambarkan logikanya.

    totalTagihan = 250000
    totalDibayar = 0
    daftarPembayaran = kosong

    function tambahPembayaran(metode, nominal):
        tambahkan {metode, nominal} ke daftarPembayaran
        totalDibayar = totalDibayar ditambah nominal

        jika totalDibayar kurang dari totalTagihan:
            status = "Belum Lunas"
            sisaTagihan = totalTagihan dikurangi totalDibayar
        jika tidak:
            status = "Lunas"
            kembalian = totalDibayar dikurangi totalTagihan

        kembalikan status

    simulasi kasus di atas:
    tambahPembayaran("tunai", 100000) hasilnya totalDibayar 100000, Belum Lunas, sisa 150000
    tambahPembayaran("kartu", 100000) hasilnya totalDibayar 200000, Belum Lunas, sisa 50000
    tambahPembayaran("tunai", 60000) hasilnya totalDibayar 260000, Lunas, kembalian 10000
