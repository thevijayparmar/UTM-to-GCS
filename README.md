# UTM-to-GCS
UTM Coordinate (Easting-Northing) converted to GCS Coordinates (Latitude-Longitude)
![UTM to GSC 2](https://github.com/user-attachments/assets/432f6fdb-90f0-41a0-8155-63016b5219a1)


# UTM ⇄ Lat/Lon (WGS84) — Two-Way Converter 🌏

A modern, **single-file HTML** app that converts **UTM ↔ Latitude/Longitude (WGS84)**.  
Includes manual & CSV modes, **map search + click** to auto-detect **UTM Zone & Hemisphere**, **orange result markers** on a Leaflet map, **DD/DMS output**, **CSV/KML downloads**, **dark/light theme**, and a subtle **moving ocean** background (10% visibility).

> Built for surveyors, GIS teams, and field engineers who need a fast, offline-friendly utility with zero install.

---

## ✨ Features

- **Two-way conversion**
  - 🔹 **UTM → Lat/Lon** (WGS84)
  - 🔹 **Lat/Lon → UTM** (WGS84)
- **Manual single-point** conversion + **CSV batch** conversion (shared output table)
- **Map helpers**
  - 🧭 **Click map**: set zone/hemisphere automatically (optional)
  - 🔎 **Search places** (OpenStreetMap Nominatim) → auto-fills Zone & Hemisphere
  - 🟠 **Orange markers** drawn for all converted results (manual & CSV) with popups
- **Flexible output**:
  - 📐 **Decimal Degrees (DD)** or **Degrees-Minutes-Seconds (DMS)**
- **Downloads**:
  - 📥 **CSV** (mirrors your chosen display format)
  - 🌐 **KML** (always numeric lat/lon for compatibility)
- **UI & Theme**: Minimal, responsive layout with **Dark/Light** toggle (saved to `localStorage`)
- **Single file**: All CSS/JS inline; just open the HTML
- **Dynamic background**: Subtle “moving ocean” (~10% opacity) for a modern look
- **Credit badge**: `(C) Vijay Parmar` at bottom-right

---

## 📦 File

- `UTM-GCS-TwoWay.html` (or your chosen name)

Open it directly in your browser. Works on Chrome/Edge/Firefox.

> 📝 If the map or search is offline, conversion and downloads still work.

---

## 🚀 Quick Start

### Local
1. Download `UTM-GCS-TwoWay.html`.
2. Double-click to open in your browser.
3. Pick **Conversion Mode** (UTM→GCS or GCS→UTM).
4. Choose **DD** or **DMS**.
5. Use either:
   - **Manual Entry** → fill required fields → **Convert Single** (or **Add Point** to append)
   - **CSV Upload** → map columns → **Convert All**
6. See results in the **table** and **map** (orange markers). Download CSV/KML.

### GitHub Pages (for sharing or WordPress embed)
1. Push your HTML file to a **public** GitHub repo at the **root**.
2. Repo **Settings → Pages** → Source: `main` / `/ (root)` → **Save**.
3. Your page will be at:  
   `https://<username>.github.io/<repo>/UTM-GCS-TwoWay.html`
4. **WordPress embed** (Custom HTML block):
   ```html
   <iframe src="https://<username>.github.io/<repo>/UTM-GCS-TwoWay.html"
           style="width:100%; height:900px; border:none;"
           title="UTM ⇄ Lat/Lon Converter"></iframe>
   ```
> Using an `<iframe>` keeps code intact and avoids WP script filters.

---

## 🧾 CSV Format & Column Mapping

The tool supports **both modes**. After selecting a mode, map the columns accordingly.

### UTM → Lat/Lon
**Required:** `Easting`, `Northing`  
**Optional:** `Sr No`, `Name`, `Altitude`

Example:
```csv
Sr No,Name,Easting,Northing,Altitude
1,TP-01,238456.12,2401234.56,22.5
2,TP-02,238789.45,2401456.78,23
```

### Lat/Lon → UTM
**Required:** `Latitude`, `Longitude`  
**Optional:** `Sr No`, `Name`, `Altitude`

Example:
```csv
Sr No,Name,Latitude,Longitude,Altitude
1,TP-01,21.7612,72.1534,22.5
2,TP-02,21.7701,72.1108,23
```

> Tip: The **Column Mapping** area auto-suggests common names. You can use any headers — just map them correctly.

---

## 🗺️ Map, Zone & Hemisphere

- **Auto-detect Zone & Hemisphere** when you **click the map** or use **Search** (toggle is on by default).
- **Zone** is computed with the standard rule:  
  `zone = floor((longitude + 180) / 6) + 1`  
  (Note: Norway/Svalbard exceptions are **not** applied in this simple rule.)
- **Hemisphere** is: `N` if `latitude ≥ 0`, else `S`.

You can override auto values by unchecking **“Auto detect from map/search”** and setting Zone/Hemisphere manually.

---

## 🟠 Orange Markers (Map Output)

- Every **converted row** (manual or CSV) gets an **orange circle marker** with a popup (Lat/Lon + label).
- **Clear Results** removes the orange layer without altering the base map or your picked-location marker.

**Customize (optional):**
```js
const ORANGE_STYLE = {
  radius: 7,          // marker size
  color: '#ff8c00',   // stroke
  fillColor: '#ff8c00',
  fillOpacity: 0.9,
  weight: 2           // stroke width
};
```

---

## 🧠 Accuracy & Assumptions

- Datum: **WGS84**
- Projection: **UTM (Transverse Mercator)**
- UTM ⇄ GCS formulas implemented in pure JS (standard approach)
- **UTM Zone** computed by the standard 6-degree rule (no Norway/Svalbard exceptions)
- **KML** always uses **numeric** coordinates regardless of DD/DMS display
- Input validation:
  - Lat: `−90 … 90`
  - Lon: `−180 … 180`
  - Zone: `1 … 60`

> Always verify Zone/Hemisphere for your region. If results look far off, swap Easting/Northing or double-check the zone.

---

## 🔒 Privacy & Offline Behavior

- All conversions run **locally** in the browser.
- **No data** is uploaded to a server by this tool.
- The map uses **OpenStreetMap tiles** from a public CDN; **Search** uses **Nominatim**. These require internet access.  
  Conversions and downloads still work offline.

---

## 🧰 Tech Stack

- **HTML/CSS/JavaScript** (vanilla, single file)
- **Leaflet** (CDN) for the map
- **OpenStreetMap** tiles
- **Nominatim** for geocoding (search)

---

## ❗ Troubleshooting

- **Nothing happens on Convert**
  - Manual: Ensure required fields are filled with numeric values.
  - CSV: Make sure a file is selected and columns are mapped.
- **Results look wrong for my area**
  - Check **Zone & Hemisphere**. For *Bhavnagar, India*, typical is **Zone 43N** with lat ≈ **21°**, lon ≈ **72°**.
  - Verify you didn’t swap **Easting ↔ Northing**.
- **Map/Search not working**
  - Check internet connection or CDN availability. Conversions still work offline.
- **WordPress won’t run the HTML**
  - Use the **GitHub Pages + `<iframe>`** method shown above.

---

## 🗺️ UI Notes

- **Dynamic ocean background** is ~10% opacity and blurred for subtlety.
- **Dark/Light** theme is remembered via `localStorage`.
- Responsive layout: panels stack on small screens.

---

## 🔧 Advanced / Extensibility

- Add more outputs (GeoJSON, GPX) by generating files from `lastResults`.
- Implement Norway/Svalbard UTM zone exceptions if needed.
- Swap base tiles by changing the Leaflet `tileLayer` URL.

---

## 📋 Changelog

- **R7.0**
  - Two-way **UTM ↔ GCS** conversion
  - **Map search + click** → auto-detect **Zone & Hemisphere**
  - **Orange markers** for converted results (manual + CSV)
  - KML/CSV downloads unified, UI polish, bug fixes
  - Moving ocean background (~10%)
- **R6.0**
  - Manual UTM single-point mode, unified table and downloads, theme toggle, initial Leaflet preview

---

## 🙌 Credits

- Tool by **Vijay Parmar** — credit badge in the UI.
- Map data © **OpenStreetMap** contributors.

---

## 📄 License

This project is open-source under the **MIT License**.
