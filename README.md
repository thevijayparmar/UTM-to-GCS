# UTM-to-GCS
UTM Coordinate (Easting-Northing) converted to GCS Coordinates (Latitude-Longitude)
![UTM to GSC](https://github.com/user-attachments/assets/df1d803d-7f0d-487d-9400-6bc1447b9173)

# UTM → Lat/Lon (WGS84) — Single-File Converter 🌏

A lightweight, **single-HTML** tool to convert **UTM coordinates → Latitude/Longitude (WGS84)**.  
Supports **manual single-point** entry and **CSV batch** conversion, with **DD/DMS output**, **KML/CSV downloads**, a **Leaflet map preview**, and a **Dark/Light theme toggle**.

> Built for surveyors, GIS pros, and field teams who need a no-install, offline-friendly utility.

---

## ✨ Features

- **Two modes**:
  - 🔹 **Manual Entry**: Convert a single UTM point (Easting/Northing [+ optional Altitude])
  - 🔹 **CSV Upload**: Convert multiple points at once
- **Output format**:  
  - 📐 **Decimal Degrees (DD)** or **Degrees-Minutes-Seconds (DMS)**
- **Map preview** (Leaflet + OpenStreetMap) with auto-zoom to results
- **Downloads**:
  - 📥 **Converted CSV** (uses displayed format)
  - 🌐 **KML** (always uses numeric lat/lon for accuracy)
- **Theme toggle**: ☀️ / 🌙 (persists via localStorage)
- **Single file**: No build tools, no extra assets — just open the HTML
- **Credit badge**: `(C) Vijay Parmar` shown at bottom-right

---

## 📦 File

- `UTM to Coordinates R6.0.html` (single HTML file)

Open it directly in your browser (double-click). Works on Chrome/Edge/Firefox.

> 📝 If the map doesn’t load (offline), conversion and downloads still work.

---

## 🚀 Quick Start

1. **Download** the HTML file to your computer.
2. **Open** it in your browser (double-click).
3. Set **UTM Zone** (1–60) and **Hemisphere** (N/S).
4. Choose **output format** (DD or DMS).
5. Use either:
   - **Manual Entry** → fill Easting/Northing (meters) → **Convert Single**  
     or **Add Point** to append into the current results table.
   - **CSV Upload** → map columns → **Convert All**
6. **Download** results as CSV/KML or inspect on the **map preview**.

---

## 🧾 CSV Format

Minimum required columns:
- `Easting` (meters)
- `Northing` (meters)

Optional columns (auto-detected if present):
- `Sr No`, `Name`, `Altitude`

> You’ll map the actual column names in the **Column Mapping** selector.

**Example (`sample.csv`):**
```csv
Sr No,Name,Easting,Northing,Altitude
1,TP-01,238456.12,2401234.56,22.5
2,TP-02,238789.45,2401456.78,23
```

---

## 🗺️ Map & Offline Notes

- The map uses **Leaflet** with **OpenStreetMap** tiles from a public CDN.
- If **offline**, the map preview shows an info message — conversion + downloads still work.
- When online, please keep the OSM attribution visible.

---

## 🧠 Accuracy & Assumptions

- Datum: **WGS84**
- Projection: **UTM (Transverse Mercator)**
- Uses standard UTM formulas to compute geographic coordinates.
- **Important**: You must select the **correct Zone** and **Hemisphere** for accurate results.

---

## 🧩 Troubleshooting

- **“Nothing happens on Convert”**
  - Manual: Ensure **Easting/Northing** are numbers (meters), Zone 1–60, Hemisphere N/S.
  - CSV: Confirm a file is selected and **Easting/Northing** are correctly mapped.
- **Lat/Lon do not look right for India**
  - For Bhavnagar area, latitude ≈ **21°**, longitude ≈ **72°**  
  - Check: **Zone = 43**, **Hemisphere = Northern (N)**  
  - Verify you didn’t swap **Easting ↔ Northing**.
- **Decimals/Commas**
  - Use `.` as decimal separator and avoid thousand separators (e.g., `2401234.56`, not `2,401,234.56`).

---

## 🔒 Privacy

- Everything runs **locally in your browser**.
- No data is uploaded anywhere.
- Only map tiles are fetched when you’re online.

---

## 🧰 Tech Stack

- Vanilla **HTML/CSS/JS**
- **Leaflet** (CDN) for map preview
- Custom CSV parser (no dependencies)

---

## 🌐 Host on GitHub Pages (optional)

1. Create a new repo and **upload** `UTM to Coordinates R6.0.html`.
2. Go to **Settings → Pages**.
3. Set **Source**: `Deploy from a branch`, select the default branch root.
4. Click **Save** — GitHub will give you a public URL to share.

> Tip: Rename the file to `index.html` to make it the default page.

---

## 📋 Changelog

- **R6.0**
  - ✅ Manual single-point conversion (Add/Convert)
  - ✅ Shared DD/DMS output for both modes
  - ✅ Unified results table + KML/CSV downloads
  - ✅ Theme toggle + stored preference
  - ✅ Map preview improvements
  - ✅ Inline troubleshooting & UX polish

---

## 🙌 Credits

- Tool by **Vijay Parmar** — credit badge included in the UI.
- Map tiles © **OpenStreetMap** contributors.

---

## 📄 License

This project is open-source under the **MIT License**.  
Feel free to use, modify, and share. (Update the license if you prefer a different one.)

---

## 💬 FAQ

**Q: Can I mix manual and CSV results?**  
Yes. Use **Add Point** in manual mode to append rows to the current results (from CSV or manual).

**Q: Why does the KML download use numeric lat/lon even if I selected DMS?**  
KML requires numeric coordinates. The **CSV** download mirrors your display format; **KML** always uses numeric values internally.

**Q: Does it work completely offline?**  
Yes—conversion and downloads work offline. Only map tiles need internet.

---

### 🧑‍💻 Contributing
Issues and PRs are welcome. If you improve formulas, add projections, or extend the UI, please include a short note in the README and the changelog.

