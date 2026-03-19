Here is a short description for your GitHub repository, followed by a comprehensive `README.md` file based on the functionality of your code.

### GitHub Repository Description

> A 100% client-side tool that parses JSON files, detects external image URLs, downloads and converts them to WebP, rewrites the JSON paths to local assets, and packages everything into a downloadable ZIP file. Zero backend required\!

-----

### README.md

````markdown
# 📦 JSON Image Asset Packager

A lightweight, 100% client-side web application designed to help developers and content managers localize remote image assets. 

Simply upload a `data.json` file containing external image URLs. The tool will automatically parse the file, download the images, optionally convert them to WebP to save space, cleverly rename them based on JSON context, update the JSON paths to point to the new local files, and package everything into a neat `.zip` archive.

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)

## ✨ Features

- **🔒 100% Client-Side:** Everything happens in your browser. No data or images are ever uploaded to a backend server, ensuring complete privacy and zero server costs.
- **🕵️ Smart URL Detection:** Automatically identifies image URLs based on key names (e.g., `image`, `logourl`, `src`) or file extensions and known domains within generic keys.
- **🗜️ Auto WebP Compression:** Optionally converts downloaded images (JPEG/PNG) to WebP format at 85% quality to drastically reduce asset size. (Automatically skips SVGs and GIFs to preserve animations).
- **🧠 Intelligent Renaming:** Instead of random hashes, it looks at sibling keys in your JSON (like `name`, `title`, or `caption`) to generate descriptive, SEO-friendly filenames (e.g., `product-name.webp`).
- **🛡️ CORS Proxy Fallbacks:** If direct image fetching is blocked by CORS, the tool automatically falls back to reliable public CORS proxies to ensure your assets are downloaded.
- **✂️ Deduplication:** If the same image URL appears multiple times in your JSON, it is only downloaded once. All references are updated to point to the single local file.
- **📊 Real-time UI:** Features a modern drag-and-drop interface, a live progress bar, and a real-time logging terminal so you can see exactly what is being processed.

## 🚀 How It Works (Before & After)

The tool mutates your JSON to replace external links with local relative paths, while preserving the original URL in a new tracking key.

**Before (`data.json`):**
```json
{
  "product": {
    "name": "Super Widget",
    "image_url": "[https://example.com/uploads/12345-raw-image.jpg](https://example.com/uploads/12345-raw-image.jpg)"
  }
}
````

**After (Inside `packaged_assets.zip`):**

```json
{
  "product": {
    "name": "Super Widget",
    "image_url_originalsourceurl": "[https://example.com/uploads/12345-raw-image.jpg](https://example.com/uploads/12345-raw-image.jpg)",
    "image_url": "assets/images/super-widget.webp"
  }
}
```

*Note how the file was intelligently renamed to `super-widget.webp` based on the `name` key\!*

## 🛠️ Usage / Installation

Because this tool relies entirely on client-side browser APIs, there is **no build step or installation required.**

1.  Clone or download this repository.
2.  Open `index.html` directly in any modern web browser.
3.  Drag and drop your `data.json` file into the upload zone.
4.  Wait for the processing to finish.
5.  Click **Download ZIP**.

The downloaded ZIP will contain:

  * `data.json` (Your updated JSON file)
  * `assets/images/` (A folder containing all your localized, optimized images)

## 📦 Dependencies

This project uses the following libraries via CDN (no NPM required):

  * [Tailwind CSS](https://tailwindcss.com/) - For rapid UI styling.
  * [JSZip](https://stuk.github.io/jszip/) - For generating the ZIP archive in the browser.
  * [FileSaver.js](https://www.google.com/search?q=https://github.com/eligrey/FileSaver.js) - For triggering the final file download.
  * [FontAwesome](https://fontawesome.com/) - For UI icons.

## ⚠️ Limitations & Notes

  * **Memory Limits:** Because everything is processed in the browser's RAM, attempting to package massive JSON files with thousands of high-resolution images might crash the browser tab.
  * **CORS Restrictions:** While the app includes multiple proxy fallbacks (`allorigins.win`, `codetabs`, `corsproxy.io`), highly secure image hosts that block all proxies may still fail to download. The app handles this gracefully by logging an error and keeping the original URL intact in the JSON.

## 📄 License

This project is open-source and available under the [MIT License](https://www.google.com/search?q=LICENSE).

```
```
