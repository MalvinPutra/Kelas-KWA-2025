##  Write-up: Login Bender (OWASP Juice Shop)

### Langkah Pengerjaan

1. **Masuk ke halaman login** di `/#/login`.
2. Isi **Email** dengan payload SQLi berikut:

   ```
   bender@juice-sh.op'--
   ```
  <img width="576" height="755" alt="image" src="https://github.com/user-attachments/assets/a7a2fa01-1d5d-4d85-851b-d3e12f4f6570" />


   Isi **Password** dengan teks bebas (misalnya: `wasd`).
3. Klik tombol **Login**.
4. Payload `'--` mengabaikan validasi password pada query SQL.

### Hasil

* Berhasil login sebagai **Bender** tanpa tahu password aslinya.

<img width="344" height="290" alt="image" src="https://github.com/user-attachments/assets/2414c91a-f119-4cfc-80e2-c5be12e2c902" />

