#	Widget	                            Masalah                                 	Perbaikan
1	MenuScreen	Column kehabisan tinggi saat landscape atau keyboard terbuka	Diganti satu CustomScrollView
2	MenuScreen	ListView(children: [...]) membangun semua item di awal	        SliverList.builder
3	MenuScreen	GridView.count dengan 4 kolom tetap	                            SliverGrid.builder dengan MaxCrossAxisExtent
4	MenuScreen	Breakpoint pakai MediaQuery dan > 600	                        LayoutBuilder dengan >= 600
5	MenuScreen	promos[0] dan promos[1] crash kalau data kosong	                Dicek dulu, second boleh null
6	MenuScreen	Tidak ada empty state	                                        Widget EmptyState dengan Key('empty-state')
7	MenuScreen	Notch di sisi kiri saat landscape	                            SafeArea kiri dan kanan
8	StoreHeader	Column dan rating di Row tanpa batas lebar	                    Expanded, rating dipindah, maxLines
9	CategoryBar	Row chip lebih lebar dari layar	                                SingleChildScrollView horizontal
10	PromoStrip	Dua kartu width: 200 di Row	                                    Expanded di dalam IntrinsicHeight
11	PromoCard	width, height tetap, Spacer, teks tanpa batas	                Ukuran tetap dihapus, maxLines
12	MenuTile	Spacer dan nama panjang tanpa batas	                            Expanded dan maxLines: 2
13	MenuCard	height: 110 di sel grid persegi	                                Gambar jadi Expanded dan FittedBox
14	CartBar	height: 72, tombol width: 160, teks tanpa Expanded	                Ukuran tetap dihapus, Expanded, SafeArea untuk gesture bar