NOMOR INVOICE BERURUTAN OTOMATIS

Format nomor invoice yang dipakai adalah INV diikuti tanggal lalu nomor urut, contohnya INV-20260812-0007, dan nomor urut tersebut harus kembali ke 0001 setiap kali berganti hari.

Bagian pertama, langkah-langkah sistem menentukan nomor invoice. Saat ada transaksi baru yang akan disimpan, sistem mengambil tanggal transaksi hari itu, misalnya 20260812. Setelah itu sistem mencari nomor urut terakhir yang khusus dipakai pada tanggal tersebut saja, bukan dari seluruh transaksi sepanjang waktu, biasanya dengan mencari invoice yang diawali dengan INV-20260812- lalu mengambil nomor urut paling besar. Apabila belum ada transaksi sama sekali pada tanggal itu, maka nomor urutnya dimulai dari 0001. Apabila sudah ada transaksi sebelumnya di tanggal yang sama, sistem mengambil nomor urut terakhir kemudian menambahkannya dengan satu. Setelah nomor urutnya didapat, sistem menggabungkannya menjadi format lengkap seperti INV-20260812-0007.

Bagian kedua, cara sistem mengetahui kapan harus mulai lagi dari 0001 dan kapan harus melanjutkan nomor terakhir. Kuncinya ada pada langkah pencarian nomor urut terakhir tadi, yaitu sistem selalu mencarinya berdasarkan tanggal transaksi, bukan berdasarkan seluruh riwayat transaksi yang pernah ada. Jadi begitu tanggalnya sudah berbeda karena berganti hari, otomatis tidak ada satu pun transaksi yang cocok dengan tanggal baru tersebut, sehingga sistem akan mulai lagi dari 0001. Namun apabila masih berada di tanggal yang sama, sistem akan menemukan nomor urut terakhir hari itu dan tinggal melanjutkannya dengan menambah satu.

Berikut pseudocode yang menggambarkan logikanya.

    function buatNomorInvoice(tanggalTransaksi):
        invoiceTerakhir = cariInvoiceTerakhir(awalan = "INV-" + tanggalTransaksi + "-")

        jika invoiceTerakhir tidak ditemukan:
            nomorUrut = 1
        jika ada:
            nomorUrutSebelumnya = ambilNomorUrut(invoiceTerakhir)
            nomorUrut = nomorUrutSebelumnya ditambah 1

        nomorUrutFormatted = formatEmpatDigit(nomorUrut)

        kembalikan "INV-" + tanggalTransaksi + "-" + nomorUrutFormatted

    contoh: buatNomorInvoice("20260812")
    kalau belum ada transaksi hari itu, hasilnya INV-20260812-0001
    kalau sudah ada enam transaksi hari itu, hasilnya INV-20260812-0007
    keesokan harinya, karena tanggal sudah berbeda, otomatis kembali ke INV-20260813-0001
