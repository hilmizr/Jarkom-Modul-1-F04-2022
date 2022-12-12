# Lapres Modul 1 Jaringan Komputer

## Anggota
- Hilmi Zharfan Rachmadi - 5025201268
- Ida Bagus Kade Rainata Putra Wibawa - 5025201235 (Mengerjakan soal nomor 1,2,3)
- Naufal Faadhilah - 5025201221

## Pembagian Tugas
- Ida Bagus Kade Rainata Putra Wibawa 
  - Nomor 1,2,3,8
  - Lapres
- Hilmi Zharfan Rachmadi & Naufal Faadhilah
  - Nomor 4,5,6,7
  - Lapres

## Soal dan Jawaban
1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"!

- Buka wireshark (soal1-2.pcapng), access monta.if.its.ac.id
- Ketik “http” pada display filter

<img width="749" alt="image10" src="https://user-images.githubusercontent.com/84707727/192101862-b6fbfcbd-89a4-4d3d-83ce-153e958d081b.png">

- Pilih salah satu paket, lalu klik kanan dan pilih opsi Follow -> TCP Stream. Muncul gambar sebagai berikut:

<img width="614" alt="image16" src="https://user-images.githubusercontent.com/84707727/192101895-0189ffef-909a-4d40-ac3c-8a595fc1c156.png">
Nama server yang digunakan adalah **nginx/1.10.3**

2. Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?

- Gunakan syntax **contains** untuk mencari keyword “detail topik”

<img width="751" alt="image18" src="https://user-images.githubusercontent.com/84707727/192101917-7a35fde3-7a13-4938-bf28-cdc146383585.png">

- Untuk mengetahui judul topiknya, hanya perlu mengakses route “index.php/detailTopik/194” di browser

<img width="944" alt="image11" src="https://user-images.githubusercontent.com/84707727/192101943-c45ee061-f9b9-4bd7-ae23-5a869c61916c.png">

Judul TA yang dicari Ishaq adalah **Evaluasi Unjuk Kerja User Space Filesystem (FUSE)**

3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80!

- Gunakan capture filter dengan ekspresi “dst port 80”

![jarkom1](https://user-images.githubusercontent.com/70790033/192103075-d23343ff-20a4-4522-b733-3f5c6c8edc50.png)

![jarkom2](https://user-images.githubusercontent.com/70790033/192103078-bce5cd2d-d100-4a66-8fe6-5f27cb194336.png)

4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!
- Jalankan FileZilla server dan client, kemudian gunakan capture filter dengan ekspresi “src port 21”

![image](https://user-images.githubusercontent.com/86661387/192102593-c95550bc-149c-48c9-9a59-b51f41e114cd.png)

- Kendala: tidak dapat menemukan paket yang berasal dari port 21 ataupun paket dengan protokol FTP meskipun sudah berhasil menjalankan FileZilla client-server, hingga dapat melakukan proses transfer antar server dan client.

5. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!

- Gunakan capture filter dengan ekspresi src port 443

![no5_1](https://user-images.githubusercontent.com/70790033/192103134-bb9cbb0b-ad4a-4b03-a01f-7f6008853cd4.png)

![no5_2](https://user-images.githubusercontent.com/70790033/192103137-eef6ed21-dcc2-4fc8-ac82-e03524c340e2.png)

6. Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id!

- Gunakan display filter dengan ekspresi http.host == "lipi.go.id"

![no6_1](https://user-images.githubusercontent.com/70790033/192103193-54a2460f-36da-4c78-868e-7d563369e6d9.png)

7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

- Pertama, periksa IP dengan menjalankan ipconfig di cmd. 

- Kemudian, gunakan capture filter dengan ekspresi src host ip_address.
IP address saya adalah 192.168.100.53, maka saya menggunakan ekspresi src host 192.168.100.53.

![no7_1](https://user-images.githubusercontent.com/70790033/192103282-f1fe015f-c08b-4525-8e35-c4349ce1a717.png)

![no7_2](https://user-images.githubusercontent.com/70790033/192103284-3b24eb5a-3a9d-4f82-865c-682af678eccb.png)

8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.

- Pertama, terdapat dua jenis protokol pada file .pcap yang diberikan, yaitu UDP dan TCP. Dilakukan eksplorasi pada paket-paket dengan protocol TCP terlebih dahulu. Hal ini dapat dilakukan dengan filter “tcp.stream” untuk menampilkan seluruh paket dengan protokol TCP.

<img width="750" alt="image15" src="https://user-images.githubusercontent.com/84707727/192101964-98514cee-0642-4649-930c-ecc2d9384fd4.png">

- Eksplor setiap paket dengan menu Follow -> TCP Stream

<img width="604" alt="image3" src="https://user-images.githubusercontent.com/84707727/192102010-c211de80-c760-4f71-a5f9-e49c8ebfcebc.png">

Percapakan tersebut tidak menunjukkan adanya indikasi kecurangan, mari kita cari kembali dengan menekan tombol arrow pada bagian stream

- Ditemukan percakapan sebagai berikut:

<img width="604" alt="image17" src="https://user-images.githubusercontent.com/84707727/192102048-6ab16c1c-fa8a-49fc-a6bb-1cd9f6708321.png">

Sepertinya percakapan ini mengindikasikan adanya kecurangan. Ditemukan di **stream nomor 12** (tcp.stream eq 12).

- Ditemukan juga percakapan lain:

<img width="604" alt="image1" src="https://user-images.githubusercontent.com/84707727/192102102-dfd87e21-ef13-4e88-a761-58a6fbb2fe94.png">
<img width="604" alt="image8" src="https://user-images.githubusercontent.com/84707727/192102103-fe12c0d7-4f8a-49c3-9dea-d984cb435bda.png">
<img width="604" alt="image9" src="https://user-images.githubusercontent.com/84707727/192102106-0e79559d-af85-40e2-af28-28aa8b8c6fa4.png">
  
