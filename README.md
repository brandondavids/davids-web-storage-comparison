# Web Storage Comparison

## EXPERIMENT 1: Persistence Test
Data disimpan, lalu browser ditutup sepenuhnya.
- Cookies: [**masih ada** / hilang]
- LocalStorage: [**masih ada** / hilang]
- SessionStorage: [masih ada / **hilang**]
<br /> \
![experiment1](screenshots/Experiment%201/1.png)

## EXPERIMENT 2: Tab Isolation
1. Increment 5 kali pada Tab Counter \
Nilai counter di tab baru: 0
<br /> \
*Tab lama*
![experiment2b](screenshots/Experiment%202/2b.png)
*Tab baru*
![experiment2](screenshots/Experiment%202/2.png)
<br /><br />
2. Increment 3 kali di tab baru \
Nilai counter di tab lama: 5
<br /> \
*Tab baru*
![experiment2a](screenshots/Experiment%202/2a.png)
*Tab lama*
![experiment2b](screenshots/Experiment%202/2b.png)
<br /> \
**Kesimpulan:** \
SessionStorage adalah **tab-isolated**.

## EXPERIMENT 3: Storage Size Comparison
Quota yang tersedia untuk:
- Cookies: ~4 KB per cookie
- LocalStorage: ~5-10 MB per origin
- SessionStorage: ~5-10 MB per tab

## EXPERIMENT 4: Decision Quiz
![experiment4](screenshots/Experiment%204/4.png)
Preferensi user untuk memilih dark mode harus persist, tapi tidak harus dikirim ke server. \
<br />
![experiment4a](screenshots/Experiment%204/4a.png)
Untuk data yang bersifat sementara, session storage digunakan. \
<br />
![experiment4b](screenshots/Experiment%204/4b.png)
Token, yaitu value random yang bersifat rahasia (biasanya setelah login) harus secure. Maka, harus menggunakan Cookies HttpOnly, agar terlindung dari XSS dan dikirim ke server. \
<br />
![experiment4c](screenshots/Experiment%204/4c.png)
Sama seperti kasus dark mode, data di shopping cart (tanpa login) harus persist agar tersimpan saat browser ditutup, tapi tidak dikirim ke server.

## PERTANYAAN REFLEKSI
1. **Mengapa session token TIDAK boleh disimpan di LocalStorage?** \
Karena data di LocalStorage dapat dibaca JavaScript dan mudah dicuri lewat serangan XSS.
2. **Apa keuntungan SessionStorage untuk multi-step form dibanding LocalStorage?** \
SessionStorage lebih cocok karena datanya hilang saat tab ditutup sehingga tidak disimpan lama.
3. **Jika kamu membuat aplikasi todo list offline-first, storage mana yang akan kamu gunakan dan mengapa?**
LocalStorage, karena datanya tersimpan secara permanen. Tapi, untuk data dalam jumlah besar, bisa menggunakan IndexedDB.