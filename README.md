# 🎬 Video Caption Generator

Automatically transcribe and burn subtitles into videos using OpenAI Whisper — optimized for Indonesian language content. **100% free**, no API key needed.

## ✨ Features

- 🎙️ Auto-transcription using [stable-ts](https://github.com/jianfch/stable-ts) (enhanced Whisper)
- 🟡 Karaoke-style highlighting — active word turns yellow
- 📐 Dynamic subtitle sizing based on video resolution
- 🔥 Subtitles burned directly into output video via FFmpeg
- ⚡ Batch processing — drop multiple videos, get all outputs at once

## 📸 Demo

| Input | Output |
|-------|--------|
| Raw video (no subtitles) | Video with auto-generated burned-in captions |

## 🛠️ Setup

### 1. Siapkan folder di Google Drive

Buat struktur folder berikut di **MyDrive**:

```
MyDrive/
└── Whisper/
    ├── video/        ← taruh video input di sini
    ├── caption/      ← file .ass subtitle (auto-generated)
    └── output/       ← video hasil akhir dengan subtitle
```

> Folder `caption/` dan `output/` akan dibuat otomatis saat notebook dijalankan.

### 2. Masukkan video

Taruh video yang ingin ditambahkan caption ke folder `MyDrive/Whisper/video/`.

### 3. Buka notebook di Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

Upload file `GenerateCaption.ipynb` ke Google Colab.

### 4. Pilih runtime GPU

`Runtime → Change runtime type → T4 GPU` → Save

### 5. Jalankan notebook

`Runtime → Run all` — notebook akan otomatis:
- Install dependencies (`stable-ts`, `ffmpeg`)
- Mount Google Drive
- Proses semua video di folder `video/`
- Simpan hasil ke folder `output/`

### 6. Ambil hasil

Video dengan subtitle sudah tersedia di `MyDrive/Whisper/output/`.

> ⚠️ **Setelah selesai, matikan sesi Colab** via `Runtime → Disconnect and delete runtime` agar kuota GPU gratis tidak terpakai sia-sia.

## ⚙️ Configuration

At the top of the main cell, you can adjust:

```python
model = stable_whisper.load_model('medium')  # tiny / base / small / medium / large
language = 'id'                               # language code, e.g. 'en', 'id', 'ja'
```

| Model | Speed | Accuracy | VRAM |
|-------|-------|----------|------|
| `tiny` | Fastest | Low | ~1 GB |
| `base` | Fast | Medium | ~1 GB |
| `small` | Moderate | Good | ~2 GB |
| `medium` | Slow | Great | ~5 GB |
| `large` | Slowest | Best | ~10 GB |

> 💡 **100% Gratis** — menggunakan Google Colab free tier (GPU T4) dan Google Drive. Tidak perlu bayar apapun.

## 🧰 Tech Stack

- [OpenAI Whisper](https://github.com/openai/whisper) — speech-to-text model
- [stable-ts](https://github.com/jianfch/stable-ts) — word-level timestamp stabilization
- [FFmpeg](https://ffmpeg.org/) — video processing & subtitle burning
- Google Colab + Google Drive — cloud GPU runtime & storage

## 📄 License

MIT
