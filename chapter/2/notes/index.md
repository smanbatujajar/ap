# Internet
{:.no_toc}

* TOC
{:toc}


## Pengantar
- Kita menggunakan internet setiap hari dan memiliki akses dan konektivitas yang konstan
- Jaringan rumah

  ![home network](homenetwork.png)

  - Modem kabel, modem DSL, atau perangkat internet fiber
    - Terhubung ke internet
    - Bayar bulanan ke ISP (Internet Service Provider)
      - Telkom, Biznet, ICON+, dsb.
    - Mungkin terdapat konektivitas nirkabel bawaan untuk perangkat Anda
      - Mungkin membutuhkan router rumah tambahan
        - Perangkat terhubung ke router melalui kabel atau wifi

## IP

- Setiap komputer di internet memiliki alamat IP (Internet Protocol)
  - Dalam bentuk #.#.#.#
    - Empat angka terpisah oleh titik dengan nilai antara 0-255
    - Format IP address lainnya juga ada saat ini
  - Seperti alamat pos, mereka secara unik mengidentifikasi komputer di internet
    - Perangkat apa pun yang terhubung ke internet memiliki alamat IP
      - Memungkinkan komputer lain berbicara dengannya
- ISP menetapkan alamat IP ke komputer Anda (router)
  - Dulu dikonfigurasi secara fisik
  - DHCP (Dynamic Host Configuration Protocol)
    - Perangkat lunak yang disediakan ISP untuk memungkinkan komputer Anda meminta alamat IP
    - Server DHCP merespons dengan alamat IP tertentu untuk rumah Anda
  - Beberapa perangkat dapat terhubung ke jaringan rumah Anda
    - Router rumah mendukung DHCP dan memberikan alamat IP ke perangkat Anda

## DNS

- Kita mengakses situs web menggunakan nama domain (Facebook.com, Google.com, dll.), tetapi ternyata situs-situs ini juga memiliki alamat IP
- Server DNS (Domain Name System) mengubah nama domain menjadi alamat IPaddresses

## Packets

- Komputer berkomunikasi dengan mengirim paket, yang seperti amplop virtual yang dikirim antar komputer
  - Masih dalam bentuk 0 dan 1
- Bandwidth (diukur dalam bit per detik) dari suatu jaringan menentukan jumlah maksimum data yang dapat dikirim dalam jumlah waktu yang tetap. Anda dapat memeriksa bandwidth jaringan Anda dengan mengunjungi [speedtest.net] (https://www.speedtest.net/).
- Sebagai analogi, misalkan kita ingin mencari gambar kucing di internet
- Jadi, kami mengirim permintaan ke server, misalnya Google, seperti "berikan kucing.jpg"
  - Kita menempatkan permintaan ini dalam amplop
- Di amplop, kita mencantumkan IP sebagai alamat pengirim
- Namun, untuk penerima permintaan, kita tidak tahu alamat IP untuk Google
  - Harus mengandalkan DNS
  - Kirim permintaan ke server DNS ISP Anda untuk alamat IP Google
    - Jika server DNS ISP tidak mengetahui alamat IP suatu situs web, mereka akan menanyakan ke server DNS lainnya
    - Terdapat *root server* yang tahu kemana harus mencari alamat IP
- Setelah mengirim permintaan, kita akan mendapatkan respons beberapa milisecon berikutnya

  ![happy cat](happycat.jpg)

- Kucing akan dikirim kembali dalam satu paket atau lebih
  - Jika gambar kucing terlalu besar untuk satu amplop, mengirimkannya dalam satu paket dapat menghabiskan lalu lintas internet
  - Untuk mengatasi ini, Google akan membagi gambar kucing menjadi fragmen yang lebih kecil
    - Masukkan fragmen ke dalam amplop yang berbeda
    - Tulis informasi pada amplop
      - Alamat pengirim: Alamat IP Google
      - Alamat pengiriman: Alamat IP kita
      - Sebutkan jumlah paket pada setiap amplop (1 dari 4, 2 dari 4, dll.)

## TCP/IP

- IP lebih dari sekedar alamat
  - Kesepakatan yang diikuti komputer dan server untuk memungkinkan komunikasi
- Fragmentasi seperti pada contoh amplop didukung oleh IP
  - Jika melewatkan suatu paket, Anda dapat secara logis menyimpulkan paket mana yang Anda lewatkan berdasarkan yang diterima
    - Namun, IP tidak memberi tahu komputer apa yang harus dilakukan dalam kasus ini
- TCP (*Transmission Control Protocol*) memastikan paket dapat sampai ke tujuannya
  - Biasa digunakan dengan IP (TCP/IP)
  - Mendukung nomor urut yang membantu data mencapai tujuannya
    - Saat kehilangan paket, komputer dapat membuat permintaan untuk paket yang hilang
    - Komputer akan menyatukan paket untuk mendapatkan seluruh file
  - Juga termasuk aturan untuk jenis layanan (pengidentifikasi port)
    - Untuk memastikan Google tahu kita meminta halaman web dan bukan email atau layanan lainnya

## Port

- Berdasarkan TCP, dunia telah mementukan standar angka yang mewakili layanan yang berbeda
- Jika 5.6.7.8 adalah alamat IP Google, 5.6.7.8:80 (port 80) memberitahukan kita bahwa kita menginginkan halaman web
  - 80 artinya http (hypertext transfer protocol)
    - Bahasa yang digunakan server web
  - Google akan mengirimkan permintaan ke server web mereka melalui http
- Banyak situs web menggunakan koneksi aman dengan SSL atau HTTPS, yang menggunakan port 443
- Sertifikat SSL ini memvalidasi kunci enkripsi yang digunakan dalam komunikasi aman. Mereka biasanya dikeluarkan oleh otoritas sertifikat.
- Email menggunakan port 25
- Port lain juga ada

## Protocol

- Protokol hanyalah seperangkat aturan
  - Manusia menggunakan ini sepanjang waktu, seperti protokol untuk bertemu orang: berjabat tangan
- Ketika permintaan dibuat ke Google untuk gambar, HTTP memberi tahu Google bagaimana merespons dengan tepat
- World wide web adalah aplikasi yang digunakan untuk melihat halaman web, program, dan file yang menggunakan protokol HTTP. Halaman web ini diawali dengan `http://www`.
- World wide web menggunakan internet, yang merupakan sistem yang jauh lebih besar yang terdiri dari banyak jaringan, menghubungkan jutaan komputer.

## UDP

- User Datagram Protocol
  - Tidak menjamin keberhasilan pengiriman
  - Digunakan untuk *Video Call* seperti di WhatsApp
    - Paket dapat diabaikan (*drop*) untuk menjaga agar percakapan terus mengalir
  - Digunakan kapan saja Anda ingin menerima data tanpa menunggu buffer terisi

## IP Lebih Detil

- Alamat IP terbatas
  - Dalam format #.#.#.#, setiap angka adalah 8 bit, jadi total 32 bit
    - Menghasilkan 2<sup>32</sup> atau sekitar 4 miliar kemungkinan alamat
      - Kita kehabisan alamat untuk semua komputer
  - Versi alamat saat ini adalah IPv4
  - Bergerak menuju IPv6
    - Menggunakan 128 bit, menghasilkan 2<sup>128</sup> kemungkinan alamat
- Bagaimana Anda menemukan alamat IP Anda?
- Pada Mac, buka preferensi sistem dan cari sedikit

  ![mac](mac.png)

- Terdapat alamat privat
  - 10.#.#.#, 192.168.#.#, or 172.16.#.#
  - Hanya dengan konfigurasi khusus seseorang dapat berbicara dengan komputer Anda
  - Perangkat pribadi Anda bukan server, jadi orang tidak perlu mengaksesnya secara langsung
    - Perangkat Anda perlu meminta data dari server
  - Bahkan email disimpan di server seperti Gmail dan perangkat Anda membuat permintaan ke server itu untuk mengakses email
- Melihat pengaturan lanjutan ...

  ![mac ethernet settings](macadv.png)

  - Subnet mask digunakan untuk memutuskan apakah komputer lain berada di jaringan yang sama
  - Router (alias Gateway) memiliki alamatnya sendiri
    - Mengatur arah data ke berbagai arah
- Di windows:

  ![windows](windows.png)

  - Memperlihatkan server DNS juga

## Routers

- Router memiliki banyak kabel yang keluar dan masuk
  - Mereka memiliki tabel besar berisi alamat IP dan kemana data harus diarahkan untuk sampai ke tujuan
    - Seringkali, data dialihkan ke beberapa router berikutnya
- Tujuan router adalah untuk mengirim data ke arah tujuan
  - Router selanjutnya akan mengirimkannya ke yang lain hingga mencapai tujuan

  ![network](network.png)

- Internet adalah gabungan dari berbagai jaringan (dengan routernya masing-masing) yang didesain agar skalanya mudah ditingkatkan. Skalabilitas adalah kapasitas sistem untuk berubah ukuran dan skala untuk memenuhi tuntutan baru.
  - Seringkali beberapa cara untuk beralih dari A ke B untuk menciptakan sistem yang lebih toleran terhadap kesalahan, ini disebut redundansi jaringan.
    - Berdasarkan logika Militer AS untuk mencegah putus koneksi saat router tertentu mati
    - Ketika beberapa paket dikirim, seperti cat.jpg dari Google, mereka masing-masing dapat mengambil jalur yang berbeda, akhirnya sampai di tujuan
      - Terkadang internet sibuk dan jalur tercepat berubah
    - Memiliki banyak jalur dari A ke B


## Traceroute

- Berapa lama waktu yang dibutuhkan untuk proses transfer data di internet?
- Traceroute adalah program yang mengirim paket ke setiap router di jalur ke tujuan, melaporkan waktu yang diperlukan untuk mencapai router tersebut
- Dari SMAN 1 Batujajar ke google.com:

  ![traceroute Google](tracertgoogle.png)

  - 1-2: Beberapa router tidak bernama di SMAN 1 BatujajarA few unnamed routers at Harvard
  - 3-5: Router tidak bernama milik ISP Telkom Indonesia
  - 6-8: Router tidak bernama di Singapura milik Telkom Indonesia Internasional
  - 9-15: Router tidak bernama milik Google
  - 16-26: Router menolak menjawab request
  - 27 adalah lokasi server Google yang dapat diakses dalam 23ms!

- Dari SMAN 1 Batujajar ke itb.ac.id

  ![traceroute Berkeley](tracertitb.png)

  - 6-8: Koneksi cepat nasional OpenIXP
    - 6: Router OpenIXP milik Telkom
    - 7: Router pertukaran data antar ISP nasional
    - 8: Router OpenIXP milik Indosat
  - 9: Masuk ke jaringan Indosat
  - 10: Router menolak menjawab request
  - 11-12: Masuk ke jaringan ITB
  - 13 adalah lokasi tujuan yang dapat diakses dalam 16ms!

- Dari SMAN 1 Batujajar ke cnn.co.jp

  ![traceroute Japan](tracertcnnjp.png)

  - 8-9 lompat dari Singapura ke Los Angeles, California menyeberangi samudera!
  - 11-12 lompat lagi dari Los Angeles, California ke Tokyo, Jepang menyeberangi samudera pasifik!
    - Menggunakan kabel bawah laut

## Kabel Bawah Laut

- Guru memperlihatkan video tentang kabel bawah laut

  <iframe src="https://www.youtube.com/embed/IlAJJI-qG2k"></iframe>

## Demo Modem Kabel

- Guru memperlihatkan modem kabel rumah, dengan fokus pada port-portnya
  - Koneksi telepon (RJ11)
  - Empat soket kabel ethernet (RJ45)
    - Berbagai perangkat dapat terhubung ke sini untuk konektivitas internet
  - Modem ini memiliki wifi didalamnya

## Demo Switch Jaringan

- Guru memperlihatkan switch jaringan
  - Perangkat yang dapat Anda pasang ke router Anda untuk memungkinkan lebih banyak koneksi untuk semua perangkat Anda yang lain

## Demo Router Rumah

- Guru memperlihatkan router rumah
- Router rumah mungkin memiliki wifi, firewall, dan switch dalam satu perangkat yang sama

  <iframe title="Router" src="https://sketchfab.com/models/ac86d8ae65a54f4aa99d7d624f71e5f4/embed?autospin=0.2&amp;autostart=1&amp;preload=1" frameborder="0" allow="autoplay; fullscreen; vr" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

## Demo Kabel Jaringan

- Guru memotong kabel ethernet hingga terbuka bagian dalam
- Di dalam kabel jaringan terdapat 8 kawat berbeda-beda warna
  - Beberapa digunakan untuk mengirim data, lainnya untuk menerima data
  - Lainnya untuk isolasi dan penolak interferensi
  - Urutan warna kabel harus mengikuti standar tertentu
