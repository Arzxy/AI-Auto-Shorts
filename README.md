# 🎬 AI Auto Shorts (Versi Lokal)

Sebuah tool otomatis berbasis AI untuk membuat konten video pendek viral (TikTok, Reels, YouTube Shorts) dari video YouTube secara lokal. Tool ini akan mengunduh video, melakukan transkripsi audio, mencari bagian paling menarik (hook), memotong video ke format vertikal 9:16 dengan pelacakan wajah, serta menambahkan subtitle dinamis ala konten Alex Hormozi.

---

## 🚀 Fitur

- **Pengunduh Video**  
  Mengunduh video YouTube secara otomatis dengan kualitas optimal.

- **Transkripsi AI**  
  Menggunakan Whisper (local) untuk konversi suara ke teks dengan timestamp per kata.

- **Analisis Hook Viral**  
  Memanfaatkan Groq (Llama 3.3 70B) untuk mendeteksi segmen paling menarik dalam video.

- **Auto Face Tracking**  
  Video otomatis dipotong ke format 9:16 sambil menjaga wajah pembicara tetap di tengah menggunakan MediaPipe.

- **Subtitle Dinamis**  
  Subtitle penuh warna dan bergaya modern seperti video Alex Hormozi.

- **Multi-Threading**  
  Proses rendering dipercepat dengan MoviePy dan OpenCV.

---

## 🛠️ Prasyarat

Sebelum menjalankan program, pastikan sudah menginstal:

1. **Python 3.8+**
2. **FFmpeg** – Dibutuhkan oleh MoviePy dan Whisper  
   👉 https://www.gyan.dev/ffmpeg/builds/
3. **ImageMagick** – Digunakan untuk fitur `TextClip` pada MoviePy  
   👉 https://imagemagick.org/script/download.php#windows  

   ⚠️ *Untuk pengguna Windows*:  
   Pastikan mencentang opsi **"Install legacy utilities (e.g. convert)"** saat instalasi.

4. **Groq API Key**  
   Dapatkan API key gratis melalui:  
   👉 https://console.groq.com/

---

## 📦 Instalasi

1. Clone repository:

```bash
git clone https://github.com/Arzxy/AI-Auto-Shorts.git
cd AI-Auto-Shorts
```

2. Install dependensi:

```bash
pip install -r requirements.txt
```

3. Buat file .env di root project dan isi dengan:

```bash
GROQ_API_KEY=your_groq_api_key_here
```

---

## 🖥️ Cara Penggunaan

1. Buka file main.py lalu atur konfigurasi berikut:

```bash
- YOUTUBE_URL → Link video YouTube yang ingin diproses
- JUMLAH_KLIP → Jumlah klip yang ingin dihasilkan
- FONT_TYPE → Pastikan font tersedia di sistem (default: Arial-Bold)
```

2. Jalankan program:

```bash
python main.py
```

3. Tunggu hingga proses selesai
Hasil video akan tersimpan di folder:

```bash
hasil_shorts
```

---

## ⚙️ Konfigurasi Subtitle

1. Kamu bisa mengatur ukuran, warna, dan posisi subtitle di dalam main.py:

```bash
FONT_SIZE = 70
FONT_COLOR = '#FFD700'  # Emas
FONT_COLOR_ALT = 'white'
POSISI_TEKS_Y = 0.75  # 75% tinggi video
```

---

## 📝 Troubleshooting

❗ Error ImageMagick
1. Jika MoviePy tidak menemukan ImageMagick, buka main.py lalu aktifkan dan sesuaikan path berikut:

```bash
change_settings({
    "IMAGEMAGICK_BINARY": r"C:\Program Files\ImageMagick-7.1.1-Q16-HDRI\magick.exe"
})
```
---

## ⚡ Whisper Tidak Menggunakan GPU

Program akan otomatis menggunakan CUDA (GPU) jika tersedia.
Jika tidak, maka akan berjalan menggunakan CPU.