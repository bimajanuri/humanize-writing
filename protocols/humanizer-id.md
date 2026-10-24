# Protocol — Humanize, Bahasa Indonesia (HUM / id)

Goal: menghapus jejak penulisan mesin agar teks terbaca sebagai tulisan manusia berbahasa Indonesia yang natural. Deteksi berbasis 26 pola AI dari blader/humanizer, lalu diperluas dengan pola khas teks AI berbahasa Indonesia. Lexicon lengkap: `references/ai-lexicon-id.md`.

**Aturan metode**: setiap pola diperbaiki dengan *menuliskan ulang idenya*, bukan menukar satu kata baku dengan sinonim kamus. Menukar sinonim tanpa mengubah struktur kalimat justru meninggalkan kerangka mesin.

---

## 1. Keluarga pola (deteksi → perbaiki)

### A. Scaffolding esai & pembuka kosong (hapus saat ditemukan)

1. **Pembuka klise dunia-akan** — "Dalam era globalisasi yang serba cepat ini...", "Seiring berkembangnya zaman...", "Di tengah pesatnya perkembangan teknologi..." → langsung ke pokok masalahnya.
2. **"Tak dapat dipungkiri / Tidak dapat dipungkiri bahwa"** → hapus; buktikan klaimnya atau tulis langsung.
3. **"Perlu diketahui / Perlu dicatat bahwa"** → hapus; jika memang perlu, letakkan faktnya.
4. **Pembuka pengantar artikel** — "Artikel ini akan membahas/mengulas...", "Melalui artikel ini, kami akan..." → hapus atau ganti dengan hook faktual yang nyata (angka, kejadian, pertanyaan konkret).
5. **Penutup klise** — "Semoga artikel ini bermanfaat", "Wallahu a'lam", "Demikian yang dapat kami sampaikan" (pada teks non-formal/akademik) → sesuaikan; penutup yang baik menyimpulkan temuan, bukan mendoakan pembaca.
6. **Ajakan basa-basi** — "Yuk, simak artikel ini sampai habis!", "Jangan lewatkan pembahasannya!" → hapus.

### B. Formalitas kaku & calque bahasa Inggris (perbaiki strukturnya)

7. **Calque sintaksis Inggris** — "Hal ini memainkan peran penting dalam..." (← plays a crucial role), "…dapat memberikan dampak yang signifikan terhadap...", "memiliki kemampuan untuk", "melakukan analisis terhadap", "secara komprehensif" → tulis dengan pola kalimat Indonesia: "Ini penting karena...", "…berdampak besar pada...", "mampu", "menganalisis", "menyeluruh/lengkap".
8. **Verba lemah + nomina** — "melakukan pengamatan/pembahasan/penjelasan/penilaian" → "mengamati/membahas/menilai/menjelaskan".
9. **Basa-basi struktural berlapis** — "Berdasarkan hal tersebut di atas, penulis bermaksud untuk melakukan..." → satu kalimat langsung.
10. **Passive tanpa aktor yang berguna** — "Diharapkan agar para pihak..." → siapa yang diharapkan, melakukan apa?

### C. Ritme & sintaksis (perbaiki saat kepadatan tinggi)

11. **Triganda terpaksa** — "baik dari segi X, Y, maupun Z" di mana isinya tidak benar-benar tiga hal paralel → biarkan apa adanya atau potong.
12. **Pembuka kalimat berulang** — beberapa kalimat berurutan dibuka "Dengan...", "Selain itu...", "Di sisi lain..." → variasikan: mulai dari subjek, dari keterangan, dari pertanyaan, gabung dua kalimat.
13. **Konjungsi berlebihan** — "namun demikian", "akan tetapi", "oleh karena itu, hal tersebut" → satu konektor per perpindahan, tidak dua.
14. **Panjang kalimat seragam** — semua kalimat 20–30 kata = ritme mesin. Campur kalimat pendek dan panjang secara disengaja.
15. **Titik-titik dan tanda seru berlebihan** — "Nah, ...", "Yuk, ...", "Tentu saja!" → hematkan atau hapus.

### D. Pembesaran & otoritas pinjaman

16. **Kata sinyal AI** — "sangat penting", "memainkan peran krusial", "lanskap", "revolusi digital", "solusi komprehensif", "inovatif", "terdepan", "berkelanjutan" (tanpa dimaknai), "paradigma", "sinergi", "memberdayakan", "memanfaatkan potensi" (see lexicon) → ganti dengan makna spesifiknya.
17. **Pembesaran signifikansi** — "tidak dapat dilepaskan dari", "sangat fundamental", "berkontribusi secara besar terhadap" → sebesar apa, tepatnya?
18. **Klaim tanpa mekanisme** — "berhubungan erat dengan", "mempengaruhi" → pengaruhnya lewat apa?
19. **Otoritas tanpa sumber** — "para ahli sepakat", "sejarah membuktikan", "riset membuktikan" (tanpa rujukan) → sebut sumbernya, atau turunkan klaimnya jadi pendapat beralasan.

### E. Pemberitahuan format & residu chat (hapus seluruhnya)

20. **Bold dekoratif** — menekan frasa acak di tengah paragraf → bold hanya istilah/istilah kunci nyata.
21. **Judul dekoratif & emoji berlebihan** — kecuali audiensnya memang santai.
22. **Tanda kutip/garis baca mesin** — sumber teks AI yang ditempel mentah (mis. "AI", karakter aneh, format daftar berpoin yang tidak disesuaikan).
23. **Residu chat** — "Tentu! Berikut adalah...", "Semoga membantu!", "Sebagai AI...", "Berikut versi yang sudah direvisi..." → hapus semua.
24. **Meta-tentang naskah** — "Makalah ini terdiri dari tiga bagian yang akan membahas..." sebagai kalimat pertama paragraf → hapus atau ganti fakta substansial.
25. **Judul diulang jadi kalimat pertama** → hapus pengulangan.
26. **Menulis untuk pembaca yang keliru** — mengulang konteks yang sudah diketahui pembaca atau menunda keputusan sampai setelah diagnosis umum → mulai dari pokok, keputusan, atau konsekuensi yang dibutuhkan pembaca. Pertahankan konteks hanya jika konteks itu memengaruhi keputusan pembaca.

## 2. Heuristik kepadatan (kapan suatu pola dihitung temuan)

- ≥2 kemunculan per halaman per pola → perbaiki semua.
- ≥3 keluarga pola berbeda dalam satu paragraf → tulis ulang paragraf dari idenya, bukan dari kalimatnya.
- Ragu? Baca luar: kalau terdengar seperti naskah presentasi korporat atau esai template kampus 2005, tulis ulang.

## 3. Yang TIDAK boleh "dihumanisasi"

- Istilah teknis yang memang baku (nama metode, istilah hukum/medis/akademik) — presisi mengalahkan detektor.
- Suara penulis yang disengaja: jika penulisnya memang formal baku (naskah akademik), jangan diselantingkan jadi kasual.
- Kutipan, judul karya, nama orang/lembaga.
- Jangan menyisipkan typo, singkatan "gaul", atau slang untuk memalsukan kesan manusia. Manusia ≠ belepotan; register harus tetap sesuai tujuan.
- Jangan mengorbankan kaidah tata bahasa demi "kelihatan natural".

## 4. Rekonstruksi suara (bila sumber tak punya suara)

Kalau teks AI datar tanpa persona yang terdeteksi, tetapkan satu sebelum menulis ulang:
1. Tentukan pembaca tersirat (dosen, klien umum, pembaca blog) dan tujuan (menginformasikan, meyakinkan, mengajar).
2. Pilih suara yang cocok: mis. "praktisi paham materi, langsung ke inti, formal-ringan, contoh konkret".
3. Tulis ulang dengan suara itu secara konsisten — satu manusia yang konsisten mengalahkan tekstur acak.
4. Sebutkan pilihan suara dalam satu baris di change log bila pengguna mungkin keberatan.

## 5. Pass verifikasi

Setelah menulis ulang, pindai ULANG output dengan lexicon (`references/ai-lexicon-id.md`):
- Kata tersisa yang terdeteksi harus bisa dipertahankan (istilah baku, kutipan, atau satu-satunya kata yang tepat).
- Cek ritme: variasi panjang kalimat dan pembuka kalimat antar paragraf.
- Cek pemicu format (bold, judul, tanda baca dekoratif) — ini paling sering lolos dari penyuntingan level kata.
- Cek kecocokan pembaca: draf harus langsung menjawab kebutuhan pembaca tanpa mengulang konteks yang sudah tersedia dalam percakapan atau dokumen.
