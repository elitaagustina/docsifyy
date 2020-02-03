# Registrasi
## 1. Registrasi Akun
Konsol ANTARES terdapat pada link berikut. Jika anda telah memiliki akun ANTARES, silahkan langsung login ke konsol. Jika belum, anda perlu melakukan registrasi agar dapat menggunakan layanan ANTARES. Ingin melakukan registrasi? silahkan kunjungi link berikut atau dengan klik tombol Register di halaman konsol.

![regis1](https://user-images.githubusercontent.com/43506640/73622569-4f5b0980-466c-11ea-9649-c022b14ed11b.PNG)
 Gambar 1. Antarmuka Halaman Login
![regis2](https://user-images.githubusercontent.com/43506640/73622660-9b0db300-466c-11ea-84c0-53b812890715.PNG)
Gambar 2. Antarmuka Halaman Registrasi

Setelah mengisi hal-hal yang diperlukan, kami akan mengirim anda email verifikasi. Harap untuk klik tautan yang terdapat pada email tersebut untuk melakukan verifikasi pada akun anda. Jika email verifikasi belum muncul pada email anda, anda bisa klik Resend Verification seperti pada gambar di bawah.


![regis3](https://user-images.githubusercontent.com/43506640/73622686-ad87ec80-466c-11ea-9425-11da2b034f33.PNG)
Gambar 3. Antarmuka Kirim Ulang Verifikasi

Karena anda sudah membuat akun, anda bisa langsung masuk ke konsol ANTARES. Tampilannya akan seperti di bawah.

![regis4](https://user-images.githubusercontent.com/43506640/73622706-c2fd1680-466c-11ea-839e-68f9619ffb08.PNG)

Gambar 4. Antarmuka Konsol Pengguna

## 2. Buat Apps
Sebelum membuat application, anda harus membangkitkan access key. Proses ini hanya dilakukan sekali jika anda merupakan pengguna baru ANTARES. Anda dapat menemukan pilihan ini dengan mengunjungi menu Account -> Access Key -> Get Access key. Access Key merupakan identitas akun anda. Harap simpan access key anda secara aman.

![regis5](https://user-images.githubusercontent.com/43506640/73622728-d6a87d00-466c-11ea-9f6a-fcd69d56d580.PNG)

Gambar 5. Antarmuka Mendapatkan Access Key

Setelah selesai, kita dapat membuat application. Kembali ke menu Application pada halaman dashboard, klik Create an Application. Anda akan masuk ke halaman berikut:

![regis6](https://user-images.githubusercontent.com/43506640/73622744-e7f18980-466c-11ea-9962-eac91e60b895.PNG)

Gambar 6. Antarmuka Pembuatan Application

Silahkan isi dengan informasi yang diperlukan.

![regis7](https://user-images.githubusercontent.com/43506640/73622759-f50e7880-466c-11ea-8966-d0fb328797fd.PNG)

Gambar 7. Antarmuka Pembuatan Application

Selamat, anda telah membuat application pertama anda di ANTARES! Anda dapat menemukan application yang telah dibuat pada dashboard anda.

## 3. Tambahkan Device ke Apps
Internet of Things bersangkutan dengan benda-benda atau things. Pada segmen ini, kita akan membuat suatu device untuk tempat menaruh data.

Halaman di bawah akan muncul. Silahkan klik Add Device. Selain klik Add Device untuk menambahkan device, anda juga dapat membuat device dengan menggunakan RESTful API pada segmen HTTP API. Anda juga dapat melakukan subscription ke device, jadi jika ada data baru yang masuk ke device, anda akan mendapatkan notifikasi. Anda dapat memanfaatkan notifikasi tersebut untuk membuat logika pada program yang anda buat.

![regis8](https://user-images.githubusercontent.com/43506640/73622777-05beee80-466d-11ea-8954-c2ba7c9aa4b9.PNG)


Ambil nama untuk device anda. Dalam kasus ini, kami akan beri nama "SmartEye1"
![regis9](https://user-images.githubusercontent.com/43506640/73622798-1b341880-466d-11ea-86a6-2b5fc143c13f.PNG)


Setelah device berhasil dibuat, akan muncul di dashboard anda seperti berikut.
![regis10](https://user-images.githubusercontent.com/43506640/73622820-2ab36180-466d-11ea-8cdf-740a7cbcc78c.PNG)


Anda telah sukses membuat sebuah device. Ikuti langkah berikutnya untuk menaruh data pada device yang telah anda buat.

## 4. Quickstart
Di bawah ini adalah beberapa contoh kode yang dapat anda gunakan untuk mengirim data dari proyek yang telah anda buat ke ANTARES.

![regis11](https://user-images.githubusercontent.com/43506640/73622837-39017d80-466d-11ea-89c4-4312c4ae1308.PNG)


Di bawah ini adalah video tutorial yang dapat anda gunakan untuk mengirim dan mendapatkan data dari ANTARES melalui ESP8266 (HTTP).
Harap install library ini pada Arduino IDE.



```c++
{#include <AntaresESP8266HTTP.h>

#define ACCESSKEY "your-access-key"
#define WIFISSID "your-wifi-ssid"
#define PASSWORD "your-wifi-password"

#define projectName "your-project-name"
#define deviceName "your-device-name"

AntaresESP8266HTTP antares(ACCESSKEY);

void setup() {
  Serial.begin(115200);
  antares.setDebug(true);
  antares.wifiConnection(WIFISSID,PASSWORD);
}

void loop() {
  int temp = random(25,30);
  int hum = random(75,90);

  antares.add("temperature", temp);
  antares.add("humidity", hum);

  antares.send(projectName, deviceName);
  delay(10000);
}
	}
}
```
![regis12](https://user-images.githubusercontent.com/43506640/73622855-47e83000-466d-11ea-9bff-90b72677642e.PNG)


