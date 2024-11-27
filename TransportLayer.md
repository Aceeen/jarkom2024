# TRANSPORT LAYER

[Fungsi Transport Layer](#fungsi-transport-layer) <br />
[Segmentasi](#segmentasi) <br />
[Reassembly](#reassembly) <br />
[Connection Control](#connection-control) <br />
[Flow Control](#flow-control)<br />
[Error Control](#error-control)<br />
[Multiplexing](#multiplexing) <br /><br />
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
- Membuka dan menutup koneksi antara dua perangkat <br />
![image](https://github.com/user-attachments/assets/9ea91dca-6426-48ba-97fd-02ea583be85f)
<br />
**Protocol Transport Layer**
1. Transmission Control Protocol (TCP)
   - Connection-oriented (perlu komunikasi awal sebelum transmisi dan pesan acknowledgment (ACK) setiap penerimaan data)
   - Reliable (data dijamin sampai tujuan)
   - Cocok untuk transmisi data besar

2. User Datagram Protocol (UDP)
   - Connectionless (tidak perlu komunikasi awal sebelum transmisi)
   - Unreliable (tidak menjamin data sampai tujuan secara utuh). Reliabilitas tergantung dari aplikasi yang digunakan.
   - Cocok untuk transmisi data kecil pada satu waktu
     <br />
     ![image](https://github.com/user-attachments/assets/bb4ba2f6-690a-4ba0-8e89-43d029bf406e)
     <br />

**Three-way Handshake** <br />
![image](https://github.com/user-attachments/assets/a21f479f-9057-4af1-b571-d31652910ffe)
<br />
Koneksi TCP diawali oleh Three-Way Handshake untuk sinkronisasi antara pengirim dan penerima. <br />
Segment data berisi : <br />
- Sequence number (Seq No): Awal byte yang ingin dikirim
- Acknowledgement number (Ack No): Sequence number berikutnya untuk menerima data <br />
Setelah Three-Way Handshake selesai, sesi dianggap terbentuk dan koneksi dua arah siap dilakukan <br />
Selama handshake, informasi tentang jumlah data yang bisa ditransmisikan (Window size) dan sequence number dipertukarkan

### Flow Control
Flow control adalah mekanisme yang digunakan untuk mengelola laju pengiriman data antara pengirim dan penerima, sehingga penerima tidak kewalahan dengan kecepatan data. Transport Layer melakukan Flow Control menggunakan mekanisme sliding windows.
<br />
**Sliding Windows**
Memungkinkan pengirim untuk mengirim serangkaian paket data secara berturut-turut tanpa harus menunggu acknowledgment. <br />
![image](https://github.com/user-attachments/assets/dfa51bce-2df3-4536-8e8e-98813f605222)

### Error Control
Error control adalah mekanisme yang digunakan untuk mendeteksi dan mengoreksi kesalahan dalam transmisi data. <br />
Tujuan utamanya adalah memastikan bahwa data yang diterima oleh penerima adalah data yang sama dengan yang dikirim oleh pengirim, tanpa adanya kehilangan data. <br />
Transport Layer melakukan Error Control menggunakan mekanisme PAR (Positive Acknowledgement with Retransmission). <br />
**PAR (Positive Acknowledgement with Retransmission)** <br />
Setelah koneksi terbentuk, koneksi tersebut harus dipertahankan sampai salah satu pihak ingin mengakhiri komunikasi. Mekanisme PAR (Positive Acknowledgement with Retransmission) memastikan data diterima dengan benar, penerima harus mengirimkan acknowledgement ke pengirim. Acknowledgement hanya berisi informasi tentang paket berikutnya yang harus dikirim. <br />
![image](https://github.com/user-attachments/assets/86d4ab7f-2944-4fd5-96f5-d870efc835ce)


### Multiplexing
![image](https://github.com/user-attachments/assets/b76a6787-aef4-4bae-8875-a06bf862818d)
<br />
Multiplexing adalah mekanisme yang memungkinkan beberapa sinyal atau aliran data untuk dikirim melalui saluran komunikasi yang sama secara bersamaan sehingga penggunaan sumber daya jaringan menjadi lebih efisien. **Transport Layer melakukan Multiplexing menggunakan Port dan Socket**

1. Port
   - Port adalah alamat internal yang digunakan untuk mengidentifikasi aplikasi atau proses tertentu yang berjalan di perangkat.
   - Setiap aplikasi memiliki port yang berbeda, baik yang menggunakan protokol TCP atau UDP
   - Aplikasi TCP/IP biasanya menggunakan nomor port di bawah 1.024, yang disebut "Well-Known Ports”
     ![image](https://github.com/user-attachments/assets/e782bd27-3ab3-4d73-b312-6b303c2b7d40)
2. Socket
   - Socket adalah kombinasi dari IP address dan port number TCP atau UDP
   - Aplikasi membuat socket saat berkomunikasi dengan komputer lain
   - IP address menentukan komputer tujuan, dan port menentukan aplikasi yang digunakan
     ![image](https://github.com/user-attachments/assets/f455124c-2db7-472d-b2cd-9a8f464d8465)






