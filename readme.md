# Membuat Development Environment Pribadi dengan VSCode dan Google Cloud
## Table of Content
1. [Apa itu Development Environment](#Apa-itu-Development-Environment)
1. [Cara Membuat Development Environment Pribadi](#Cara-Membuat-Development-Environment-Pribadi)
    - [Pada Komputer Pribadi](#Pada-Komputer-Pribadi)
    - [Pada Komputasi Awan](#Pada-Komputasi-Awan)
        - [Apa itu Cloud Shell](#Apa-itu-Cloud-Shell)
        - [Cara Menggunakan Cloud Shell](#Cara-Menggunakan-Cloud-Shell)
        - [Cara Menginterasikan Cloud Shell](#Cara-Menginterasikan-Cloud-Shell)
1. [Additional - Simple Coding with Database Initialization](#Additional---Simple-Coding-with-Database-Initialization)
1. [Warning - Limitasi Cloud Shell](#Warning---Limitasi-Cloud-Shell)
1. [Referensi](#Referensi)

### Apa itu Development Environment
Mengutip dari techopedia, Development Environment adalah kumpulan dari   
prosedur dan alat-alat yang digunakan untuk mengembangkan aplikasi.

Nah, setelah mengetahui arti dari `development environment`, bagaimana  
cara kita secara umumnya dalam membuat `development environment` pribadi?

### Cara Membuat Development Environment Pribadi
Umumnya kita membuat development environment pribadi dengan menggunakan  
infrastruktur yang kita miliki sendiri seperti komputer / laptop pribadi.

Hal ini bisa saja dilakukan apabila kita memiliki komputer / laptop yang  
cukup canggih, misalnya: Komputer dengan spesifikasi yang cukup canggih  
(Core i5 ke atas, RAM 8GB ke atas, menggunakan SSD, dsb).

Nah, bagaimanakah cara kita melakukannya?

#### Pada Komputer Pribadi
Dalam kondisi yang sempurna ini, di mana seseorang memiliki komputer yang cukup  
canggih, maka membuat development environment ini caranya cukup mudah:
- Memasang Sistem Operasi yang dibutuhkan untuk men-develop aplikasi  
  (mis. Windows 10)
- Memasang IDE / Text Editor dan Tools lainnya
- Memasang Runtime yang dibutuhkan agar dapat menjalankan aplikasi 
  (mis. Node.js)
- Mengatur `Environment Variable` atau `Path` yang dibutuhkan agar dapat  
  menjalankan runtime / aplikasi yang dibutuhkan
- Memasang Database Server apabila dibutuhkan (mis MySQL / PostgreSQL server)
- (Trend Sekarang) Memasang Container Runtime dan Tools yang dibutuhkan
  (mis. Docker)
  ![image](assets/image0.png)

Namun tentunya tidak semua orang memiliki komputer / laptop dengan  
spesifikasi yang canggih untuk bisa membuat development environment pribadi  
yang sesuai dengan kondisi di atas bukan?

Sebagai contoh saja:
- Membuka VSCode yang memiliki aplikasi Node.js dengan menggunakan database  
  PostgreSQL dengan Client Database bernama pgAdmin4 dengan membuka browser  
  Chrome sebanyak 5 s.d. 8 Tab saja pada Sistem Operasi Windows 10, sudah  
  membutuhkan RAM lebih dari 4 GB.

Berdasarkan kasus ini, bagaimanakah cara kita membuat  
development environment pribadi walaupun spesifikasi dari komputer yang  
digunakan tidak cukup canggih?

#### Pada Komputasi Awan

Masalah di atas sebenarnya dapat diselesaikan dengan cara memindahkan 
sebagian load yang dimiliki pada komputer pribadi yang digunakan menuju  
komputasi awan (Cloud), sehingga kita tetap dapat men-develop aplikasi pada
komputer pribadi walaupun komputer kita memiliki spesifikasi yang *KENTANG*.

Adapun solusi yang disediakan perusahaan besar penyedia *cloud* adalah:
- Codespaces by Github (Beta, Invitation Only, nantinya akan berbayar)
- Gitpod.io (Berbayar, versi Free hanya diberikan 50 jam per bulan saja)
- AWS Cloud9 (Berbayar, tidak ada versi Free)
- Cloud Shell Editor by Google Cloud Platform
- dan banyak *Editor on the Cloud* lainnya yang umumnya hanya menyediakan  
  "tempat" untuk menuliskan kode aplikasi saja (namun tidak memberikan  
  infrastruktur yang lengkap untuk menjalankan aplikasi yang dibuat)

Namun dari cara di atas ini, umumnya kita akan sangat terikat pada Editor  
yang sudah disediakan oleh penyedia *cloud* tersebut, sehingga kita tidak akan  
cukup leluasa untuk mengkustomisasi tampilan Editor yang kita miliki.

Nah pada artikel ini, yang akan dibahas adalah mengintegrasikan `Cloud Shell`  
yang disediakan oleh Google Cloud Platform (GCP) dengan VSCode yang ada pada  
komputer pribadi.

##### Apa itu Cloud Shell
Sebelum mengetahui apa itu Cloud Shell dan Editornya, ada baiknya kita mengetahui 
apa itu GCP terlebih dahulu.

GCP adalah layanan penyedia cloud computing yang berasal dari perusahaan aplikasi 
mesin pencari yang besar di dunia, Google.

Cloud Shell, menurut GCP sendiri, adalah sebuah mesin administrasi yang dikurasikan 
oleh Google sendiri yang memiliki akses terhadap sumber daya GCP yang powerful, 
aman secara default, dengan berbagai macam tools yang telah disediakan dan siap untuk digunakkan.

Secara sederhananya, dari kacamata developer, Cloud Shell adalah

```markdown
Sebuah sistem operasi Linux, yang sudah memiliki banyak tools dan runtime yang
terpasang dan siap digunakan untuk mengembangkan aplikasi.
```

Tools apa sajakah yang sudah tersedia di dalam Cloud Shell ?  
(Untuk list lengkap dapat dilihat di 
[sini](https://cloud.google.com/shell/docs/how-cloud-shell-works))

| Tipe | Tool |
| ---- | ---- |
| Linux Shell | bash |
| | sh   |
| Linux Utiliies | Utilities standar Debian |
| Text Editors | Emacs |
| | vim |
| | nano |
| Tools Pengembangan | npm |
| | nvm |
| | pip |
| | composer |
| Versioning | git |
| | mercurial |
| Tambahan | docker |
| | MySQL Client |


##### Cara Menggunakan Cloud Shell
Sebelum mencoba untuk menggunakan Cloud Shell ini, ada sedikit prasyarat yang  
harus dipenuhi:
- Memiliki sebuah akun GMail.

Yap, syaratnya hanyalah dengan memiliki sebuah akun GMail saja !  
Hal ini dibutuhkan karena Akun GCP ini akan terikat dengan akun GMail yang  
digunakan untuk mengakses Cloud Shell.

Kemudian kita tinggal mengunjungi situs https://console.cloud.google.com/  
lalu memasukkan persetujuan dan membuat project awal, lalu menekan tombol
Terminal pada kanan atas halaman Console 

![image1](/assets/image1.png)

dan `voila`, kita sudah berada di dalam Cloud Shell. Mudah bukan?

![image2](/assets/image2.png)

Tapi tentu saja cara ini masih memiliki limitasi, yaitu kita diberikan  
"pinjaman" infrastruktur oleh GCP, namun pada saat kita ingin menuliskan kode  
untuk membuat aplikasi, halaman yang diberikan adalah halaman Terminal atau  
tulisan hitam putih yang cukup menantang untuk membuat kode bukan?

Bagaimanakah cara kita sekarang untuk mempermudah dalam menuliskan kode,  
kalau bisa dengan editor yang mudah digunakan (seperti VSCode), namun tetap  
dapat mengakses infrastruktur yang dberikan oleh GCP berupa Cloud Shell   
tersebut?

```markdown
Singkatnya kita ingin menuliskan kode pada VSCode pada komputer pribadi kita,
namun infrastruktur untuk menjalankan kode tersebut sepenuhnya berada pada GCP.
```

##### Cara Menginterasikan Cloud Shell

**Langkah Nol**  
Nah, sebelum kita mengintegrasikan Cloud Shell pada komputer pribadi kita, ada  
beberapa tools tambahan yang butuh diinstall:
- Visual Studio Code (VSCode) (https://code.visualstudio.com/download)
- Google Cloud SDK (https://cloud.google.com/sdk/docs/install).   
  Untuk Windows ada baiknya menggunakan Cloud SDK Installer, supaya lebih cepat.

Disclaimer:  
- Penulis menggunakan Sistem Operasi Windows dalam membuat tulisan ini,  
  Untuk Sistem Operasi Linux dan Mac OS, seharusnya bisa lebih mudah yah !
- Untuk Windows, terminal yang akan digunakan adalah `cmd` yah, bukan  
  `powershell` (untuk powershell, harus ada langkah tambahan yang tidak  
  dijelaskan di sini).

Setelah melakukan instalasi tersebut, sekarang kita bisa mengakses gcloud cli  
melalui terminal / cmd yang ada pada komputer masing masing.

**Langkah Pertama**  
Setelah melakukan instalasi, langkah pertama yang harus dilakukan adalah login  
ke akun GCP via gcloud cli yang ada.

Hal ini dapat dilakukan dengan mengetikkan perintah di bawah ini pada pada  
terminal / cmd yang digunakan:

```shell
gcloud auth login
```

Pada langkah ini, akan membuka browser secara otomatis dan akan meminta kita  
untuk melakukan login ke akun GMail yang terhubung ke GCP Console.

Setelah melakukan login, kita sudah boleh menutup browser tersebut

**Langkah Kedua**  
Setelah login, langkah selanjutnya adalah kita mencoba untuk masuk ke dalam  
Cloud Shell yang ada pada akun GCP.

Hal ini dapat dilakukan dengan mengetikkan perintah

```shell
gcloud cloud-shell ssh --authorize-session
```

Saat pertama kali langkah ini dilakukan, terminal akan menanyakan untuk  
membuat beberapa file pada `$HOME/.config/ssh/`, jawablah dengan `(Y)es`.
- Pada Windows, lokasinya adalah `C:\Users\USERNAME\.config\ssh\`
- Pada Linux dan Mac OS, lokasinya adalah `/home/USERNAME/.config/ssh/`

Setelah langkah ini dilakukan, pada Linux dan Mac OS, akan langsung masuk ke  
terminal di mana Cloud Shell tersebut berada, sedangkan pada Windows, akan  
membuka sebuah aplikasi PuTTY dan meminta ijin untuk mengakses Cloud Shell,   
jawab dengan `(Y)es`.

Sampai pada langkah ini artinya kita sudah berhasil masuk ke dalam  
Cloud Shell, namun diaksesnya benar-benar dari komputer kita pribadi.

Ketik perintah `exit` untuk keluar dari Cloud Shell.

**Langkah Ketiga**  
Setelah berhasil masuk ke dalam Cloud Shell dan sudah keluar dari Cloud Shell,  
Maka sekarang kita akan membuka VSCode pada komputer kita, kemudian kita akan  
memasang sebuah extension pada VSCode yang bernama `Remote - SSH`.

Langkah untuk memasang extension ini adalah sebagai berikut:
- Pertama-tama, kita akan membuka VSCode kita terlebih dahulu.
- Selanjutnya pada VSCode, navigasi sebelah kiri, pilih `Extensions`   
  (icon berupa 4 buah kubus yang salah satunya terpisah).
  ![image3](/assets/image3.png) 
- Pada navigasi `Search Extensions in Marketpace`, ketik `Remote - SSH`
- Pilih Remote - SSH by Microsoft, lalu tekan `Install`, kemudian tunggu  
  sampai proses selesai.  
  ![image4](/assets/image4.png) 

Sampai pada tahap ini artinya kita sudah siap untuk melakukan koneksi secara  
remote ke Cloud Shell dengan menggunakan SSH.

**Langkah Keempat**  
Pada langkah ini kita akan mulai untuk mengkoneksikan VSCode ke Cloud Shell.

Langkah untuk mengkoneksikan VSCode ke cloud-shell adalah sebagai berikut:
- Pada VSCode, pilih `Terminal` -> `New Terminal`
- (Khusus Windows), pada saat muncul halaman Terminal, tekan icon `v` di   
  sebelah tombol `+`, kemudian pilih `Command Prompt`
  ![image5](/assets/image5.png)
- Selanjutnya kita akan mengetikkan perintah untuk mendapatkan alamat ip dari  
  Cloud Shell agar bisa kita remote ssh. (alamat ip ini berupa angka yang  
  terpisah menjadi 4 bagian, misalnya 30.100.250.50).   
  Perintah untuk melakukan langkah ini adalah:  
  ```shell
  gcloud cloud-shell ssh --authorize-session --dry-run
  ```
- Ketika perintah ini selesai, maka akan muncul sebuah string perintah ssh  
  yang cukup panjang, seperti contoh di bawah ini:
  ```shell
  'putty.exe' -t -P 6000 -i 'C:\Users\USERNAME\.ssh\google_compute_engine.ppk' gclouduser@xx.xxx.xxx.xxx -m 'C:\Users\USERNAME\AppData\Loc16 -m 'C:\Users\USERNAME\AppData\Local\Temp\tmph7xxxxxx'
  ```
  PS:  
  Contoh di atas mengarah pada putty karena pada Windows, gcloud mengarahkan  
  ke putty, sedangkan pada Linux dan Mac OS, gcloud mengarahkan ke ssh).  

  PS2:  
  Contoh di atas mungkin akan berbeda dengan perintah yang ada pada Linux /  
  Mac OS, disesuaikan saja yah.
- Catatlah perintah tersebut dengan baik-baik, karena kita akan memodifikasi  
  dan menggunakan perintah yang panjang ini.
- Pada sebelah kiri bawah pada VSCode, akan ada icon dengan warna hijau, tekan  
  icon tersebut untuk membuka command pallete.   
  ![image6](/assets/image6.png)
- Pada command pallete, pilih perintah `Connect to Host` kemudian pilih  
  `+ Add New SSH Host`, kemudian masukkan perintah yang tadi kita catatkan  
  tadi dengan sedikit modifikasi.  
   ![image7](/assets/image7.png)
- Pada Windows, yang butuh dimodifikasi adalah, 
    - perintah awal yang mengarah pada `putty.exe` harus diganti menjadi 
      `ssh.exe`, 
    - kemudian untuk opsi `-P` harus diganti menjadi `-p` (perhatikan huruf  
      besar dan kecilnya)
    - kemudian untuk file `google_compute_engine.ppk` harus diganti menjadi  
      `google_compute_engine` (tanpa `.ppk`).
    - kemudian untuk opsi `-m` dihapus saja
    - kemudian tambahkan opsi `-o StrictHostKeyChecking=no`

  Sehingga pada Windows, perintah yang akan diketikkan adalah:
  ```shell
  ssh -t -p 6000 -i 'C:\Users\USERNAME\.ssh\google_compute_engine' gclouduser@xx.xxx.xxx.xxx -o StrictHostKeyChecking=no
  ```
- Pada Linux dan Mac OS, perintah yang akan diketikkan adalah sama persis  
  dengan yang dicopy dari terminal.
- Setelah mengetikkan perintah ini, maka VSCode akan menanyakan dimana file  
  konfigurasi ssh yang harus di-update, supaya mudah kita tinggal memilih yang  
  paling atas saja.
- Kemudian setelah berhasil, maka di kanan bawah VSCode akan muncul notifikasi  
  bahwa koneksi SSH telah berhasil ditambahkan, kemudian kita tinggal menekan  
  tombol `Connect` untuk mengkoneksikan ke Cloud Shell.  
 ![image8](/assets/image8.png)
- Selanjutnya akan terbuka sebuah VSCode yang baru yang akan mengkoneksikan  
  ke Cloud Shell.
    - Pada Windows, apabila pertama kali menggunakan Remote SSH ini, maka akan  
      muncul notifikasi Windows Defender Firewall berusaha memblokir access  
      VSCode, pilih enable saja, kemudian pada command pallete akan muncul  
      opsi `Select the Platform of the Remote Host 'xx.xxx.xxx.xxx'`,   
      pilih `Linux`.  
      ![image9](/assets/image9.png)
    - Pada Linux dan Mac OS, tidak ada notifikasi ini.

Sampai pada tahap ini, artinya kita sudah mengkoneksikan VSCode ke Cloud Shell.

Hal ini bisa dilihat pada bagian kiri bawah VSCode, icon hijau tadi sudah   
berubah dan ada informasi tambahan dengan nama `SSH - xx.xxx.xxx.xxx`.

Selain itu juga pada saat membuka terminal, yang terbuka bukan terminal yang  
ada pada komputer kita lagi, melainkan terminal yang terbuka di Cloud Shell.

Dan pada saat membuka folder (`Open Folder`), maka akan muncul folder yang  
terdapat pada Cloud Shell, tidak ada pada komputer kita.

Maka sampai di titik ini kita mulai harus menggunakan git dan lain lain agar  
dapat menyimpan kode yang kita buat dalam mengembangkan aplikasi.

🔥🔥🔥 Selamat memulai membuat aplikasi ! 🔥🔥🔥

```markdown
Apabila sudah selesai dan ingin menutup koneksi ke Cloud Shell, kita tinggal  
menekan tombol hijau di kiri bawah, kemudian memilih `Close Remote Connection`
```

### Additional - Simple Coding with Database Initialization
Sekarang kita akan mencoba untuk membuat aplikasi nodejs yang menggunakan  
database PostgreSQL dan keseluruhan dari aplikasi ini bisa diakses pada   
browser, namun sebenarnya, keseluruhan infrastruktur yang digunakan untuk  
men-develop aplikasi ini seluruhnya ada pada Cloud Shell.

Dikarenakan pada Cloud Shell ini awalnya tidak memiliki PostgreSQL, maka   
seharusnya kita akan menginstall PostgreSQL, kemudian menggunakannya.

Tapi karena kita menggunakan Cloud Shell, dan pada Cloud Shell ini sudah  
terpasang docker dengan docker-compose, maka kita bisa saja menggunakan  
docker-compose untuk membuat PostgreSQL dengan mudah.

Langkah-langkah untuk mendevelop aplikasi nodejs dengan database PostgreSQL:
1. Pastikan sudah login dan berhasil masuk ke dalam Cloud Shell pada VSCode.
2. Buka terminal pada VSCode (`Terminal -> New Terminal`).
3. Pada terminal tersebut, masukkan perintah `mkdir workspaces` untuk membuat  
   folder bernama `workspaces`.
4. Pada VSCode, pilih `File -> Open Folder`, kemudian pilih folder yang baru  
   saja dibuat tadi (`/home/gclouduser/workspaces`).
5. Buatlah sebuah file baru dengan nama `docker-compose.yml` pada folder  
   `workspaces`.
6. Pada file tersebut, tuliskan konten sebagai berikut:
    ```yaml
    version: '3.1'

    services:
      db:
        image: postgres:13.4-alpine
        environment:
          POSTGRES_PASSWORD: postgres
        ports:
          - 5432:5432
      adminer:
        image: adminer:4.8.1-standalone
        ports:
          - 8081:8080
    ```
7. Kemudian selanjutnya kita akan menjalankan docker-compose dengan   
   mengetikkan perintah `docker-compose up -d`.
8. Pada tahap ini, sebenarnya kita sudah berhasil menjalankan postgresql pada  
   port 5432 dan adminer pada port 8081, di Cloud Shell, selanjutnya kita akan  
   melakukan `port forwarding` agar dapat mengakses halaman adminer pada  
   browser yang kita gunakan.
9. Pada VSCode, di bagian Terminal, ada klik tab dengan nama `Ports` kemudian  
   tekan tombol `Forward a Port`  
   ![image10](/assets/image10.png)
10. Pada kolom pertama, ketik `8081`, kemudian tekan `Enter`. `8081` merupakan  
   port `Adminer` (Adminer adalah client db yang dapat diakses pada browser)
11. Setelah ini, kita akan membuka browser, kemudian masukkan alamat url  
   `http://localhost:8081/`, maka akan muncul halaman utama adminer.

Sampai pada tahap ini artinya kita sudah berhasil mengoneksikan  
infrastruktur pada GCP dan bisa diakses dengan `localhost` pada   
komputer pribadi, menakjubkan bukan?

Langkah selanjutnya adalah sekarang kita akan membuat aplikasi berbasis Node.js  
yang kemudian akan ditampilkan pada browser kita juga selayaknya localhost !

1. Buatlah sebuah file dengan nama `app.js` pada folder `workspaces`.
2. Pada VSCode, pilih tab `Terminal` kemudian ketik perintah   
   `nvm install lts/fermium && nvm use lts/fermium`.
3. Perintah ini digunakan untuk menginstall nodejs dengan versi LTS terbaru  
   pada Cloud Shell (pada saat tulisan ini dibuat, nodejs LTS terbaru adalah  
   `lts/fermium`, sesuaikan dengan kondisi pada saat mencoba tulisan ini yah !).
4. Ketik perintah `npm init -y` untuk membuat file `package.json`
5. Ketik perintah `npm install express && npm i -D nodemon`  
   untuk menginstall express pada folder project berada.
6. Pada file `app.js` ketiklah kode berikut:
    ```javascript
    const express = require('express');
    const app = express();

    const port = process.env.PORT || 10000;

    app.use(express.urlencoded({ "extended": false }));
    app.use(express.json());

    app.get("/", (req, res) => {
        res
            .status(200)
            .json({ code: 200, message: "Hello World" });
    });

    app.listen(port, _ => console.log(`Apps bekerja pada port ${port}`));
    ```
7. Pada terminal, ketik perintah `npx nodemon app.js` untuk menjalankan
   aplikasi
8. Buka tab `Ports`, kemudian tambahkan sebuah port baru yaitu `10000`.
9. Bukalah pada browser `http://localhost:10000/` dan lihatlah hasilnya.

Selamat sampai di sini kita sudah berhasil membuat aplikasi Node.js sederhana  
dan berhasil mengakses PostgreSQL pada Cloud Shell !

🔥🔥🔥 Happy Developing !!! 🔥🔥🔥

### Warning - Limitasi Cloud Shell
Tiada gading yang tak retak, begitu pula dengan Cloud Shell ini sendiri,  
pastinya akan ada harga yang harus dibayarkan karena kita menggunakan Cloud  
Shell ini sendiri, yang selanjutnya akan kita sebut sebagai limitasi Cloud  
Shell.

Limitasi Cloud Shell ini adalah:
  - Tempat penyimpanan / storage yang diberikan hanya dapat disimpan pada  
    `/home/<namauser>` saja.
  - State pada aplikasi tidak dapat disimpan, hanya kode-nya saja  
    (Cloud Shell memiliki idle time sekitar 30 menit, apabila tidak ada  
    aktivitas dari pengguna, maka Cloud Shell akan direstart secara otomatis  
    dan akan kembali ke state awal, kecuali data yang disimpan pada  
    `/home/<namauser>`)
  - Data tidak disimpan dalam storage offline (Apabila mau kode tersebut harus  
    didownload atau ditaruh pada server repo lainnya (mis. Github)
  - Belum dapat digunakan untuk `Mobile App Development`, karena tidak bisa  
    digunakan untuk usb debugging / emulator
  - Limitasi Waktu
      - Cloud Shell sendiri hanya memiliki batas waktu sekitar 50 jam   
        per minggu.

### Referensi
- https://www.techopedia.com/definition/16376/development-environment
- https://cloud.google.com/shell/docs/how-cloud-shell-works
