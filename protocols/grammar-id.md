# Protocol — Grammar & EYD, Bahasa Indonesia (GRAM / id)

Authority: **Ejaan Bahasa Indonesia yang Disempurnakan (EYD) / PUEBI** and, where EYD is silent or updated, **EYD 2022** (Permendikbudristek No. 18 Tahun 2022, berlaku efektif 2023) + **KBBI** for word choice/baku status. When EYD-2015-PUEBI and EYD-2022 differ, prefer EYD 2022 and note the change if the user might be following older guidance (e.g. institutional templates).

Scope: spelling, punctuation, word formation, baku/non-baku, capitalization, reduplication, affixation. Style/voice issues belong to the humanizer; this protocol handles *correctness*.

---

## 1. Workflow

1. Mechanical sweep first (§2) — patterns that can be hunted systematically.
2. Morphology & word choice (§3) — affixation, baku words, KBBI.
3. Punctuation & mechanics (§4).
4. Capitalization & numerals (§5).
5. Consistency pass (§6).
6. Re-read for meaning: grammar fixes must not change claims (anti-hallucination rules apply — a grammar "fix" that alters scope is a bug).

## 2. Mechanical checklist (hunt these explicitly)

- [ ] **di / ke / yang** as prefixes vs as free words: "dianalisis" (imbuhan, menyatu) vs "di analisis" salah; "ditempati" vs "di tempati" — rule: tulis menyatu bila di awal kata sebagai imbuhan dan tidak menimbulkan kerancuan; terpisah hanya bila tetap bermakna sebagai kata sendiri ("yang di luar", "pergi ke pasar").
- [ ] **bukan / bukanlah vs adalah**: "bukan X" untuk nomina/pronoma; "bukan" tidak dipakai untuk adjektiva ("bukan baik" → "tidak baik").
- [ ] **tidak vs bukan**; **belum / belum lagi**.
- [ ] **kah / lah / tah / pun**: menyatu dengan kata yang didampingi ("apakah", "siapakah", "pastilah", "apapun") — EYD 2022 mengubah penulisan partikel setelah kata ganti tertentu; bila ragu, ikuti pola yang dipakai KBBI terkini dan konsisten dalam naskah.
- [ ] **Angka**: angka 0–10 umumnya ditulis huruf dalam teks umum (kecuali gaya jurnal/kampus yang mensyaratkan angka; konsisten); persen: "10 persen" (EYD) — "%" diperbolehkan pada teks teknis bila gaya lembaga mengizinkan; bilangan bertitik (1.000, 1.000.000).
- [ ] **Sisa singkatan**: "dll., dst., dsb., ds." — EYD 2022 membolehkan tanpa titik (dll, dst, dsb) — pilih satu gaya dan konsisten.
- [ ] **Kata ulang (reduplikasi)**: hanya untuk makna banyak/ganda/berulang yang bermakna; jangan mengulang tanpa fungsi ("para-para" tidak baku, "para" saja sudah jamak; "masing-masing" baku, jangan "masing masing"; "saling-saling" salah → "saling").
- [ ] **Kata serapan**: ikuti bentuk baku terkini di KBBI (contoh klasik: "analisis bukan analisa", "apotek bukan apotik", "risiko bukan resiko", "praktik bukan praktek", "karier bukan karir", "izin bukan ijin", "provinsi bukan propinsi", "silabus bukan silabus/silabus?" — ikuti KBBI).
- [ ] **Kata ganda yang salah**: "adalah merupakan" (redundan — pilih satu), "ikut serta" (pilih "ikut" atau "berpartisipasi"), "kolaborasi bersama" (redundan).
- [ ] **Preposisi**: "diskusi tentang" (bukan "diskusi mengenai/mengenai" berlebih), "berbeda dari" (bukan "berbeda dengan" untuk perbandingan atribut — catatan: "berbeda dengan" lazim untuk membandingkan dua entitas; "berbeda dari" untuk atribut — konsisten), "fokus pada" (bukan "fokus untuk"), "berkontribusi pada/untuk".
- [ ] **Imbuhan salah**: "memberikan" hanya untuk pemberian konkret/metafora kuat — cek redundansi ("memberikan penjelasan" → "menjelaskan"); "ter-" keliru ("tergelar" untuk acara → "digelar"); "meng-" + kata berawalan vokal tanpa petakan ("menganalisis" ✓, "meng analisis" ✗).
- [ ] **Potongan klise esai**: "Dalam rangka untuk" → "untuk"; "pada saat ini" → "saat ini/kini"; "dapat dikatakan bahwa" → hapus/tulis langsung; "semakin ... semakin" dipastikan paralel.
- [ ] **Istilah asing dipertahankan**: istilah Inggris/asing dalam teks TIDAK diterjemahkan atau "diindonesiakan" sewenang-wenang — lihat §3.1.

## 3. Word choice (KBBI gate)

- Every content word should exist in KBBI in the form used. Doubtful word → check KBBI (kbbi.kemdikbud.go.id) if online access exists; otherwise flag.
- Do not "correct" a correct non-obvious word just because it's rare.
- Keep the author's intentional colloquialisms in casual texts; in formal texts, flag them rather than silently deleting (meaning may depend on them).

### 3.1 Istilah asing / bahasa Inggris — pertahankan apa adanya

Kebijakan default untuk SEMUA mode (terutama GRAM, PARA, HUM): **istilah asing dan istilah bahasa Inggris tetap ditulis sama, tidak diterjemahkan ke Bahasa Indonesia.**

1. **Jangan terjemahkan** istilah Inggris/asing ke dalam teks Indonesia: "machine learning", "supply chain", "user interface", "deadline", "brand awareness", "startup" — ditulis apa adanya sesuai bentuk yang lazim dipakai. Menerjemahkannya (apalagi dengan padanan harfiah) berisiko mengubah makna — masuk kategori halusinasi (`protocols/anti-hallucination.md` §3).
2. **Istilah yang sudah diserap baku** (tercatat di KBBI dengan bentuk Indonesia: "aplikasi", "komputer", "internet", "analisis") → gunakan bentuk bakunya — bukan bentuk asingnya, dan juga bukan versi tidak baku ("aplik", "resiko", "praktek").
3. **Jangan mengarang padanan Indonesia.** Padanan resmi hanya dipakai bila user atau kebijakan lembaga mensyaratkannya; tulis istilah asing + padanan dalam kurung pada kemunculan pertama. Jika padanan tidak persis setara maknanya, pertahankan istilah asing — padanan yang melemahkan makna lebih buruk daripada istilah asing.
4. **Ejaan**: istilah asing ditulis sesuai ejaan aslinya yang sudah beredar ("computer", bukan "kompyuter"); sebaliknya, istilah yang sudah masuk KBBI ditulis dalam bentuk Indonesia bakunya.
5. **Parafrase/humanisasi**: jangan mengganti istilah asing dengan deskripsi panjang hanya untuk "memperbanyak bahasa Indonesia". Satu-satunya pengecualian: teks populer untuk pembaca umum yang secara eksplisit meminta tanpa istilah asing — boleh memakai padanan baku, dengan istilah asling dicantumkan sekali saat pertama muncul.
6. **Jangan campur dua bahasa dalam satu frasa**: pilih "kepuasan pelanggan" ATAU "customer satisfaction" — jangan "customer satisfaction pelanggan".

## 4. Punctuation

- **Titik**: akhir kalimat; singkatan sesuai gaya yang dipilih (§2); tidak dua titik berturut-turut kecuali elipsis gaya tertentu (pilih gaya: "..." atau "…" — konsisten).
- **Koma**: sebelum konjungsi penghubung antarkalimat ("tetapi", "namun", "sementara") bila diperlukan untuk kejelasan; **EYD 2022 tidak mewajibkan koma sebelum "dan" pada enumerasi** — pilih gaya serial-comma/serial-no-comma dan pakai konsisten; koma pemisah unsur setara; TANPA koma antara subjek dan verba atau objek dan verba yang tidak perlu.
- **Titik koma** untuk unsur setara panjang dalam satu kalimat.
- **Tanda hubung vs pisah vs sengketa**: "anak-anak" (hubung, kata ulang); "makan nasi—nasi uduk" (pisah, makna berbeda); "perihal—perihal yang…" (sengketa, sisa kalimat); **tidak pakai hubung untuk sambungan kata berawalan vokal** ("ke-adaan" salah → "keadaan").
- **Kurung**: tanda baca di dalam kurung mengikuti isi; kalimat lengkap di dalam kurung → titik di dalam.
- **Tanda kutip**: EYD — kutipan langsung dalam tanda ganda; di dalamnya tanda tunggal; kutipan dalam kalimat → tanda baca akhir di luar kutipan bila mengakhiri kalimat; "dst." di dalam kutipan tetap di dalam.
- **Tanda seru/?**: jangan berlebihan (juga pola AI) — hemat.

## 5. Kapitalisasi

- Awal kalimat; nama diri orang, gelar, lembaga, produk, negara, bahasa, hari, bulan.
- **EYD 2022: musim dan mata angin huruf kecil** ("musim dingin", "angin barat daya") — bedakan dari nama diri resmi yang memakai huruf kapital.
- Singkatan nama lembaga resmi boleh kapital semua sesuai nama resmi.
- Jangan kapital untuk penekanan umum (juga tell AI/dekoratif).

## 6. Consistency pass

- One term per concept (jangan "pengguna / pemakai / user" bergantian untuk konsep yang sama).
- Consistent spelling register (baku/non-baku), consistent numeral style, consistent quotation style, consistent hyphenation of the same reduplicated form.
- Terminology of the field wins over general preference (term of art unchanged).

## 7. Output format for GRAM mode

Deliver: (a) the corrected text, (b) a compact list of notable corrections grouped by category (only meaningful ones, not every comma), (c) flags for anything doubtful that was left as-is. Never claim a correction is required by EYD when it's a style preference — label style fixes as "gaya".
