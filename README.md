# Elixir Cards — Distillery

Gacha thẻ bài cocktail / spirits / lịch sử rượu. Web app (PWA) có thể cài như app trên Android.

## Cài trên Android (không cần APK)

1. Đưa repo lên GitHub và bật **GitHub Pages** (Settings → Pages → Deploy from branch `main` / folder `/root` hoặc `/docs`).
2. Mở link Pages bằng **Chrome** trên điện thoại Android, ví dụ:
   `https://<username>.github.io/elixir-cards/`
3. Menu Chrome (⋮) → **Cài đặt ứng dụng** / **Add to Home screen** / **Install app**.
4. Icon Elixir Cards xuất hiện trên màn hình chính, mở full-screen như app native.

> Cần HTTPS (GitHub Pages đã có). Sau lần cài đầu, app chạy offline nhờ service worker.

## Cấu trúc repo

```
elixir-cards/
├── index.html          # App chính
├── manifest.json       # PWA manifest
├── sw.js               # Service worker (offline)
├── icons/              # Icon đa kích thước + maskable
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── maskable-512.png
│   └── ...
└── README.md
```

## Upload lên GitHub

```bash
# Trong thư mục elixir-cards
git init
git add .
git commit -m "Elixir Cards Distillery — PWA"
git branch -M main
git remote add origin https://github.com/<USERNAME>/elixir-cards.git
git push -u origin main
```

Sau đó vào **Settings → Pages** chọn branch `main`, root, Save. Đợi 1–2 phút rồi mở URL Pages.

## (Tuỳ chọn) Build APK thật bằng Capacitor

Nếu bạn muốn file `.apk` cài được ngoài Play Store:

```bash
npm init -y
npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap init "Elixir Cards" com.elixir.cards --web-dir .
npx cap add android
npx cap sync
npx cap open android   # mở Android Studio → Build → Build APK
```

Cần Android Studio + JDK. Icon đã nằm trong `icons/`; copy `icons/icon-512.png` vào `android/app/src/main/res/...` nếu muốn.

## Ghi chú

- Dữ liệu (album, pity, essence…) lưu **localStorage** trên máy người dùng.
- Font Google (Montserrat, Playfair Display) cần mạng lần đầu; lần sau cache.
- Happy Hour (19–21h) và daily pull theo giờ máy.
