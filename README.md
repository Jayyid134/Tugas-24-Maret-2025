# Tugas-24-Maret-2025

## 1. Jelaskan Struktur Antar Hubungan dan Beri Contohnya?
### -) Interkoneksi Prosesor dan Memori

Prosesor berkomunikasi dengan memori utama untuk mengambil instruksi dan data.

Menggunakan bus sistem untuk transfer data antara CPU dan RAM.

Contoh: Arsitektur Von Neumann, di mana instruksi dan data disimpan dalam satu memori yang sama.

### -)Interkoneksi Prosesor dan I/O (Input/Output)

Digunakan untuk komunikasi antara CPU dan perangkat input/output seperti keyboard, mouse, dan monitor.

Menggunakan bus I/O atau pengendali I/O (I/O Controller).

Contoh: DMA (Direct Memory Access) memungkinkan transfer data langsung antara memori dan perangkat I/O tanpa intervensi CPU.

### -)Struktur Bus

Bus berfungsi sebagai jalur komunikasi untuk menghubungkan komponen dalam komputer.

Ada tiga jenis bus utama:

Bus Data: Mengirimkan data antara CPU, memori, dan I/O.

Bus Alamat (Address Bus): Mengirimkan alamat lokasi memori.

Bus Kontrol: Mengirimkan sinyal kontrol dan status.

Contoh: Bus PCIe (Peripheral Component Interconnect Express) untuk koneksi kartu grafis ke motherboard.

### -)Interkoneksi Multiprosesor

Digunakan dalam sistem komputer yang memiliki lebih dari satu prosesor.

Bisa berupa Shared Memory Multiprocessing (beberapa prosesor berbagi memori) atau Distributed Memory Multiprocessing (masing-masing prosesor memiliki memori sendiri).

Contoh: Arsitektur SMP (Symmetric Multiprocessing) di mana semua prosesor memiliki akses ke memori yang sama dengan hak yang setara.

### Contoh Kasus
Misalkan ada sebuah komputer yang menjalankan game berat. Struktur antar hubungan dalam komputer bekerja sebagai berikut:

Prosesor (CPU) membaca instruksi dari RAM melalui bus sistem.

GPU (Graphics Processing Unit) terhubung melalui PCIe Bus untuk menangani perhitungan grafis.

Data game dibaca dari SSD/HDD melalui bus SATA/NVMe.

Input dari keyboard/mouse diproses melalui bus I/O.

Output tampilan dikirim ke monitor melalui HDMI atau DisplayPort.

## 2.  Bila terlalu banyak modul atau perangkat dihubungkan pada bus maka akan terjadi penurunan kinerja, sebutkan penyebabnya?:

### -)Kontensi (Contention) Bus

Banyak perangkat yang mencoba mengakses bus secara bersamaan dapat menyebabkan bottleneck karena bus hanya bisa menangani satu transfer dalam satu waktu.

Akibatnya, perangkat harus menunggu giliran, yang meningkatkan latensi komunikasi.

### -)Perebutan Bandwidth

Bandwidth bus terbatas, sehingga jika banyak perangkat menggunakannya, kecepatan transfer data menurun.

Contoh: Jika beberapa perangkat penyimpanan (HDD, SSD, dan USB) menggunakan bus SATA/USB yang sama, kecepatan transfer data dapat berkurang.

### -)Kapasitas Elektrik Terbatas

Setiap perangkat yang terhubung ke bus menambah beban listrik pada jalur komunikasi.

Jika terlalu banyak perangkat terhubung, sinyal bisa mengalami penurunan kualitas atau noise, yang dapat menyebabkan kesalahan data dan retransmisi.

### -)Meningkatnya Latensi

Waktu tunggu (latency) meningkat karena perangkat harus menunggu giliran untuk menggunakan bus.

Misalnya, dalam bus PCIe, jika banyak kartu ekspansi dipasang, masing-masing harus berbagi jalur komunikasi, yang dapat mengurangi kinerja total.

### -)Overhead Manajemen Bus

Dengan lebih banyak perangkat terhubung, sistem harus mengelola dan mengoordinasikan lebih banyak komunikasi.

Ini memerlukan proses kontrol tambahan, seperti mekanisme arbitrasi bus, yang memperlambat respon keseluruhan.

### Solusi untuk Mengatasi Penurunan Kinerja Bus
Menggunakan bus berkecepatan tinggi, seperti PCIe Gen 4/5 dibandingkan dengan PCIe lama.

Menerapkan arsitektur hierarkis, misalnya menggunakan beberapa bus untuk membagi beban kerja (contoh: bus terpisah untuk CPU-memori dan I/O).

Menggunakan teknologi point-to-point, seperti Direct Memory Access (DMA) untuk mengurangi ketergantungan pada CPU dalam transfer data.

Menggunakan cache dan buffering agar data dapat diproses lebih efisien tanpa sering mengakses bus utama.

## 3. Umumnya perangkat berprioritas paling rendah memiliki waktu tunggu rata-rata yang paling singkat. Dengan dasar ini biasanya CPU diberi perioritas tertinggi pada SBI. Sebutkan alasan perangkat berprioritas 16 memiliki waktu tunggu rata-rata paling rendah? Dibawah kondisi seperti apa keadaan diatas tidak berlaku

Perangkat dengan prioritas lebih rendah dapat memiliki waktu tunggu rata-rata lebih singkat dalam sistem bus tertentu. Hal ini terjadi jika sistem menggunakan mekanisme penjadwalan round-robin atau fair scheduling, yang memberikan kesempatan akses secara bergilir. Selain itu, jika perangkat dengan prioritas lebih tinggi memerlukan waktu pemrosesan yang lama, perangkat dengan prioritas lebih rendah bisa mendapatkan akses lebih cepat. Faktor lain seperti jumlah perangkat berprioritas tinggi yang sedikit juga dapat mempercepat waktu tunggu rata-rata perangkat berprioritas lebih rendah.

Namun, kondisi ini tidak berlaku dalam sistem yang menerapkan strict priority arbitration, di mana perangkat dengan prioritas tinggi selalu mendapatkan akses lebih dulu. Jika banyak perangkat dengan prioritas lebih tinggi terus-menerus menggunakan bus, perangkat dengan prioritas lebih rendah harus menunggu lebih lama. Selain itu, jika lalu lintas data pada bus sangat tinggi, akses perangkat berprioritas rendah akan semakin tertunda. Sistem dengan preemption yang kurang efisien juga dapat menyebabkan perangkat berprioritas rendah semakin jarang mendapatkan kesempatan akses.

Oleh karena itu, waktu tunggu rata-rata perangkat tidak hanya bergantung pada prioritas, tetapi juga pada kebijakan manajemen bus yang diterapkan. Jika sistem dirancang dengan mekanisme pembagian akses yang adil, perangkat berprioritas rendah tetap dapat memperoleh akses dalam waktu yang wajar. Namun, jika sistem hanya mengutamakan perangkat berprioritas tinggi tanpa pengaturan khusus, perangkat berprioritas rendah akan mengalami peningkatan waktu tunggu. Dengan memahami faktor-faktor ini, desain sistem bus dapat disesuaikan agar lebih optimal bagi semua perangkat yang terhubung.
