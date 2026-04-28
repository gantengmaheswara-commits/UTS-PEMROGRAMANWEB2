# Woww! Cuma Modal ‘ OR ‘1’=’1 Bisa Jebol Database? 🚀
*(Eksperimen SQL Injection)*

### Pendahuluan
Halo semua! Kenalin, saya **Sam**, mahasiswa Informatika. Sebagai orang yang sering berkutat dengan kode (apalagi kalau lagi garap project di **Laragon**), saya sadar kalau keamanan itu bukan cuma tugas tim cyber security, tapi tanggung jawab kita sebagai developer juga. 

Di artikel ini, saya mau berbagi hasil eksperimen sederhana saya tentang salah satu serangan paling klasik tapi mematikan: **SQL Injection**.

---

### Apa sih itu SQL Injection?
Singkatnya, ini adalah teknik di mana “penyerang” memanfaatkan celah pada form input kita untuk masuk ke database tanpa izin. Harusnya form login itu minta username dan password yang benar, tapi karena kodenya kurang aman, penyerang bisa “menyisipkan” perintah SQL tambahan yang menipu sistem kita.

### Langkah Eksperimen
Di sini saya pakai **Laragon** buat bikin lab sederhana. Saya bikin satu tabel `users` dengan satu admin saja. Nah, kodenya kira-kira begini:

<img width="940" height="789" alt="Screenshot 2026-04-28 111814" src="https://github.com/user-attachments/assets/1c84af36-8b44-4733-98bd-062e6f1344a4" />

Bisa dilihat, variabel $user dan $pass langsung saya masukkan ke query tanpa difilter sama sekali. Inilah sumber masalahnya.

### Momen Pembuktian (Eksekusi Serangan)
Sekarang bagian serunya. Pas saya buka di browser, saya nggak masukin password yang bener. Di kolom username, saya cuma ketik: ' OR '1'='1

<img width="430" height="232" alt="Screenshot 2026-04-28 110929" src="https://github.com/user-attachments/assets/b9724cc0-1ca5-4c13-9221-f30296cfc095" />

Hasilnya? Login Berhasil!. Sistem menganggap pernyataan '1'='1' itu selalu benar, jadi dia langsung buka pintu masuk tanpa peduli password-nya apa.Sumpah serem, kan?merindingg asli xixixi

<img width="668" height="411" alt="Screenshot 2026-04-28 110836" src="https://github.com/user-attachments/assets/4ba3a2ff-f8bc-400a-a90c-9037f187b4f2" />

### Terus, Gimana Cara Mencegahnya?

Jangan panik! Solusinya sebenarnya simpel: Jangan pernah percaya sama input user. Kita harus pakai yang namanya Prepared Statements. Kalau kamu pakai framework seperti CodeIgniter 4 (yang lagi saya pelajari juga buat tugas kuliah), biasanya fitur ini sudah otomatis ada lewat Query Builder-nya. Intinya, input user harus dipisah dari perintah SQL-nya biar nggak dianggap sebagai kode perintah.

### Kesimpulan

Dari eksperimen UTS ini, saya belajar kalau bikin aplikasi yang "jalan" itu gampang, tapi bikin yang "aman" itu butuh ketelitian lebih. Jangan sampai sistem yang kita bangun susah payah jebol cuma gara-gara satu baris input yang kita remehkan.Beuh ngeri bngetttt xixixix

Artikel ini disusun untuk memenuhi tugas UTS Pemrograman Web.



