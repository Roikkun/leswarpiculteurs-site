# Les Warpiculteurs

Static website for **Les Warpiculteurs**, a tabletop wargaming association based in Villemomble (93), France.

---

## Customizable Images by Section

All website images are located in the `img/` directory (with the site favicon located at the root). You can replace any of these files to update the visuals on the website without modifying `index.html`.

> **Note on Case Sensitivity:** GitHub Pages runs on Linux environments where file names are **case-sensitive**. Always keep filenames in lowercase kebab-case (e.g., `warpi-planning.png` rather than `Warpi_planning.png`) to avoid broken images after deployment.

---

### 1. Header & Social Media Preview

* **Header Hero Banner & Social Card:** `img/header.png`
  * **Location:** Top hero banner background on the homepage, as well as preview thumbnail for social shares (Open Graph / Discord / Facebook / Twitter Card / Schema.org metadata).
  * **Recommended Dimensions:** `1920 × 1080 px` or `1200 × 630 px` (16:9 standard landscape).
  * **Format:** PNG.
  * **Tip:** The hero section has a semi-transparent dark gradient overlay on the left side to ensure text readability. Choose a high-contrast, landscape-oriented image showcasing the club atmosphere or miniatures.

---

### 2. Section: "L'association" (`#asso`)

These images appear in the 4 alternating presentation cards in the association overview section. Images are displayed with `object-fit: cover` and automatically adapt to screen width.

| Card Title | Image Path | Description / Role | Recommended Dimensions |
| :--- | :--- | :--- | :--- |
| **Nos jeux** | `img/our-games.png` | Illustrates games played (Warhammer 40K, AoS, Warcry, etc.) | `800 × 600 px` (4:3) or landscape |
| **La salle & matériel** | `img/room-and-equipment.png` | Illustrates the venue, gaming tables, scenery, and terrain | `800 × 600 px` (4:3) or landscape |
| **Animations** | `img/animations.png` | Illustrates painting workshops, narrative events, and leagues | `800 × 600 px` (4:3) or landscape |
| **Compétition** | `img/competition.png` | Illustrates the association's competitive teams and tournaments | `800 × 600 px` (4:3) or landscape |

* **Format:** PNG.
* **Tip:** Keep key subjects centered so they remain visible across desktop and mobile screen sizes.

---

### 3. Section: "Horaires & accès" (`#accesHoraires`)

* **Event Calendar / Planning:** `img/warpi-planning.png`
  * **Location:** Displayed in the schedule section and opens in full size when clicked by visitors.
  * **Recommended Dimensions:** `1200 × 800 px` to `1920 × 1080 px` (landscape).
  * **Format:** PNG (preferred for crisp text and calendar legibility).
  * **Tip:** Ensure text and dates remain clearly legible when scaled down on smaller screens.

---

### 4. Section: "Comment venir jouer avec nous ?" (`#jouerAvecNous`)

These images appear as circular avatar icons (vignettes) next to each step in the onboarding timeline.

| Step | Image Path | Description / Role | Recommended Dimensions |
| :--- | :--- | :--- | :--- |
| **1. Rejoins-nous sur Discord** | `img/join-discord.png` | Visual for joining the Discord server | `300 × 300 px` (1:1 square) |
| **2. Trouve un adversaire** | `img/find-opponent.png` | Visual for finding gaming partners | `300 × 300 px` (1:1 square) |
| **3. Retrouve-nous à l'association** | `img/come-play.png` | Visual for visiting the venue in person | `300 × 300 px` (1:1 square) |
| **4. Deviens adhérent** | `img/become-a-member.png` | Visual for membership perks | `300 × 300 px` (1:1 square) |

* **Format:** PNG with transparent background.
* **Tip:** Images are styled with `border-radius: 50%` (circular mask). Center the main subject within a square frame so important details are not clipped by the circular boundary.

---

### 5. Site Identity & Favicon

* **Brand Favicon & Icon:** `favicon.svg`
  * **Location:** Browser tab icon, mobile bookmarks (`apple-touch-icon`), and Schema.org logo.
  * **Format:** Scalable Vector Graphics (SVG).
  * **Tip:** Retains crisp sharpness across all device resolutions.

---

## How to Update Images

### Option A: Via GitHub Web Interface (Easiest)

1. In the GitHub repository, navigate to the `img/` folder.
2. Click on the image file you wish to update (e.g. `img/warpi-planning.png`).
3. Click the **...** menu (top right of file view) and choose **Replace file** (or click **Add file** > **Upload files** from the folder view with the exact same filename).
4. Upload your new file and commit the changes to `main`.
5. GitHub Actions will automatically rebuild and deploy the update to GitHub Pages within 1–2 minutes.

### Option B: Via Git Command Line

1. Overwrite the file in the `img/` directory with your new image (ensuring the filename matches exactly).
2. Stage, commit, and push:
   ```bash
   git add img/warpi-planning.png
   git commit -m "Update event calendar"
   git push origin main
   ```

---

## Image Optimization Best Practices

To keep page load speeds fast for mobile users and reduce bandwidth:
- **Compress Images:** Use tools like [TinyPNG](https://tinypng.com/) or [Squoosh](https://squoosh.app/) before uploading.
- **Keep File Sizes Reasonable:** Aim for `< 300 KB` per card image and `< 800 KB` for the calendar/header banner.
- **Maintain Exact File Names:** If you replace an image with a different extension (e.g. `.jpg` instead of `.png`), you must also update the corresponding `src` in `index.html` or `styles.css`.

---

## Local Development & Preview

Because this is a static site (HTML/CSS), you can preview changes locally with any static web server:

### Using Python
```bash
python -m http.server 8000
```
Then open `http://localhost:8000` in your browser.

### Using Node.js / npx
```bash
npx serve .
```

### Using VS Code / PhpStorm
- **PhpStorm:** Right-click `index.html` > **Open in** > **Browser**.
- **VS Code:** Use the **Live Server** extension.

---

## Deployment

The website is hosted on **GitHub Pages**. Any commit pushed to the `main` branch automatically triggers the deployment workflow located at `.github/workflows/pages.yml`.
