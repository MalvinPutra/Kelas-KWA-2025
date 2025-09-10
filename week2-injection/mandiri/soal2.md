#  Write-up: SQL Injection Login Bypass

## Judul Lab

**Lab: SQL injection vulnerability allowing login bypass (Apprentice)**

---

## Tujuan

Login sebagai **administrator** dengan memanfaatkan SQL Injection di form login.

---

## Langkah Eksploitasi

1. Buka halaman **Login**.
2. Masukkan pada field **Username**:

   ```
   administrator'--
   ```

   (`'--` berfungsi untuk menutup query SQL dan mengabaikan bagian password).
3. Pada field **Password** masukkan sembarang, contoh:

   ```
   WASD
   ```
4. Klik **Login**.
5. Berhasil masuk sebagai **administrator**. ✅

---

## Inti Kerentanan

* Query SQL awal kira-kira seperti:

  ```sql
  SELECT * FROM users WHERE username = 'administrator'--' AND password = 'WASD'
  ```
* Bagian `--` adalah komentar SQL, jadi pengecekan password diabaikan.
* Hasilnya, aplikasi langsung menganggap login sukses.

---

## Kesimpulan

* Jenis bug: **SQL Injection (Authentication Bypass)**
* Dampak: Penyerang bisa login tanpa tahu password asli.
* Solusi: Gunakan **prepared statements / parameterized queries** dan jangan pernah menggabungkan input user langsung ke query SQL.


Mau aku bikinin 5 write-up pendek kaya gini biar langsung jadi bahan tugas GitHub kamu?

