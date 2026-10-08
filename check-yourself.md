1. Bagian mana yang dilanggar, dan oleh widget apa?
Yang melanggar adalah Row-nya, bukan Text. Pada “constraints go down”, Row memberi anak yang tidak fleksibel lebar tak terbatas. Text lalu menentukan ukurannya sendiri sepanjang isi teks (sizes go up). Ukuran itu lebih besar dari lebar yang diberikan ke Row oleh parent-nya, sehingga muncul garis kuning. Text hanya mematuhi constraint yang ia terima, dan tidak ada yang menyuruhnya mengalah. Perbaikannya Expanded atau Flexible supaya ia menerima batas lebar, ditambah maxLines dan ellipsis.

2. Kenapa width: 150 salah, walau garis kuningnya hilang?
Itu angka, bukan hubungan. Angka 150 hanya cocok untuk satu ukuran layar dan satu panjang teks. Di layar yang lebih sempit atau dengan font yang diperbesar, masalahnya muncul lagi. Di layar lebar, ruangnya terbuang. Garis kuningnya hanya pindah ke ukuran layar lain, bukan hilang.

3. Tes mana yang gagal, dan kenapa penting kalau datanya dari API?
Tes 7 (500 item) gagal. shrinkWrap: true memaksa list menghitung tinggi semua anaknya, jadi semua 500 MenuTile dibangun sekaligus dan jumlahnya jauh melewati batas 100. Kalau datanya dari API dan bisa ribuan baris, aplikasi jadi lambat, boros memori, dan patah-patah saat scroll. List yang tidak kamu kontrol panjangnya harus dibangun lazy dengan .builder, supaya hanya item yang terlihat yang dibuat.

4. Kenapa LayoutBuilder, bukan MediaQuery.sizeOf(context)?
MediaQuery hanya tahu ukuran seluruh layar, sedangkan LayoutBuilder tahu ruang yang benar-benar diberikan parent ke widget itu. Kalau widget ditaruh di panel samping, mode split-screen, atau dialog, lebar layarnya bisa 1000 tapi ruang yang tersedia cuma 400. Dengan LayoutBuilder, layout menyesuaikan tempatnya berada, bukan perangkatnya.

5. Kenapa crash data kosong termasuk lab layout?
Karena crash itu terjadi di kode yang membangun layar. promos[0] dan promos[1] mengasumsikan datanya ada, jadi saat data kosong layar langsung error. Layout harus tahan terhadap semua bentuk konten, bukan hanya semua ukuran layar: kosong, satu item, banyak, dan teks sangat panjang. Empty state juga bagian dari desain layout, yaitu apa yang tampil ketika tidak ada isi.