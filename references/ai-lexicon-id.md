# AI Lexicon & Tell-Signs — Bahasa Indonesia

Bantuan deteksi, bukan daftar larangan. Konteks menentukan: sebuah kata hanya menjadi temuan bila (a) dekoratif/kabur, bukan pilihan kata yang tepat, dan (b) bagian dari pola (≥2 per halaman atau berkelompok). Jangan pernah menukar istilah teknis yang presisi dengan kata lemah demi daftar ini.

---

## 1. Kata/frasa sinyal tinggi (over-represented di output LLM)

**Frasa pembuka klise**:
"Dalam era globalisasi yang serba cepat ini...", "Seiring berjalannya waktu...", "Di tengah pesatnya perkembangan teknologi...", "Tidak dapat dipungkiri bahwa...", "Perlu diketahui bahwa...", "Perlu dicatat bahwa...", "Sebagai salah satu...", "Di era digital ini...", "Belakangan ini, semakin banyak..." (klise, bukan fakta).

**Frasa pembesaran**:
"memainkan peran (penting/krusial/vital)", "memegang peranan penting", "tidak dapat dilepaskan dari", "sangat fundamental", "berkontribusi secara signifikan", "menjadi kunci keberhasilan", "solusi yang tepat", "dunia yang semakin kompleks ini", "tantangan dan peluang", "potensi yang luar biasa", "menjadi primadona", "tak asing lagi", "semakin marak", "lazim ditemui".

**Kata sinyal (kata benda/adjektiva)**:
"lanskap" (metaphorical), "revolusi", "paradigma", "sinergi", "ekosistem", "inovasi" (tanpa isi), "komprehensif", "holistik", "multifaset", "dinamis", "berkelanjutan" (tanpa dimaknai), "terdepan", "terpercaya", "berdaya saing", "globalisasi", "transformasi digital", "disrupsi", "daya saing", "potret", "fenomena" (dipakai sebagai hiasan).

**Kata kerja lemah/korporat**:
"melakukan (analisis/pengembangan/penjelasan/penilaian/pengamatan)" → gunakan verba sebenarnya; "memberikan (dampak/kontribusi/penjelasan)", "memanfaatkan (potensi)", "mendorong terciptanya", "menjadi wadah", "turut serta dalam", "berperan aktif dalam", "secara (komprehensif/efektif/optimal)".

**Kata sandiwara formal**:
"Adapun", "Berdasarkan hal tersebut di atas", "Demikian makalah ini kami sampaikan", "Semoga bermanfaat", "Wallahu a'lam" (pada konteks non-formal), "Penulis bermaksud untuk", "Bertolak dari hal tersebut".

**Ajakan & basa-basi konten**:
"Yuk, simak sampai habis!", "Jangan sampai ketinggalan!", "Nah, kali ini kita akan membahas...", "Penasaran? Simak ulasannya!", "Semoga artikel ini menambah wawasan Anda".

## 2. Pemberitahuan struktural (per paragraf)

- Kalimat dibuka "Selain itu", "Di sisi lain", "Lebih lanjut", "Oleh karena itu" beruntun — 3 pembuka sama berturut-turut = temuan.
- Triganda paksa: "baik dari segi X, Y, maupun Z" tanpa alasan isi.
- Pertanyaan retoris + jawaban diri sendiri.
- Setiap paragraf diakhiri kalimat penutup meringkas.
- Panjang kalimat seragam 20–30 kata; panjang paragraf seragam.
- Struktur esai template: pembuka klise → 3 poin → kesimpulan yang mengulang daftar.
- "Artikel ini akan membahas..." sebagai kalimat pertama.
- Judul diulang jadi kalimat pembuka paragraf.

## 3. Pemberitahuan format

- **Bold** dekoratif di tengah paragraf.
- Emoji pada teks formal/akademik; bullet berhias.
- Terlalu banyak judul/subjudul untuk teks pendek.
- Daftar berpoin untuk hal yang seharusnya prosa; daftar tepat 3 atau 5 item berulang kali.

## 4. Residu chat (hapus saja)

- "Tentu! Berikut adalah...", "Berikut versi yang sudah direvisi:", "Semoga membantu!", "Sebagai AI...", "Jika ada yang ingin ditanyakan...", "Apakah ada yang bisa saya bantu lagi?".

## 5. Skor kepadatan (dipakai final audit)

Hitung per 1000 kata:
- 0–2 lexicon hit, tanpa kluster struktural → risiko rendah.
- 3–6 atau satu kluster struktural → sedang; humanisasi sebelum kirim.
- 7+ atau beberapa keluarga pola per paragraf → tinggi; tulis ulang dari idenya.

**Selalu catat**: detektor AI hanyalah heuristik. Teks bisa bersih skor tapi tetap terdengar AI (pemberitahuan struktural lebih menentukan), atau sebaliknya. Optimalkan untuk pembaca manusia lebih dulu.
