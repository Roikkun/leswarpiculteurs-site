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

* **Header Brand Logo:** `img/logo.png`
  * **Location:** Navigation bar brand logo on the top-left of the homepage.
  * **Format:** PNG with transparent background (rendered within a round background frame).
* **Brand Favicon & Icon:** `img/logo-with-bg.png`
  * **Location:** Browser tab icon, mobile bookmarks (`apple-touch-icon`), and Schema.org logo.
  * **Format:** PNG.

---

## ⚠️ Before publishing: fill in the legal placeholders

`mentions-legales.html` contains three facts that only the association can supply. They are highlighted
in yellow on the rendered page (`<span class="todo">`) so they are impossible to miss:

| Placeholder | What to put |
| :--- | :--- |
| Téléphone | A contact phone number for the association |
| Numéro RNA | The `W________` number on the préfecture declaration receipt |
| Directeur de la publication | First and last name of the president (legal representative) |

Find them with `grep -n 'class="todo"' mentions-legales.html`, then delete the `<span class="todo">…</span>`
wrapper along with the placeholder text.

> The LCEN (art. 6 III-1) requires a legal person publishing a website to disclose its name, registered
> address, phone number, publication director and host. These pages were drafted to meet that baseline
> plus RGPD art. 13 information duties — **they are not legal advice.** Have a board member read them
> before going live.

---

## Site Pages

| File | Indexed? | Role |
| :--- | :--- | :--- |
| `index.html` | Yes | Single-page site (all sections) |
| `mentions-legales.html` | Yes | Legal notice — LCEN art. 6 III-1 |
| `confidentialite.html` | Yes | Privacy policy — RGPD art. 13 |
| `merci.html` | No (`noindex`) | Confirmation shown after the contact form is submitted |

All pages share `styles.css` and the same footer. `merci.html` is deliberately excluded from
`sitemap.xml` because it is a post-submission destination, not a landing page.

### Contact form

The form posts to [FormSubmit](https://formsubmit.co/) and its `_next` hidden field redirects to
`merci.html`. **Both `_next` and the `rel=canonical` / `og:url` tags hardcode the absolute site URL**
(`https://roikkun.github.io/leswarpiculteurs-site/`). If the site ever moves to a custom domain, update:

```bash
grep -rn "roikkun.github.io" . --include=*.html --include=*.xml --include=*.txt
```

> FormSubmit requires a one-time activation: the first submission triggers a confirmation e-mail to
> `leswarpiculteurs@gmail.com` that must be clicked before messages start arriving.

### External action links

| Link | Where it lives |
| :--- | :--- |
| HelloAsso membership | Step 4 of `#jouerAvecNous` (`.step-link-join`) — renew the URL each season |
| Discord invite | See the section below |

---

## Discord Invite Link

Discord is presented as the association's primary information channel, so the invite URL
(`https://discord.gg/ApjmxBuTHG`) is intentionally repeated across several entry points in `index.html`:

| Entry point | Role |
| :--- | :--- |
| `Schema.org` `sameAs` (in `<head>`) | Declares the server to search engines |
| Navigation bar (`.nav-discord`) | Always-visible button; collapses to a circular icon on mobile, outside the burger menu |
| Hero primary call to action (`.hero-link-discord`) | Main action above the fold |
| Discord banner (`#discord`) | Dedicated "everything happens on Discord" section |
| Step 1 of `#jouerAvecNous` (`.step-link`) | Invite inside the onboarding timeline |
| Contact hint (`.contact-hint`) | Points visitors to Discord instead of the form for quick answers |
| Social icons list (`.wrapper .icon.discord`) | Footer-style social link |

> **If the invite ever changes,** replace **every** occurrence — a stale link in one spot is easy to miss.
> Find them all with `grep -n "discord.gg" index.html` (7 occurrences as of the last update).
> Prefer a permanent (non-expiring) invite so the site never points at a dead link.

The Discord brand colour is defined once in `styles.css` as the `--discord-blurple` /
`--discord-blurple-dark` custom properties.

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
