# Contekan

Aplikasi web pengingat highlight perdagangan untuk bahan Mendag. Halaman awal menampilkan daftar program dengan kolom pencarian. Klik sebuah program untuk membuka detailnya: angka kunci, highlight, dan pertanyaan yang sering muncul.

## Isi file

| File | Fungsi |
| --- | --- |
| `index.html` | Tampilan aplikasi. Tidak perlu diubah untuk memperbarui isi. |
| `data/programs.json` | Seluruh isi program dan highlight. Ubah file ini untuk memperbarui data. |

## Cara memperbarui highlight

1. Buka `data/programs.json` di GitHub, lalu klik ikon pensil (Edit).
2. Ubah atau tambah isi pada program yang dimaksud.
3. Ganti `"updated"` dengan tanggal hari ini (format `TAHUN-BULAN-TANGGAL`, mis. `2026-11-03`).
4. Klik **Commit changes**. GitHub Pages memperbarui aplikasi dalam 1–2 menit.

Program yang `updated`-nya lebih dari 30 hari akan ditandai **Perlu diperbarui**.

### Format satu program

```json
{
  "id": "tei",
  "title": "TEI",
  "full": "Kepanjangan atau subjudul (boleh kosong)",
  "art": "expo",
  "tone": "lilac",
  "updated": "2026-10-27",
  "summary": "Ringkasan singkat (boleh kosong)",
  "tags": ["kata kunci", "untuk", "pencarian"],
  "kpis": [
    { "label": "Transaksi", "value": "USD 22,94 M" }
  ],
  "highlights": [
    "Satu highlight per baris.",
    "Gunakan \n untuk ganti baris di dalam satu highlight."
  ],
  "qa": [
    { "q": "Pertanyaan", "a": "Jawaban" }
  ],
  "source": "Sumber / PIC"
}
```

- `id`: huruf kecil tanpa spasi, harus unik. Dipakai untuk tautan langsung, mis. `.../#tei`.
- `art` (gambar): `expo`, `campus`, `ship`, `scale`, `shield`, `globe`, `local`, `chart`, `doc`.
- `tone` (warna aksen): `lilac`, `blue`, `sand`, `sage`, `rose`, `teal`, `butter`.
- Urutan program di aplikasi mengikuti urutan di file.
- Perhatikan tanda koma antar-item dan tanda kutip. Jika format salah, aplikasi menampilkan pesan "Data tidak bisa dimuat".

## Menjalankan aplikasi

**GitHub Pages:** Settings → Pages → Source: *Deploy from a branch* → pilih branch `main` dan folder `/ (root)`. Aplikasi akan tersedia di `https://<username>.github.io/<nama-repo>/`.

**Di komputer sendiri:** aplikasi perlu dibuka lewat server lokal, karena browser memblokir pembacaan file JSON jika `index.html` diklik dua kali.

```bash
python -m http.server 8000
```

Lalu buka `http://localhost:8000`.
