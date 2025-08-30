# 📂 Uploader

Uploader adalah salah satu tools sederhana yang digunakan untuk mengunggah file melalui **GitHub**.  
Dengan repo ini, kamu bisa memanfaatkan GitHub sebagai media penyimpanan file, baik untuk kebutuhan bot, aplikasi, maupun project pribadi.

---

## ✨ Fitur
- 🚀 Upload file langsung ke repository GitHub
- 📦 Simpan file dengan aman di repo
- ⚡️ Ringan dan mudah digunakan
- 🔗 Dapat diintegrasikan dengan bot atau project lain

---

## 🔑 Cara Generate GitHub Personal Access Token (Classic)

Ikuti langkah-langkah berikut untuk membuat token:

1. Login ke akun GitHub kamu  
2. Klik foto profil kanan atas → **Settings**  
3. Scroll ke bawah → klik **Developer settings**  
4. Pilih menu **Personal access tokens** → **Tokens (classic)**  
5. Klik **Generate new token (classic)**  
6. Isi **Note** (misalnya: `Uploader Access`)  
7. Pilih **Expiration** (misalnya: 30 days, 90 days, atau No expiration)  
8. Centang scope berikut:
   - ✅ `repo` → full control of private repositories  
   - (opsional) `workflow` jika ingin digunakan untuk GitHub Actions  
9. Klik **Generate token**  
10. Salin token yang muncul → gunakan di perintah `git clone`  

⚠️ **Catatan:**  
- Token hanya ditampilkan sekali, jadi simpan dengan aman.  
- Jangan pernah commit atau share token di repo publik.  

---

## 📖 Tutorial (JavaScript)

Berikut contoh fungsi untuk mengunggah file ke GitHub menggunakan **Axios**:

```javascript
const axios = require('axios');
const fileType = require('file-type');

async function uploadToGithub(media) {
  try {
    const owner = 'rhnxofficial'; // Nama pemilik repositori
    const repo = 'Uploader';      // Nama repositori
    const branch = 'main';

    const fileInfo = await fileType.fromBuffer(media);
    const ext = fileInfo ? fileInfo.ext : 'bin'; // Default ke 'bin' jika tidak ada ekstensi
    const fileName = `${Date.now()}.${ext}`;
    const filePath = `uploader/${fileName}`;

    // Mengonversi konten file menjadi Base64
    const base64Content = Buffer.from(media).toString('base64');

    // Mengunggah file ke GitHub
    const githubResponse = await axios.put(
      `https://api.github.com/repos/${owner}/${repo}/contents/${filePath}`,
      {
        message: `Upload file ${fileName}`,
        content: base64Content,
        branch: branch,
      },
      {
        headers: {
          Authorization: `Bearer ${key.tokenGithub}`,
          'Content-Type': 'application/json',
        },
      }
    );

    // Mengembalikan URL file mentah
    return `https://raw.githubusercontent.com/${owner}/${repo}/${branch}/${filePath}`;
  } catch (error) {
    console.error('Error uploading to GitHub:', error.message);
    throw new Error('Gagal mengunggah file ke GitHub');
  }
}
```

---

## 📌 Catatan
- Gunakan **GitHub Token** dengan permission yang sesuai  
- Jangan membagikan token secara publik  
- Repo ini bisa dijadikan media penyimpanan file untuk berbagai kebutuhan  

---

## 🌐 Sosial Media
Terhubung dengan saya melalui:

[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?&style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/username)
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?&style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/username)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-%2325D366.svg?&style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/628xxxxxxxxxx)
[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?&style=for-the-badge&logo=facebook&logoColor=white)](https://facebook.com/username)
[![GitHub](https://img.shields.io/badge/GitHub-%23181717.svg?&style=for-the-badge&logo=github&logoColor=white)](https://github.com/username)

---

## 📊 GitHub Stats

![Stars](https://img.shields.io/github/stars/username/Uploader?style=for-the-badge)
![Forks](https://img.shields.io/github/forks/username/Uploader?style=for-the-badge)
![Issues](https://img.shields.io/github/issues/username/Uploader?style=for-the-badge)
![Contributors](https://img.shields.io/github/contributors/username/Uploader?style=for-the-badge)
![Repo Size](https://img.shields.io/github/repo-size/username/Uploader?style=for-the-badge)

---

## 📄 Lisensi
Repo ini dilisensikan di bawah [MIT License](LICENSE).
