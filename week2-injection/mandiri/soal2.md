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

<img width="958" height="501" alt="image" src="https://github.com/user-attachments/assets/3ab5b007-f4b5-4b4a-87a5-0cc39b450dda" />


5. Berhasil masuk sebagai **administrator**. 

<img width="845" height="264" alt="image" src="https://github.com/user-attachments/assets/5b19463b-d374-4b6b-8d9a-084c33bdca22" />

## Kesimpulan

* Jenis bug: **SQL Injection (Authentication Bypass)**
* Dampak: Penyerang bisa login tanpa tahu password asli.
* Solusi: Gunakan **prepared statements / parameterized queries** dan jangan pernah menggabungkan input user langsung ke query SQL.


