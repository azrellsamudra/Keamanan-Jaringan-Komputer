**Nama: Muhammad Azrell Samudra** 

**Nim : 09011282126063**

**Keamanan Jaringan Komputer** 

**Dumping And Cracking SAM Hashes to Extract PlainText Password** 

Security Account Manager (SAM) adalah basis data di sistem operasi Windows yang menyimpan informasi akun pengguna dan deskriptor keamanannya. File ini menyimpan kata sandi pengguna dalam bentuk hash (LM dan NTLM). Karena proses hashing bersifat satu arah, ini memberikan tingkat keamanan dalam penyimpanan kata sandi.Dalam konteks peretasan, penyerang biasanya akan mengekstrak hash kata sandi setelah berhasil mengakses komputer target. Hash ini memungkinkan mereka untuk melakukan berbagai serangan, seperti peretasan kata sandi, menggunakan hash untuk mengakses sistem lain, menganalisis kata sandi, dan mengidentifikasi pola untuk memecahkan kata sandi lain dalam lingkungan yang sama.Untuk dapat mengekstrak isi file SAM, diperlukan hak akses administrator. Menilai kekuatan kata sandi adalah langkah penting dalam penilaian keamanan. Proses ini dimulai dengan mengekstrak hash SAM dan kemudian menggunakan metode dekripsi untuk mendapatkan kata sandi dalam bentuk teks biasa.

Tujuan dari dumping dan cracking ini adalah untuk membantu mempelajari cara: 

- Mengetahui cara mengunakan alat pwdump7 untuk mengekstrak hash kata sandi 
- Mengetahui cara mengunakan alat Ophcrack untuk memecahkan kata sandi dan mendapatkan teks biasa 
1. Pertama, kita mencari tahu User ID dengan username menggunakan command prompt yang di run sebagai administrator.
   ![Screenshot 2024-10-22 133917](https://github.com/user-attachments/assets/34c3fad8-7255-4563-b873-3f6635174941)

2. Lalu ketikan code "wmic useraccount get name,sid" yang memiliki fungsi menampilkan daftar semua akun pengguna yang ada di sistem beserta SID-nya masing-masing.
   ![Screenshot 2024-10-22 133838](https://github.com/user-attachments/assets/fdf8f2bb-6712-4c0a-9566-a4659c364ec8)

3. Kemudian download dan ekstrak file pwdump dan ophcrack yang akan digunakan untuk percobaan ini.
   ![Screenshot 2024-10-22 140340](https://github.com/user-attachments/assets/7f87fa7f-f7e1-4b71-bf35-0f0d26bddcd2)

4. Setelah itu buka dan copy lokasi file pwdump dan klik enter untuk masuk ke directory pwdump- master , kemudian ketik PwDump7.exe untuk mendapatkan dan menampilkan password hashes dan userID.
   ![Screenshot 2024-10-22 142344](https://github.com/user-attachments/assets/769cb6f7-f89d-4966-b48c-0fae9ff7d595)

5.Kemudian untuk memindahkan dan men-copy semua data hasil dari PwDump7.exe ke hashes.txt menggunakan command PwDump7.exe > c:\hashes.txt
  ![Screenshot 2024-10-22 150145](https://github.com/user-attachments/assets/e97289bc-11d4-46f8-a40d-f858ebfcbb6a)

6. Berikut ini adalah isi file dari hashes.txt.
   ![Screenshot 2024-10-22 190014](https://github.com/user-attachments/assets/d378bb6f-73c0-4152-b843-ac6cf524cfcb)

7.Lalu isi semua username yang kosong sesuai dengan username pengguna pada step 2 kemudian save file hashes.txt
  ![Screenshot 2024-10-22 142848](https://github.com/user-attachments/assets/8cd1b627-4abc-4466-9bd2-6e91d42bfe2b)

8. Selanjutnya buka oph crack kemudian pilih load PWDUMP file dan pilih file hashes.txt.
   ![Screenshot 2024-10-22 143439](https://github.com/user-attachments/assets/cbfe03d5-3bb1-42f0-9356-5af7cbd452b8)

9. File Hashes tersebut akan tampil dengan lm hash dan nt hash sesuai username user.
  ![Screenshot 2024-10-22 151529](https://github.com/user-attachments/assets/38f2cd0c-31df-4d61-8d67-728daa916b29)

10. Selanjutnya klik table dan pada table selection pilih "xp free small" kemudian klik install, kemudian pilih table xp free small yang sudah di download sebelumnya .
    ![Screenshot 2024-10-22 151453](https://github.com/user-attachments/assets/2830ad5d-69fc-4c4c-b794-463ef23c6dec)

11. Setelah table yang dipilih tampil, kemudian klik icon crack disamping icon untuk mulai memecahkan kata sandi. Ophcrack akan membutuhkan waktu beberapa menit untuk memecahkan kata sandi. Tunggu hingga proses pemecahan kata sandi selesai.
    ![Screenshot 2024-10-22 151529](https://github.com/user-attachments/assets/88cfeea2-9885-46c0-a700-f16d74170796)
    ![Screenshot 2024-10-22 151835](https://github.com/user-attachments/assets/4e4a2742-988a-4f31-950b-1d05aa9f2f89)

12. Setelah  selesai  maka  password  akan  tampil,  Jika  hasilnya  menunjukkan  not  found  maka kemungkinan besar karena windows 11 terbaru secara default tidak lagi menyimpan password di hash  LM  karena  kurang  aman  atau  bisa  juga  karena  beberapa  akun  (seperti  "Guest"  atau "DefaultAccount") mungkin tidak memiliki password atau sedang tidak aktif, sehingga Ophcrack tidak menemukan apa-apa.
    ![Screenshot 2024-10-22 152214](https://github.com/user-attachments/assets/bc4f5297-64ba-4ee3-9c57-40de10d3d925)


