
# 🧩 Lottie Sticker Builder (WAS) — Create Animated WhatsApp Stickers  
**by Silent Tech**  

[![Beta](https://img.shields.io/badge/status-beta-orange)](https://github.com/Pedrozz13755/Lottie-Whatsapp)
[![Node.js](https://img.shields.io/badge/node-%3E%3D14-green)](https://nodejs.org)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

> Convert any image (PNG, JPG, WEBP) into a ready‑to‑send **animated WhatsApp sticker** (`.was` Lottie format) in seconds.  
> Perfect for bots, automation, and custom sticker packs.

---

## 🚀 Why This Tool?

- **Instant Conversion** – Turn a single image into a looping `.was` sticker.
- **Baileys Ready** – Works out‑of‑the‑box with WhatsApp bots.
- **Lightweight** – Zero external Node dependencies.
- **Silent Tech Quality** – Built for performance and reliability.

---

## 📥 Installation

### 1. Clone the repository


git clone https://github.com/silent-tech-offc/Lottie-Whatsapp-stickers.git
cd Lottie-Whatsapp-stickers


2. Install system dependency (zip)

This tool requires the zip command to package the final .was file.


# Termux / Debian / Ubuntu
pkg install zip   # or apt install zip


---

📁 Expected Folder Structure


src/
 └── exemple/
      └── animation/
           └── animation_secondary.json   # Lottie JSON with base64 placeholder


The JSON must already contain a base64 image – the builder replaces it with your own image.

---

🛠️ Usage

Basic Example


const path = require("path");
const { buildLottieSticker } = require("./src/index");

const output = await buildLottieSticker({
  baseFolder: path.resolve(__dirname, "src", "exemple"),
  buffer: imageBuffer,        // Buffer from file or download
  mime: "image/jpeg",
  output: path.resolve(__dirname, "my-sticker.was")
});


Send with Baileys (WhatsApp Bot)


await client.sendMessage(chatId, {
  sticker: fs.readFileSync("./my-sticker.was"),
  mimetype: "application/was"
});


---

🔧 Parameters

Parameter Type Required Description
baseFolder string ✅ Root folder of the Lottie animation
buffer Buffer ❌ Image data in memory
imagePath string ❌ File path to the image
mime string ❌ MIME type (e.g., image/png). Auto‑detected if imagePath is given
output string ❌ Destination path for the .was sticker
jsonRelativePath string ❌ Path to the JSON file relative to baseFolder

Note: You must supply either buffer or imagePath.

---

✅ Supported Input Formats

· PNG
· JPG / JPEG
· WEBP

---

⚠️ Common Errors & Fixes

Error Cause Solution
Mime not detected No MIME type provided Pass the mime option or use imagePath
JSON without assets Invalid Lottie structure Verify the JSON file has an assets array
No base64 image found Missing embedded placeholder Ensure your JSON contains a base64 image string
zip: command not found zip is not installed Install it with your package manager

---

💡 Pro Tip: Use with WhatsApp Message Buffer


const buffer = await getFileBuffer(message, "image");

const stickerPath = await buildLottieSticker({
  baseFolder: path.resolve(__dirname, "src", "exemple"),
  buffer,
  mime: "image/jpeg",
  output: path.resolve(__dirname, `sticker-${Date.now()}.was`)
});

---

🚧 Beta Notice

This project is in active development. Some Lottie structures may not be fully compatible yet.
Feedback and contributions are welcome!

---

👑 Credits & Community

Developed by Silent Tech
Maintained by Silent tech 

· 📢 WhatsApp Group: Join Community
· 📣 Channel: https://whatsapp.com/channel/0029VbB4gB0D38CKNsNzYE0n
· ⭐ Star the repo if you find it useful!

---

🔍 SEO Keywords (for discoverability)

WhatsApp animated sticker creator · Lottie to WAS converter · Node.js sticker builder · Baileys .was sticker · image to Lottie animation · create animated WhatsApp sticker · Silent Tech sticker tool · convert photo to .was · WhatsApp bot sticker generator

---

Footer

Made with ❤️ by Silent Tech
Beta Version – subject to changes and improvements.

