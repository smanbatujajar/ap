# Masalah Tertulis: Algoritma Sehari-hari
{:.no_toc}

* TOC
{:toc}

## Singkat Kata

Tuliskan algoritma untuk menjelaskan secara lengkap dalam teks dan _pseudocode_, langkah-langkah untuk menyikat gigi, makan jeruk, dan sesuatu yang Anda lakukan setiap hari.

{% include honesty.md %}

## Langkah 1: Baca ini.

Algoritma adalah sekumpulan instruksi untuk menyelesaikan tugas selangkah demi selangkah. Kadang-kadang algoritma ini bisa sangat sederhana. Salah satu cara untuk mengekspresikan algoritma untuk memutuskan cara berpakaian berdasarkan cuaca adalah dengan mengatakan sesuatu seperti ini.

```
Lihat keluar jendela. Jika hujan di luar, kenakan sepatu bot hujan dan jas hujan Anda. Lalu pergi ke luar.
```

Konsep algoritma adalah dasar fundamental dalam ilmu komputer. Ingat sebelumnya bahwa kita mendefinisikan komputer sebagai _perangkat yang menerima input, dan memprosesnya dengan cara tertentu untuk menghasilkan hasil secara otomatis_. Kata kunci dalam kalimat tersebut ketika kita berbicara tentang algoritma adalah kata "proses".

Katakanlah Anda bermain video game favorit. Jika Anda penggemar nostalgia, mungkin game populer ini.<sup>[&#91;1&#93;](#fn-1)</sup>

<iframe src="https://www.youtube.com/embed/zNBwkI0ytZo"></iframe>

Anggaplah Anda membalap Sonic di sekitar Green Hill Zone dan Anda melihat beberapa cincin di udara, di atas kepala Sonic. Karena cincin tersebut melindungi Anda jika Anda diserang musuh, Anda ingin mengambilnya. Untuk mengambilnya, Anda harus menekan salah satu tombol pada controller. Ketika Anda menekan tombol itu, Sonic melompat ke udara dengan ketinggian yang konsisten. Ketika dia menyentuh cincin, cincin itu menghilang dari layar sehingga tidak dapat diambil berulang kali, dan jumlah cincin yang dimilikinya&#8212;ditunjukkan oleh penghitung cincin&#8212;bertambah satu.

Setiap langkah dari proses itu melibatkan banyak algoritma. Dijelaskan secara informal, algoritma tersebut (sangat disederhanakan) dapat dibaca sebagai sesuatu seperti ini:

```
Jika tombol lompat ditekan dan jika Sonic berdiri di tanah, mulailah menggerakkannya ke atas sampai dia
mencapai puncak busurnya. Setelah dia mencapai puncak busurnya, mulailah menggerakkannya ke bawah dengan
mensimulasikan tarikan gravitasi hingga dia berdiri di tanah lagi.
```

Dan untuk cincinnya:

```
Jika Sonic menyentuh cincin, hapus cincin dari layar dan tingkatkan penghitung cincin Sonic satu per satu.
```

Mari kita fokus hanya pada algoritma lompat untuk saat ini, karena "input" untuk algoritma itu jauh lebih jelas. Perangkat yang menjalankan algoritma ini adalah konsol Sega Genesis (atau, yang lebih mungkin saat ini, sebuah emulator) yang menjalankan perangkat lunak _Sonic the Hedgehog_. Apa data atau inputnya? Itu adalah Anda, memegang controller atau joystick Anda, menekan tombol yang membuat Sonic melompat.

Apa hasilnya? Di layar televisi atau monitor Anda melihat ketinggian Sonic di tanah mulai berubah; seperti apa penampilannya mungkin mulai berubah juga. Alih-alih menjaga penampilan yang sama seperti yang dia lakukan ketika berdiri di tanah, biasanya ketika Sonic melompat _sprite_ (istilah yang akan segera kita temui kembali) berubah menjadi bola yang berputar, menunjukkan bahwa lompatannya sebenarnya lebih ke flip atau jungkir balik di udara. Seperti pada dunia nyata, seseorang tidak melompat dari tanah dan kemudian terbang ke langit tanpa batas. Apa yang naik harus turun dan akhirnya setelah mencapai puncak lompatannya Sonic mendarat di tanah lagi.

Semua ini adalah suatu proses. Dan, sebenarnya, prosesnya jauh lebih spesifik daripada itu. kita sangat menyederhanakannya untuk tujuan ilustrasi. Kita juga telah mengabaikan adanya beberapa algoritma yang berjalan secara bersamaan di _threads_ yang terpisah (istilah lain yang akan segera kita temui kembali). Tapi semoga contoh ini cukup untuk saat ini.

Karena proses apa yang terjadi ketika tombol lompat ditekan dapat digambarkan sebagai serangkaian langkah yang jelas, tidak ambigu, (alias, secara algoritmik) konsisten dan, yang penting, dapat diulang. Sonic selalu melompat ke ketinggian yang sama, dia berputar dengan cara yang sama saat melompat, dan dia mendarat di tanah setelah jumlah waktu yang sama. Karena algoritma lompatan, komputer selalu tahu persis apa yang harus dilakukan ketika tombol lompat itu ditekan, dan selalu melakukan persis apa yang diperintahkan untuk dilakukan.

Terkadang paling mudah untuk mengekspresikan suatu algoritma menggunakan bahasa yang sama. Itulah yang telah kita lakukan sejauh ini. Lihatlah kembali algoritma pertama yang disebutkan di atas&#8212;tentang memutuskan apa yang akan dikenakan jika terjadi hujan. Mungkin ada proses pengambilan keputusan yang lebih jelas?

Alih-alih ini:

```
Lihat keluar jendela. Jika hujan di luar, kenakan sepatu bot hujan dan jas hujan Anda. Lalu pergi ke luar.
```

Anda mungkin melihat seorang ilmuwan komputer menggunakan apa yang disebut _pseudocode_&#8212;ekspresi singkat dalam bahasa umum yang disusun dengan cara yang menyerupai apa yang tampak seperti _source code_&#8212;untuk menulis algoritma mereka. Kita akan berbicara lebih banyak tentang _pseudocode_ segera, tetapi membiasakan diri menulisnya sebelum Anda terjun ke pengkodean yang sebenarnya di Scratch, C, PHP, atau JavaScript adalah ide bagus, seperti menulis draf pertama esai.

Inilah salah satu cara untuk menerjemahkan algoritma itu ke dalam _pseudocode_:

```
0   lihat keluar jendela
1   jika di luar hujan
2      kenakan sepatu bot hujan Anda
3      kenakan jas hujan Anda
4   pergi ke luar
```

Kita memberikan nomor pada setiap baris untuk alasan yang akan Anda lihat sebentar lagi. Tetapi perhatikan bagaimana terlepas dari apakah hujan atau tidak, algoritma memerintahkan Anda untuk pergi keluar. Baris ke-1 sampai ke-3 hanyalah hal-hal ekstra yang Anda lakukan sebelum pergi keluar jika kebetulan sedang hujan. Kita menyebut sesuatu seperti "jika hujan di luar" sebuah _condition_. Beberapa algoritma juga memiliki langkah-langkah yang diulang-ulang, seperti ini:

```
Pilih nomor favorit Anda dari 1 hingga 50 secara rahasia. Ketika teman Anda memberi Anda nomor, jika
terlalu tinggi minta mereka menebak lebih rendah dan jika terlalu rendah minta mereka menebak lebih
tinggi. Jika benar, mintalah teman Anda berhenti menebak.
```

Kita menyebut pengulangan seperti itu sebagai _loop_, karena Anda akan terus berputar dan mengitari langkah yang sama sampai beberapa kondisi (teman Anda menebak angka yang tepat) membuat Anda berhenti. Inilah salah satu dari banyak cara untuk mengekspresikan permainan menebak angka dalam _pseudocode_:

```
0   pilih nomor favorit Anda dari 1 hingga 50 secara rahasia
1   minta teman Anda menebak nomor favorit Anda
2   jika teman Anda menebak angka yang lebih rendah
3      beri tahu teman Anda untuk menebak angka yang lebih tinggi
4      kembali ke baris 1
5   lain jika teman Anda menebak angka yang lebih tinggi
6      beri tahu teman Anda untuk menebak angka yang lebih rendah
7      kembali ke baris 1
8   lain
9      beritahu temanmu untuk berhenti menebak
```

Perhatikan di sini bahwa sampai teman Anda menebak angka yang benar, mereka akan kembali ke baris 1 dari algoritma, yang meminta mereka untuk membuat tebakan lain. Hanya ketika mereka menebak dengan benar mereka dapat melanjutkan ke baris 9 dan keluar dari _loop_.

## Langkah 2: Tulis ini.

Oke, sekarang Anda telah belajar banyak tentang algoritma dan _pseudocode_. Mungkin kita harus mencoba menulis beberapa&#8212;tiga, tepatnya. Buka editor teks dan buat file dengan nama `algorithms.docx`. Pertama, tulis algoritma (baik dalam bentuk kalimat maupun dalam _pseudocode_) untuk cara:

* menyikat gigi
* makan jeruk

Selanjutnya, pikirkan sesuatu yang Anda lakukan setiap hari atau hampir setiap hari. Tulis algoritma dalam bentuk kalimat dan _pseudocode_ untuk bagaimana melakukan hal yang Anda pikirkan.

Lakukan yang terbaik untuk menghindari loop tak terbatas (loop yang tidak mungkin untuk keluar) dalam algoritma Anda, jangan sampai Anda terjebak didalamnya selamanya!

## Langkah 3: Lakukan ini.

Sekarang waktunya sedikit bersenang-senang. Sebelum Anda benar-benar mengumpulkan algoritma Anda, Anda mungkin harus meminta seseorang untuk mengujinya. Inilah yang terjadi dalam pertemuan Informatika ketika membuat sandwich selai strawberry menggunakan algoritma yang disediakan oleh siswa.

<iframe src="https://www.youtube.com/embed/hiZz5EE5YCE"></iframe>

Seperti yang Anda lihat, mendeskripsikan algoritma secara tepat sangat penting untuk mendapatkan efek yang diinginkan! Mintalah beberapa teman atau anggota keluarga menguji algoritma Anda, menginstruksikan mereka untuk sama sekali tidak membuat asumsi di luar apa yang telah Anda tulis. Apakah algoritma Anda sudah cukup jelas sehingga serangkaian instruksi yang telah Anda buat dapat diulang persis tanpa kebingungan apa yang harus dilakukan? Apakah teman atau anggota keluarga Anda menemukan cara untuk memecahkan algoritma Anda atau, lebih buruk lagi, menemukan diri mereka dalam _loop_ tak terhingga?

Jika demikian, bantu mereka keluar, lalu tulis ulang instruksi algoritma Anda untuk melihat apakah Anda bisa membuatnya sedikit lebih jelas.

## Cara Mengumpulkan

### Langkah 1 dari 3

Buka [https://github.com/me50/USERNAME](https://github.com/me50/USERNAME), gantikan `USERNAME` di URL dengan nama pengguna GitHub Anda sendiri. Di sisi kiri layar, klik "Branch: master". Di bidang yang bertuliskan "Find or crate branch...", ketikkan `informatikasma/problems/2019/algorithms` dan klik "Create branch".

### Langkah 2 dari 3

Klik tombol yang mengatakan "Upload files". Seret file Scratch `algorithms.docx` Anda ke dalam kotak yang bertuliskan "Drag files here".

### Langkah 3 dari 3

Klik tombol hijau "Commit changes". Kamu sudah selesai!

Kiriman Anda akan dinilai kebenarannya dalam 2 menit, pada saat itu skor Anda akan muncul di [https://submit.cs50.io](https://submit.cs50.io)!

***

<sup><b id="fn-1">1.</b> Jangan khawatir, kita akan segera memberi Mario haknya!</sup>  