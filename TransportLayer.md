# TRANSPORT LAYER

[Fungsi Transport Layer](#fungsi-transport-layer) <br />
[Segmentasi](#segmentasi) <br /> <br />
Transport layer merupakan lapisan 4 pada model OSI. Transport layer bertugas mengawasi pengiriman paket process-to-process 
(komunikasi antara dua proses atau aplikasi yang berjalan pada komputer yang berbeda dalam sebuah jaringan). <br />
Transport layer akan melakukan sesi komunikasi antar komputer dalam jaringan dan mengatur bagaimana data ditransmisikan.

## Fungsi Transport Layer
1. Segmentasi & Reassembly <br />
   Memecah data menjadi segmen-segme kecil untuk dikirim.
   Menggabungkan kembali segmen-segmen tersebut menjadi data asli di sisi penerima
2. Connection Control <br />
   Membuka dan menutup koneksi antara dua perangkat.
   Mengelola komunikasi connection-oriented (TCP) dan connectionless (UDP)
3. Flow Control <br />
   Mengatur jumlah data yang dikirim
   Menggunakan mekanisme seperti sliding window untuk menjaga keseimbangan aliran data
4. Error Control <br />
   Memastikan data yang diterima tidak rusak dan sesuai dengan yang dikirim
   Menggunakan teknik seperti checksum dan acknowledgment
5. Multiplexing <br />
   Mengizinkan beberapa aplikasi untuk menggunakan koneksi jaringan yang sama
   Mengidentifikasi data dari aplikasi berbeda dengan menggunakan port


### SEGMENTASI
Data dari banyak aplikasi dikirimkan bersama-sama melalui jaringan yang sama, dan harus diterima oleh aplikasi yang sesuai. <br />
Manfaat segmentasi:
-	Multiplexing: data dari berbagai aplikasi dapat dikirim bersama-sama melalui jaringan 
-	Error control: memanfaatkan checksum pada setiap segmen untuk deteksi error
-	Connection-oriented: Memastikan aplikasi siap untuk menerima data
-	Reliable delivery: Memastikan segmen data yang hilang/rusak harus dikirim ulang supaya data diterima secara utuh penerima
-	Ordered data reconstruction: Memastikan data diterima sesuai dengan urutan saat data dikirimkan
-	Flow control: Mengelola jumlah data yang dikirimkan untuk mengatur kepadatan lalu lintas pada host <br />
**2 Protokol transport layer:** <br />
- TCP <br />
  Header pada segmen memiliki sequence number untuk reassembly
- UDP
  Tidak punya sequence number, mengabaikan urutan data , dan less overhead <br />

### Reassembly
  **TCP** <br />
  - Unit data terkecil: Segmen (unit data yang dibuat oleh transport layer untuk dikirimkan melalui jaringan)
  - Saat segmen sampai tujuan, harus diurutkan terlebih dahulu (re-order)
  - Masuk receiving buffer
  - Diurutkan berdasarkan sequence number <br />

  **UDP**  <br />
  - Unit data terkecil: Datagram (unit data yang dikirimkan dalam jaringan tanpa memastikan urutan pengiriman)
  - Tidak diurutkan
  - Data yang hilang tidak dikirim ulang

### Connection Control
Transport layer memastikan komunikasi antara dua proses dengan cara :
- Mengelola komunikasi connection-oriented (TCP) dan connectionless (UDP)
- Membuka dan menutup koneksi antara dua perangkat



