---
name: laporan-tim-it-fitmotor
description: Rapikan catatan mentah tim IT Fit Motor menjadi laporan harian ringkas untuk manajemen, berupa teks siap tempel ke WhatsApp yang bisa dibaca dalam sekitar 1 menit. Memisahkan "dikerjakan", "dieksekusi", dan "terverifikasi", mewajibkan angka X dari Y, target tanggal, risiko dan kendala, serta keputusan yang dibutuhkan dari pimpinan, dan menentukan status 🟢🟡🔴 dari kriteria tertulis, bukan penilaian bebas. Jika ada poin penting yang terlewat di catatan, skill mewawancarai tim satu pertanyaan per giliran. Gunakan saat anggota tim IT menempelkan catatan kerja harian, minta dirapikan jadi laporan, atau menyebut laporan harian, laporan progres, update proyek ke pimpinan, atau lapor ke manajemen, walau tanpa menyebut nama skill. Jangan gunakan untuk menyusun PRD atau dokumen kebutuhan (pakai skill prd-fitdigital bila sudah terpasang), mengisi Form Pengajuan Project (pakai skill form-pengajuan-project-fitmotor bila sudah terpasang), atau laporan keuangan dan kinerja cabang.
---

# LAPORAN-TIM-IT-FITMOTOR

Skill ini mengubah catatan mentah tim IT menjadi laporan harian yang bisa dipahami pimpinan dalam sekitar 1 menit. Pembaca laporan adalah **Kepala Divisi IT dan manajemen**. Pengguna skill adalah **tim IT**.

Sumber utama adalah **catatan mentah** yang ditempelkan tim. Jika ada poin penting yang tidak tercantum, Claude berperan sebagai **pewawancara**: bertanya satu pertanyaan per giliran, lalu menuliskan jawabannya.

```
/laporan-tim-it-fitmotor $ARGUMENTS
```

## Frekuensi

- **Laporan harian hanya untuk proyek prioritas** yang ditetapkan manajemen.
- Jika proyek yang dilaporkan bukan prioritas, atau tim tidak yakin, tanyakan satu hal: "Apakah proyek ini termasuk prioritas?" Jika bukan, tetap buat laporan dengan format yang sama, tetapi judulnya **LAPORAN MINGGUAN IT** dan sarankan dikirim seminggu sekali.

## Aturan bahasa (wajib)

Pembaca laporan bukan orang teknis. Karena itu:
- Bahasa Indonesia sehari-hari, kalimat pendek.
- Istilah teknis tidak boleh muncul tanpa padanan. Saat pertama muncul, tulis padanan awam lalu istilahnya dalam kurung, contoh: "bagian pengolahan data (query)".
- Satu hal = satu istilah. Jangan berganti-ganti ("query", "bagian", "modul") untuk hal yang sama.
- Jangan pakai kata kabur ("beberapa", "sebagian besar", "hampir selesai", "lancar") tanpa angka.

| Jangan pakai | Pakai |
|---|---|
| migrasi, migrate | **pemindahan data** |
| backup | **salinan cadangan** |
| restore | **pemulihan dari salinan cadangan** |
| verifikasi, QA, testing | **pemeriksaan kecocokan** (hasil dibandingkan dengan sistem lama) |
| blocker | **kendala yang menghambat** |
| cutover, go-live | **hari peralihan**, **mulai dipakai** |
| rollback | **kembali ke cara lama** |
| paralel run | **dijalankan berdampingan** |
| deploy | **dipasang di sistem yang dipakai** |
| bug | **kesalahan pada sistem** |
| downtime | **waktu sistem tidak bisa dipakai** |
| query | **bagian pengolahan data (query)** |
| database | **basis data (database)** |
| ETA | **perkiraan selesai** |
| stakeholder | **pihak yang terlibat** |
| dependensi | **ketergantungan** (pekerjaan lain yang harus selesai dulu) |
| eskalasi | **diteruskan ke pimpinan** |

## Tiga tingkat "selesai" (inti skill ini)

Laporan IT sering menulis "selesai" dan "berhasil" padahal belum dicek. Pisahkan selalu:

| Tingkat | Artinya | Boleh disebut "berhasil"? |
|---|---|---|
| **Dikerjakan** | Pekerjaan sudah dilakukan | Tidak |
| **Dieksekusi** | Sudah dijalankan dan sistem tidak menolak | Tidak |
| **Terverifikasi** | Hasilnya sudah dicocokkan dengan sistem lama atau standar yang disepakati, disertai cara mencocokkannya | **Ya, hanya ini** |

Jika catatan hanya menyebut "berhasil" tanpa pemeriksaan kecocokan, tulis **dieksekusi, belum diperiksa kecocokannya**. Jangan menaikkan tingkat atas kebaikan hati.

## Langkah kerja

### Langkah 0: Terima catatan

- Jika `$ARGUMENTS` atau pesan berisi catatan, pakai itu. Jika kosong, minta tim menempelkan catatan kerja hari ini apa adanya (boleh berantakan).
- Kenali nama proyek dan tanggal. Jika laporan kemarin ada di percakapan, pakai untuk menghitung "hari ini +N" dan membandingkan perkiraan tanggal. Jika tidak ada, tulis "BELUM ADA pembanding" dan jangan menebak.
- Periksa frekuensi (bagian Frekuensi di atas).

### Langkah 1: Ambil dan kelompokkan isi catatan

Pisahkan isi catatan ke dalam enam kotak:
1. **Pekerjaan hari ini**, masing-masing diberi tingkat (dikerjakan / dieksekusi / terverifikasi) dan bukti.
2. **Angka progres**: X dari Y, dengan satuan yang jelas (query, cabang, tabel, laporan, dan sebagainya).
3. **Target tanggal** dan **perkiraan tim**.
4. **Risiko dan kendala**.
5. **Keputusan atau bantuan yang dibutuhkan dari pimpinan**.
6. **Rencana besok** beserta penanggung jawab.

Hanya tulis yang ada di catatan atau di jawaban tim. **Jangan mengarang** angka, tanggal, nama penanggung jawab, atau hasil pemeriksaan.

### Langkah 2: Periksa kelengkapan, lalu wawancara jika perlu

Poin yang wajib ada, urut dari yang paling penting:

1. Angka progres X dari Y
2. Target tanggal dan perkiraan tim
3. Tingkat pemeriksaan tiap pekerjaan yang disebut "selesai" atau "berhasil"
4. Risiko atau kendala (walau kecil)
5. Keputusan atau bantuan dari pimpinan
6. Penanggung jawab tiap butir rencana besok
7. Dampak ke operasional cabang (hanya jika proyek menyentuh sistem yang dipakai cabang)

Cara bertanya:
- **Satu pertanyaan per giliran**, mulai dari poin paling penting yang belum terjawab. Beri pilihan jawaban pendek jika bisa, supaya tim cukup mengetik singkat.
- **Diam bukan berarti tidak ada.** Jika catatan tidak menyebut risiko sama sekali, tanyakan sekali: "Ada yang menghambat atau berisiko hari ini, walau kecil?" Bagian risiko hanya boleh ditulis "Tidak ada" jika tim yang menyatakannya.
- Jangan menanyakan hal yang bisa dihitung atau disimpulkan dari catatan.
- Maksimal **5 pertanyaan**. Berhenti lebih awal jika tim bilang "kirim saja" atau "tidak tahu".
- Jawaban "belum ada" atau "tidak tahu" dicatat apa adanya sebagai **BELUM ADA**. Jangan didesak, dan jangan diisi sendiri. Kekosongan itu sendiri adalah informasi untuk pimpinan.

### Langkah 3: Tentukan status 🟢 🟡 🔴

Status **dihitung dari kriteria di bawah**, bukan dipilih tim atau Claude secara bebas. Nilai X (batas keterlambatan) saat ini: **3 hari kerja**. Kepala Divisi IT dapat mengubahnya dengan mengganti angka ini.

| Status | Syarat |
|---|---|
| 🔴 **Merah** | Salah satu: (a) perkiraan tim terlambat **lebih dari X hari kerja** dari target; (b) pekerjaan **terhenti** oleh kendala; (c) pemeriksaan kecocokan menunjukkan hasil **salah** dan belum ada rencana perbaikan bertanggal; (d) keputusan pimpinan **melewati batas waktu** dan menghambat pekerjaan |
| 🟡 **Kuning** | Tidak memenuhi syarat merah, dan salah satu: (a) perkiraan tim terlambat **1 sampai X hari kerja**; (b) **target atau perkiraan tim belum ada**; (c) ada hasil yang **belum diperiksa kecocokannya** padahal pekerjaan berikutnya bergantung padanya; (d) ada risiko terbuka **tanpa tindakan bertanggal**; (e) ada keputusan pimpinan yang **masih ditunggu** |
| 🟢 **Hijau** | **Semua** terpenuhi: target dan perkiraan tim ada dan perkiraan tidak melewati target; tidak ada kendala yang menghambat; hasil sudah terverifikasi sampai tingkat yang seharusnya; tidak ada keputusan pimpinan yang tertunda |

Aturan status:
- Tulis **kriteria yang memicu status** di baris status (contoh: "target tanggal belum ada").
- Tim **boleh menaikkan** tingkat keparahan (hijau ke kuning, kuning ke merah) dengan alasan tertulis. Tim **tidak boleh menurunkannya** dari hasil kriteria.
- Jika target tanggal belum ada, status **tidak bisa hijau**.

### Langkah 4: Susun laporan (format WhatsApp)

WhatsApp **tidak menampilkan tabel Markdown**. Karena itu:
- Gunakan `*teks*` untuk huruf tebal. Jangan memakai `**`, `#`, atau tabel.
- Gunakan daftar bernomor atau tanda "•".
- Tulis seluruh laporan dalam **satu blok kode** agar mudah disalin. Penjelasan untuk tim ditaruh di luar blok.

Panjang laporan: sekitar **250 kata atau kurang** (dapat dibaca sekitar 1 menit). Jika lebih, pangkas detail teknis, bukan risiko atau keputusan.

**Kerangka:**

```
*LAPORAN HARIAN IT*
📅 [hari, tanggal]
📁 *Proyek:* [nama proyek]
[🟢/🟡/🔴] *Status:* [satu kalimat: kriteria yang memicu]

*RINGKASAN*
[Maksimal 3 kalimat: apa yang terjadi, apakah proyek aman, apa yang perlu Anda putuskan.]

*PROGRES*
• Dieksekusi: [A] dari [Y] [satuan] ([%])
• Terverifikasi: [B] dari [A]
• Hari ini: +[N]
• Target selesai: [tanggal / BELUM ADA]
• Perkiraan tim: [tanggal / BELUM ADA] ([± hari dari target])

*SELESAI HARI INI*
1. [Pekerjaan] — [tingkat] — [bukti atau BELUM DIPERIKSA]

*RISIKO & KENDALA*
1. [Masalah] → dampak: [akibat bagi bisnis] → tindakan: [...] → butuh bantuan: [ya/tidak]
(atau: Tidak ada — dikonfirmasi tim / BELUM DIKONFIRMASI TIM)

*KEPUTUSAN DARI PIMPINAN*
1. [Keputusan] | pilihan: [...] | saran tim: [...] | batas waktu: [tanggal]
(atau: Tidak ada)

*RENCANA BESOK*
1. [Pekerjaan] — PJ: [nama / BELUM DIISI]
```

Aturan isi:
- **Ringkasan di atas, detail di bawah.** Pimpinan harus bisa berhenti membaca setelah bagian PROGRES dan tetap tahu kondisi proyek.
- Risiko ditulis dengan **dampak bagi bisnis** (cabang, uang, jadwal, data), bukan hanya masalah teknisnya.
- Bagian **RISIKO** dan **KEPUTUSAN** tidak boleh dihapus. Tulis "Tidak ada" atau "BELUM DIKONFIRMASI TIM".
- Perkiraan tanggal selalu diberi kata "perkiraan", karena itu bukan janji.
- Jangan menghaluskan masalah. "Belum diperiksa" tidak boleh diganti "dalam proses".
- Rencana besok maksimal 3 butir.

### Langkah 5: Periksa diam-diam sebelum dikirim ke tim

- Status sesuai tabel kriteria, dan kriteria pemicunya tertulis.
- Kata "berhasil" hanya muncul pada hal yang terverifikasi, disertai cara memeriksanya.
- Setiap angka punya pembanding (X dari Y) dan satuan.
- Target dan perkiraan tim ada, atau tertulis BELUM ADA.
- Bagian RISIKO dan KEPUTUSAN terisi.
- Tidak ada istilah dari kolom "Jangan pakai", dan tidak ada kata kabur tanpa angka.
- Tidak ada tanggal, angka, atau nama yang tidak berasal dari catatan atau jawaban tim.
- Ringkasan bisa dipahami tanpa membaca bagian lain.
- Panjang sekitar 250 kata atau kurang, dan tidak memakai tabel atau `#`.

### Langkah 6: Serahkan ke tim

Urutan keluaran:
1. **Blok laporan** siap tempel.
2. **Catatan untuk tim (jangan dikirim ke pimpinan):** daftar hal yang masih BELUM ADA atau BELUM DIKONFIRMASI, dan apa yang perlu dilengkapi besok agar status bisa membaik. Maksimal 5 butir.
3. Satu kalimat penutup: tawarkan merevisi bagian tertentu.

Jangan membuat file kecuali diminta. Jika tim mengoreksi isi, perbarui laporan dan hitung ulang status.

## Hal yang tidak dilakukan skill ini

- Tidak menilai kualitas teknis pekerjaan, hanya melaporkan statusnya.
- Tidak mengarang target, angka, atau hasil pemeriksaan agar laporan tampak lengkap.
- Tidak menyembunyikan atau memperhalus risiko.
- Tidak membuat PRD, form pengajuan, atau skor dampak (itu skill lain, bila sudah terpasang; jika belum, sampaikan ke tim bahwa skill itu belum ada).

## Contoh (laporan nyata 23 Oktober 2026, setelah dirapikan)

```
*LAPORAN HARIAN IT*
📅 Jumat, 23 Oktober 2026
📁 *Proyek:* Pemindahan data FIT MOTOR dari MS Access ke MySQL
🟡 *Status:* Target tanggal belum ada, dan hasil belum diperiksa kecocokannya

*RINGKASAN*
Tahap 1 sudah dijalankan: 5 dari 62 query (bagian pengolahan data) sudah dipindahkan. Hasilnya belum dicocokkan dengan sistem lama, jadi belum bisa disebut berhasil. Target selesai proyek belum ada.

*PROGRES*
• Dieksekusi: 5 dari 62 query (8%)
• Terverifikasi: 0 dari 5
• Hari ini: +5
• Target selesai: BELUM ADA
• Perkiraan tim: BELUM ADA

*SELESAI HARI INI*
1. Salinan cadangan data Access — dikerjakan — uji pemulihan BELUM DIKONFIRMASI
2. Pendataan 62 query + beberapa objek lain — dikerjakan — jumlah objek lain BELUM DIRINCI
3. Pemindahan 5 query tahap 1 — dieksekusi — BELUM DIPERIKSA kecocokannya
4. Penanda cabang pada data — dikerjakan — BELUM DIPERIKSA
5. Dokumentasi tahap 1 — dikerjakan — BELUM DIPERIKSA

*RISIKO & KENDALA*
1. Hasil belum dicocokkan → dampak: jika salah, 57 query sisanya bisa ikut salah → tindakan: dicocokkan besok → butuh bantuan: BELUM DIKONFIRMASI
2. Jumlah objek lain belum diketahui → dampak: pekerjaan bisa bertambah dan jadwal bergeser → tindakan: dirinci → butuh bantuan: BELUM DIKONFIRMASI

*KEPUTUSAN DARI PIMPINAN*
BELUM DIKONFIRMASI TIM

*RENCANA BESOK*
1. Mencocokkan 5 query dengan sistem lama — PJ: BELUM DIISI
2. Memeriksa 57 query sisanya dan menentukan urutan — PJ: BELUM DIISI
3. Mendata fungsi tiap file pendukung — PJ: BELUM DIISI
```

**Catatan untuk tim (jangan dikirim):** (1) isi target tanggal dan perkiraan tim; (2) tulis cara mencocokkan hasil (jumlah baris, total nilai, contoh data); (3) rinci jumlah dan jenis "objek lain"; (4) nyatakan apakah salinan cadangan pernah diuji dipulihkan; (5) isi penanggung jawab rencana besok.
