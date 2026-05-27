# TikTok Callback Relay

Static callback page untuk TikTok Login Kit ketika TikTok Developer Portal meminta URL property verification.

Deploy folder ini ke GitHub Pages. Setelah deploy, pakai URL:

```text
https://USERNAME.github.io/REPOSITORY/auth/tiktok/callback
```

sebagai TikTok Redirect URI dan sebagai TikTok URL Prefix property.

## GitHub Pages setup

1. Buat repo publik baru di GitHub, misalnya `ae-social-tiktok-callback`.
2. Upload seluruh isi folder ini ke repo tersebut.
3. Buka `Settings > Pages`.
4. Pilih `Deploy from a branch`.
5. Branch: `main`.
6. Folder: `/ (root)`.
7. Save.
8. Tunggu Pages aktif.

Jika repo bernama `ae-social-tiktok-callback` dan username GitHub kamu `yourname`, callback URL-nya:

```text
https://yourname.github.io/ae-social-tiktok-callback/auth/tiktok/callback
```

TikTok URL prefix property:

```text
https://yourname.github.io/ae-social-tiktok-callback/
```

Kalau TikTok memberi signature verification file, taruh file itu di root folder ini, commit, push, lalu klik verify lagi di TikTok Developer Portal.

Flow:

1. TikTok mengirim OAuth `code` dan `state` ke URL HTTPS static site.
2. `auth/tiktok/callback/index.html` langsung forward browser ke helper lokal:

```text
http://127.0.0.1:47831/auth/tiktok/callback
```

3. Helper lokal menukar code menjadi access token.

Catatan:

- Ini hanya menyelesaikan masalah URL verification/HTTPS redirect.
- Ini tidak memberi akses `video.publish` kalau TikTok belum approve Direct Post.
- Dengan scope `video.upload`, output TikTok tetap draft/inbox upload.
