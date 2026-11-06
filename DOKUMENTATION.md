# Projektdokumentation: Juergen Giesen Garten- & Landschaftsbau

## Inhaltsverzeichnis

1. [Projektuebersicht](#1-projektuebersicht)
2. [Technologie-Stack](#2-technologie-stack)
3. [Projektstruktur](#3-projektstruktur)
4. [Seiten](#4-seiten)
5. [Komponenten](#5-komponenten)
6. [Daten & Inhalte](#6-daten--inhalte)
7. [Datenbank (Supabase)](#7-datenbank-supabase)
8. [SEO & Suchmaschinenoptimierung](#8-seo--suchmaschinenoptimierung)
9. [Barrierefreiheit (Accessibility)](#9-barrierefreiheit-accessibility)
10. [Design & Styling](#10-design--styling)
11. [Funktionen im Detail](#11-funktionen-im-detail)
12. [Oeffentliche Dateien (Public)](#12-oeffentliche-dateien-public)

---

## 1. Projektuebersicht

Dieses Projekt ist die vollstaendige Website fuer **Juergen Giesen Garten- und Landschaftsbau** in Alpen am Niederrhein. Es handelt sich um eine moderne, professionelle Marketing-Website mit folgenden Kernfunktionen:

- Unternehmensdarstellung mit Leistungen, Team und Referenzprojekten
- Kontaktformular mit Rueckrufwunsch-Funktion (Daten in Supabase)
- Ratgeber-Blog mit 10 Fachartikeln und Kategoriefilter
- Vorher/Nachher-Galerie mit Lightbox
- Kundenbewertungen als Karussell
- FAQ-Bereich mit Akkordeon
- WhatsApp-Kontakt-Button
- Newsletter-Anmeldung
- Interne Konkurrenzanalyse mit PDF-Export
- Vollstaendige SEO-Optimierung inkl. Schema.org, Sitemap, robots.txt
- DSGVO-konforme Seiten (Impressum, Datenschutz)

**Domain:** https://gartentraeume-giesen.de

---

## 2. Technologie-Stack

| Technologie | Version | Zweck |
|---|---|---|
| React | 18.3.1 | UI-Bibliothek (Komponentenbasiert) |
| TypeScript | 5.5.3 | Typsichere Entwicklung |
| Vite | 5.4.2 | Build-Tool und Entwicklungsserver |
| React Router DOM | 7.13.1 | Client-seitiges Routing (SPA) |
| Tailwind CSS | 3.4.1 | Utility-First CSS Framework |
| Supabase | 2.57.4 | PostgreSQL-Datenbank als Backend |
| Lucide React | 0.344.0 | SVG-Icon-Bibliothek |
| PostCSS | 8.4.35 | CSS-Transformations-Pipeline |
| Autoprefixer | 10.4.18 | Browser-Vendor-Prefixes |
| ESLint | 9.9.1 | Code-Qualitaetspruefung |

### Schriftarten (Google Fonts)
- **Playfair Display** (700, 900) -- Ueberschriften (Serif, elegant)
- **DM Sans** (300, 400, 500, 600) -- Fliesstext (Sans-Serif, modern)

---

## 3. Projektstruktur

```
project/
├── public/                          # Statische Dateien (Bilder, SEO-Dateien)
│   ├── Logo_Giesen.png             # Firmenlogo
│   ├── JuergenGiesen_(1).jpg       # Portraitfoto
│   ├── Landschaftsbaugiesen*.jpg   # 25 Projektfotos
│   ├── Nutursteinmauervorher.jpg   # Vorher-Foto Natursteinmauer
│   ├── Nutursteinmauernachher.jpg  # Nachher-Foto Natursteinmauer
│   ├── robots.txt                  # Suchmaschinen-Steuerung
│   ├── sitemap.xml                 # XML-Sitemap (16 URLs)
│   ├── llms.txt                    # LLM/KI-Crawler-Information
│   └── manifest.json               # PWA-Manifest
│
├── src/
│   ├── App.tsx                     # Haupt-App mit Routing
│   ├── main.tsx                    # React-Einstiegspunkt
│   ├── index.css                   # Globale Styles (2700+ Zeilen)
│   ├── vite-env.d.ts              # Vite TypeScript-Typen
│   │
│   ├── pages/                      # 10 Seitenkomponenten
│   │   ├── HomePage.tsx            # Startseite
│   │   ├── LeistungenPage.tsx      # Leistungen (8 Services)
│   │   ├── RatgeberPage.tsx        # Blog/Ratgeber mit Filter
│   │   ├── ArticlePage.tsx         # Einzelner Blogartikel
│   │   ├── KontaktPage.tsx         # Kontaktseite mit Formular
│   │   ├── TeamPage.tsx            # Team & Unternehmen
│   │   ├── AnalysePage.tsx         # Konkurrenzanalyse (noindex)
│   │   ├── ImpressumPage.tsx       # Impressum
│   │   ├── DatenschutzPage.tsx     # Datenschutzerklaerung
│   │   └── NotFoundPage.tsx        # 404-Fehlerseite
│   │
│   ├── components/                 # 17 wiederverwendbare Komponenten
│   │   ├── Navbar.tsx              # Hauptnavigation (fixiert)
│   │   ├── Footer.tsx              # Fusszeile mit Links
│   │   ├── Hero.tsx                # Hero-Bereich Startseite
│   │   ├── Services.tsx            # Leistungsuebersicht (9 Karten)
│   │   ├── About.tsx               # Ueber-uns-Bereich
│   │   ├── Gallery.tsx             # Vorher/Nachher-Galerie + Lightbox
│   │   ├── Testimonials.tsx        # Kundenbewertungen-Karussell
│   │   ├── Process.tsx             # 4-Schritte-Prozess
│   │   ├── FAQ.tsx                 # Haeufige Fragen (Akkordeon)
│   │   ├── BlogTeaser.tsx          # Blog-Vorschau (3 Beitraege)
│   │   ├── ContactBanner.tsx       # Kontakt-CTA-Banner
│   │   ├── ContactForm.tsx         # Kontaktformular + Supabase
│   │   ├── PageHero.tsx            # Wiederverwendbarer Seiten-Hero
│   │   ├── ServiceBlock.tsx        # Einzelner Leistungsblock
│   │   ├── SealBadge.tsx           # "Seit 2005"-Siegel (SVG)
│   │   └── WhatsAppButton.tsx      # Schwebender WhatsApp-Button
│   │
│   ├── hooks/                      # 2 Custom React Hooks
│   │   ├── useSEO.ts              # Dynamische SEO-Meta-Tags
│   │   └── useScrollReveal.ts     # Scroll-Animationen
│   │
│   ├── data/                       # Statische Daten
│   │   └── articles.ts            # 10 Blogartikel mit HTML-Inhalt
│   │
│   ├── lib/                        # Bibliotheks-Integration
│   │   └── supabase.ts            # Supabase-Client-Initialisierung
│   │
│   └── utils/                      # Hilfsfunktionen
│       └── generatePdf.ts         # PDF-Export Konkurrenzanalyse
│
├── supabase/
│   └── migrations/                 # 3 Datenbank-Migrationen
│       ├── 20260329142647_create_contact_requests.sql
│       ├── 20260329153418_create_newsletter_subscribers.sql
│       └── 20260329154455_fix_contact_requests_rls_policy.sql
│
├── index.html                      # HTML-Einstiegspunkt + Schema.org
├── package.json                    # Abhaengigkeiten
├── vite.config.ts                  # Vite-Konfiguration
├── tailwind.config.js              # Tailwind-Konfiguration
├── tsconfig.json                   # TypeScript-Konfiguration
├── eslint.config.js                # ESLint-Regeln
├── postcss.config.js               # PostCSS-Plugins
└── .env                            # Umgebungsvariablen (Supabase)
```

---

## 4. Seiten

### 4.1 Startseite (`HomePage.tsx`)
- **Route:** `/`
- **Inhalt:** Hero-Bereich, Leistungsuebersicht, Ueber-uns, Galerie, Kundenstimmen, Prozess, FAQ, Blog-Vorschau, Kontakt-Banner
- **SEO:** Eigener Titel und Beschreibung

### 4.2 Leistungen (`LeistungenPage.tsx`)
- **Route:** `/leistungen`
- **Inhalt:** 8 detaillierte Leistungsbloecke mit alternierenden Layouts
- **Leistungen:**
  1. Gartengestaltung & Neuanlagen
  2. Pflege & Wartung
  3. Pflasterarbeiten
  4. Natursteinarbeiten
  5. Erdbewegung & Gelaendemodellierung
  6. Baumfaellung & Baumpflege
  7. Wegebau & Einfahrten
  8. Rollrasen & Zaunbau
- **Funktionen:** Jeder Block hat Nummer, Titel, Beschreibung, Tags, Bild, CTA-Button

### 4.3 Ratgeber / Blog (`RatgeberPage.tsx`)
- **Route:** `/ratgeber` und `/ratgeber/thema/:category`
- **Inhalt:** 10 Fachartikel mit Kategoriefilter
- **Funktionen:**
  - Filterleiste mit 10 Kategorien
  - Erster Artikel als "Featured" hervorgehoben (groessere Karte)
  - Newsletter-Anmeldung am Ende der Seite
  - Duplikat-Erkennung bei Newsletter-E-Mails

### 4.4 Artikelseite (`ArticlePage.tsx`)
- **Route:** `/ratgeber/:slug`
- **Inhalt:** Voller Artikelinhalt mit Hero-Bild, Lesezeit, Kategorie
- **Funktionen:**
  - HTML-Rendering des Artikelinhalts
  - 2 verwandte Artikel am Ende
  - CTA-Box fuer Kontaktanfrage
  - Automatische Weiterleitung falls Slug nicht existiert
  - Article-Schema.org JSON-LD fuer Google

### 4.5 Kontaktseite (`KontaktPage.tsx`)
- **Route:** `/kontakt`
- **Inhalt:** Kontaktformular + Seitenleiste mit Informationen
- **Seitenleiste:**
  - Kontaktdaten (Telefon, Mobil, E-Mail, Adresse)
  - Oeffnungszeiten (Mo-Fr 7-17 Uhr, Sa 8-13 Uhr)
  - Google Maps Einbettung
- **Formular:** Siehe Abschnitt 11.1

### 4.6 Team (`TeamPage.tsx`)
- **Route:** `/team`
- **Inhalt:** Portrait Juergen Giesen, Statistiken, 4 Unternehmenswerte, CTA
- **Statistiken:** 20+ Jahre Erfahrung, 500+ Projekte, 9 Leistungsbereiche

### 4.7 Konkurrenzanalyse (`AnalysePage.tsx`)
- **Route:** `/analyse`
- **Sichtbarkeit:** noindex (nicht in Suchmaschinen)
- **Inhalt:** 5 Wettbewerber-Analysen mit Bedrohungsstufen, Staerken/Schwaechen
- **Funktionen:** Fortschrittsanzeige, 3 Prioritaetsstufen, PDF-Export

### 4.8 Impressum (`ImpressumPage.tsx`)
- **Route:** `/impressum`
- **Inhalt:** Gesetzlich vorgeschriebene Angaben (TMG), Haftungsausschluss

### 4.9 Datenschutz (`DatenschutzPage.tsx`)
- **Route:** `/datenschutz`
- **Inhalt:** DSGVO-konforme Datenschutzerklaerung

### 4.10 404-Seite (`NotFoundPage.tsx`)
- **Route:** `*` (alle nicht definierten Pfade)
- **Inhalt:** Fehlermeldung mit Links zur Startseite und Kontakt
- **SEO:** noindex

---

## 5. Komponenten

### 5.1 Navigation (`Navbar.tsx`)
- Fixiert am oberen Rand, z-index 1000
- Glasmorphismus-Effekt (halbtransparent mit Blur)
- Logo-Link zur Startseite
- Qualitaetssiegel "Seit 2005 Ihr Partner am Niederrhein"
- 5 Navigationslinks + Telefon-CTA-Button
- Responsive: Hamburger-Menue ab 768px
- Schatten bei Scroll (`scrolled`-Klasse)
- ARIA-Label fuer Barrierefreiheit

### 5.2 Fusszeile (`Footer.tsx`)
- 4-Spalten-Grid: Marke, Leistungen, Mehr, Unternehmen
- Social-Media-Links (Facebook, Instagram)
- Copyright mit automatischem Jahr
- Adresse und Telefonnummer
- Links zu allen wichtigen Seiten

### 5.3 Hero (`Hero.tsx`)
- Vollbild-Hero-Bereich mit animierten Blatt-SVGs
- Firmenlogo und Badge "Ihr Fachbetrieb in Alpen & Umgebung"
- Hauptueberschrift mit Betonung
- 2 CTA-Buttons: "Kostenlos anfragen" + "Alle Leistungen"
- Statistiken (Responsive: Desktop am unteren Rand, Mobile inline)
- Hero-Bild rechts mit Clip-Path (Desktop)
- "Seit 2005"-Siegel als SVG-Badge

### 5.4 Leistungsuebersicht (`Services.tsx`)
- 9 Leistungskarten im Grid-Layout
- Jede Karte: Icon (Lucide), Titel, Kurzbeschreibung
- Hover-Effekt: Verschiebung + Schatten + Farbwechsel des Icons
- Untere Akzentlinie bei Hover
- CTA-Link zur Leistungsseite

### 5.5 Ueber uns (`About.tsx`)
- 2-Spalten-Layout: Bild links, Text rechts
- Schwebendes Badge "20+ Jahre"
- 4 Vorteile mit Haekchen-Icons
- CTA-Button zum Kontaktbereich

### 5.6 Galerie (`Gallery.tsx`)
- 6 Projekte mit Vorher/Nachher-Bildern
- Umschalt-Button zwischen Vorher und Nachher
- Lightbox-Modal mit:
  - Beiden Bildern nebeneinander
  - Vor/Zurueck-Navigation
  - Schliessen-Button
  - Tastatursteuerung (Escape, Pfeiltasten)
  - ARIA-Attribute (Dialog, Modal)

### 5.7 Kundenstimmen (`Testimonials.tsx`)
- Karussell mit 5 Bewertungen
- Sterne-Bewertung (5 Sterne)
- Kundenname, Ort, Leistung
- Zitattext (kursiv)
- Navigation: Vor/Zurueck-Buttons + Punkt-Indikatoren

### 5.8 Prozess (`Process.tsx`)
- 4 nummerierte Schritte in einer Reihe
- Verbindungslinie zwischen den Schritten (Desktop)
- Schritte: Erstgespraech, Planung & Angebot, Umsetzung, Uebergabe
- Hover-Effekt auf Nummernkreisen

### 5.9 FAQ (`FAQ.tsx`)
- 7 Fragen mit Akkordeon-Funktion
- Nur eine Antwort gleichzeitig geoeffnet
- Chevron-Icon dreht sich bei Oeffnung
- CTA am Ende: "Noch Fragen?" mit Kontakt- und Telefon-Links
- ARIA-Attribute: aria-expanded, aria-controls, id

### 5.10 Blog-Vorschau (`BlogTeaser.tsx`)
- 3 ausgewaehlte Blogartikel als Karten
- Bild, Kategorie-Label, Titel, Kurztext
- "Weiterlesen"-Link zu jedem Artikel
- "Alle Beitraege"-Button

### 5.11 Kontakt-Banner (`ContactBanner.tsx`)
- Dunkler Hintergrund mit Farbverlauf
- Logo, Ueberschrift, Beschreibung
- 3 Kontakt-Chips: Festnetz, Mobil, E-Mail
- 2 CTAs: Kontaktformular + Telefon

### 5.12 Kontaktformular (`ContactForm.tsx`)
- **Felder:** Name, E-Mail, Telefon (optional), Leistung (Dropdown), Nachricht
- **Rueckruf-Option:** Checkbox + Zeitfenster-Auswahl (3 Optionen)
- **Spamschutz:** Honeypot-Feld ("website")
- **Datenspeicherung:** Supabase `contact_requests`-Tabelle
- **Zustaende:** Leer, Laden, Erfolg, Fehler
- **Validierung:** HTML5-Formularvalidierung + Server-seitige Regex

### 5.13 Seiten-Hero (`PageHero.tsx`)
- Wiederverwendbar fuer alle Unterseiten
- Props: label, title (HTML-faehig), description
- Logo-Link (dekorativ, aria-hidden)
- Hintergrund mit Farbverlauf

### 5.14 Leistungsblock (`ServiceBlock.tsx`)
- Fuer die Leistungsseite
- 2-Spalten-Layout mit optionaler Spiegelung (`reverse`)
- Props: Nummer, Label, Titel, Absaetze, Tags, CTA, Bild
- Lazy Loading fuer Bilder

### 5.15 WhatsApp-Button (`WhatsAppButton.tsx`)
- Schwebender Button (unten rechts, z-index 1500)
- WhatsApp-Link mit vorgefuellter Nachricht
- Tooltip bei Hover: "WhatsApp schreiben"
- Telefonnummer: +49 172 7854394

---

## 6. Daten & Inhalte

### 6.1 Blogartikel (`src/data/articles.ts`)

| Nr | Slug | Titel | Kategorie | Lesezeit |
|---|---|---|---|---|
| 1 | der-perfekte-garten-planung | 5 Ideen fuer einen naturnahen Garten in NRW | Gartengestaltung | 8 Min |
| 2 | gartenpflege-fruehjahr | Gartenpflege im Fruehjahr | Pflege | 5 Min |
| 3 | pflastermaterial-vergleich | Welches Pflastermaterial passt zu Ihrem Haus? | Pflasterarbeiten | 6 Min |
| 4 | natursteinmauern-garten | Natursteinmauern im Garten | Naturstein | 7 Min |
| 5 | gelaendemodellierung-bagger | Gelaendemodellierung mit Minibagger | Erdbewegung | 4 Min |
| 6 | kranke-baeume-erkennen | Wann muss ein Baum gefaellt werden? | Baumfaellung | 5 Min |
| 7 | gartenwege-gestalten | Gartenwege schoener gestalten | Wegebau | 6 Min |
| 8 | rollrasen-verlegen | Rollrasen richtig verlegen | Rollrasen | 5 Min |
| 9 | zaun-materialien-vergleich | Zaun-Materialien im Vergleich | Zaunbau | 5 Min |

Jeder Artikel enthaelt vollstaendigen HTML-Inhalt mit Ueberschriften, Absaetzen, Listen und Hervorhebungen.

### 6.2 Kategorien

Alle Themen, Gartengestaltung, Pflege, Pflasterarbeiten, Naturstein, Erdbewegung, Baumfaellung, Wegebau, Rollrasen, Zaunbau

### 6.3 Galerie-Projekte (in `Gallery.tsx`)

6 Projekte mit Vorher/Nachher-Paaren:
1. Komplettgestaltung Vorgarten -- Alpen
2. Pflasterarbeiten Einfahrt -- Xanten
3. Natursteinmauer Hangbefestigung -- Rheinberg
4. Gartenteich-Anlage -- Sonsbeck
5. Rollrasen & Wege -- Wesel
6. Baumfaellung & Neugestaltung -- Moers

### 6.4 Kundenstimmen (in `Testimonials.tsx`)

5 Bewertungen von Kunden aus der Region (alle 5 Sterne):
- Familie Weber, Alpen
- Thomas Mueller, Xanten
- Maria Schneider, Rheinberg
- Peter & Anna Koch, Sonsbeck
- Dr. Fischer, Wesel

### 6.5 FAQ (in `FAQ.tsx`)

7 Fragen zu: Erstberatung, Einzugsgebiet, Kosten, Pflegevertraege, beste Jahreszeit, Baumfaellgenehmigung, Projektdauer

---

## 7. Datenbank (Supabase)

### 7.1 Verbindung

- **URL:** Aus `VITE_SUPABASE_URL` (.env)
- **Anon Key:** Aus `VITE_SUPABASE_ANON_KEY` (.env)
- **Client:** `src/lib/supabase.ts` -- Singleton-Instanz mit `createClient()`

### 7.2 Tabellen

#### `contact_requests`
| Spalte | Typ | Standard | Beschreibung |
|---|---|---|---|
| id | uuid | gen_random_uuid() | Primaerschluessel |
| name | text | -- | Name des Besuchers |
| email | text | -- | E-Mail-Adresse |
| phone | text | '' | Telefonnummer (optional) |
| service | text | '' | Gewaehlte Leistung |
| message | text | -- | Nachricht |
| callback_requested | boolean | false | Rueckruf gewuenscht? |
| callback_time | text | '' | Gewuenschter Zeitraum |
| created_at | timestamptz | now() | Erstellungszeitpunkt |
| status | text | 'new' | Status: new/read/replied |

**RLS-Policy:** Nur INSERT fuer anonyme Nutzer mit Validierung:
- Name darf nicht leer sein
- E-Mail muss gueltig sein (Regex)
- Nachricht darf nicht leer sein
- Status muss 'new' sein

#### `newsletter_subscribers`
| Spalte | Typ | Standard | Beschreibung |
|---|---|---|---|
| id | uuid | gen_random_uuid() | Primaerschluessel |
| email | text (UNIQUE) | -- | E-Mail-Adresse |
| subscribed_at | timestamptz | now() | Anmeldezeitpunkt |
| active | boolean | true | Aktiv/Abgemeldet |

**RLS-Policy:** Nur INSERT fuer anonyme Nutzer. Duplikat-Erkennung ueber UNIQUE-Constraint.

### 7.3 Sicherheit
- Row Level Security (RLS) auf beiden Tabellen aktiviert
- Anonyme Nutzer koennen nur INSERT (keine SELECT/UPDATE/DELETE)
- Server-seitige Validierung in der Policy
- Honeypot-Feld im Frontend gegen Spam

---

## 8. SEO & Suchmaschinenoptimierung

### 8.1 Schema.org Structured Data (index.html)

**LocalBusiness:**
- Firmenname, Beschreibung, URL
- Telefon: +492802948787
- E-Mail: juergen-giesen-galabau@web.de
- Adresse: Giesenacker 61, 46519 Alpen, NRW, DE
- Geo-Koordinaten: 51.5886, 6.5126
- Oeffnungszeiten: Mo-Fr 07:00-17:00
- Gruendungsjahr: 2005
- Gruender: Juergen Giesen
- Einzugsgebiet: 40km Radius + 6 namentliche Staedte
- 9 Leistungsbereiche in `serviceType` und `knowsAbout`

**FAQPage:**
- 7 Frage-Antwort-Paare fuer Google Rich Snippets

### 8.2 Dynamische SEO (useSEO Hook)

Jede Seite setzt individuell:
- `<title>` -- z.B. "Leistungen | Juergen Giesen -- Garten- & Landschaftsbau"
- `<meta name="description">` -- Seitenbeschreibung
- `<meta name="robots">` -- index/follow oder noindex/nofollow
- `<link rel="canonical">` -- Kanonische URL
- Open Graph Tags: og:title, og:description, og:url, og:image, og:type, og:locale
- Twitter Card Tags
- Optionales JSON-LD (z.B. Article-Schema fuer Blogartikel)

### 8.3 Statische SEO-Dateien

**robots.txt:**
- Erlaubt alle Crawler
- Blockiert `/analyse`
- Verweist auf Sitemap

**sitemap.xml:**
- 16 URLs mit Prioritaeten (1.0 bis 0.3)
- Aenderungsfrequenz: weekly, monthly, yearly
- Letztes Aenderungsdatum: 2026-04-16

**llms.txt:**
- Strukturierte Firmeninformationen fuer KI-Crawler
- Firmenname, Adresse, Kontakt, Leistungen, Oeffnungszeiten

**manifest.json:**
- PWA-Manifest fuer "Zum Startbildschirm hinzufuegen"
- Theme-Color: #617327

### 8.4 Geo-Meta-Tags (index.html)

```html
<meta name="geo.region" content="DE-NW" />
<meta name="geo.placename" content="Alpen" />
<meta name="geo.position" content="51.5886;6.5126" />
<meta name="ICBM" content="51.5886, 6.5126" />
```

### 8.5 Bild-Optimierung

- Hero-Bild: `loading="eager"`, `fetchPriority="high"`
- Alle anderen Bilder: `loading="lazy"`
- Breiten- und Hoehenangaben auf allen Bildern (verhindert Layout-Verschiebungen)
- Preload-Hints im HTML-Head fuer Hero-Bild und Logo

---

## 9. Barrierefreiheit (Accessibility)

### 9.1 Tastaturnavigation
- "Zum Inhalt springen"-Link (Skip-to-Content)
- Sichtbare Fokus-Styles (`focus-visible`) auf 25+ interaktiven Elementen
- Tastatursteuerung in der Galerie-Lightbox (Escape, Pfeiltasten)

### 9.2 ARIA-Attribute
- `aria-label` auf Navigation, FAQ, Seitenheroes
- `aria-expanded` und `aria-controls` auf FAQ-Akkordeon
- `aria-modal` und `role="dialog"` auf Lightbox
- `aria-hidden` auf dekorativen Elementen

### 9.3 Versteckte Eingabefelder
- Checkboxen in Kontaktformular sind screenreader-kompatibel (visually-hidden statt display:none)

### 9.4 Farbkontraste
- Helle Texte auf dunklem Hintergrund: mindestens 85% Deckkraft
- Mindest-Schriftgroessen korrigiert

### 9.5 Bewegungsreduzierung
- `prefers-reduced-motion: reduce` deaktiviert alle Animationen
- Scroll-Reveal-Animationen werden uebersprungen

### 9.6 Druckstyles
- Navigation, WhatsApp-Button und Dekorelemente ausgeblendet
- Links zeigen URLs im Ausdruck
- Hintergruende auf Weiss gesetzt

---

## 10. Design & Styling

### 10.1 Farbpalette (CSS-Variablen)

| Variable | Wert | Verwendung |
|---|---|---|
| --green-dark | #617327 | Primaerfarbe, Ueberschriften |
| --green-mid | #7a8e3a | Sekundaerfarbe, Hover |
| --green-light | #9aad55 | Akzente, Fokus-Styles |
| --green-pale | #d5de98 | Hintergruende, Badges |
| --accent | #4e5c1f | CTAs, dunkle Akzente |
| --accent-light | #617327 | Hover auf Akzenten |
| --cream | #fafaf5 | Seitenhintergrund |
| --text-dark | #2d3618 | Haupttext |
| --text-mid | #5a6340 | Sekundaertext |
| --white | #ffffff | Weiss |

### 10.2 CSS-Architektur

Die Styles sind in `src/index.css` organisiert nach Abschnitten:

1. Tailwind-Direktiven und CSS-Variablen
2. Globaler Reset
3. Navigation (fixiert, Glasmorphismus)
4. Hero-Bereich (Animationen, Statistiken)
5. Siegel-Badge (SVG, Animation)
6. Allgemeine Sektionen (Padding, Titel, Untertitel)
7. Leistungskarten (Grid, Hover-Effekte)
8. Ueber-uns (2-Spalten, Bild)
9. Prozess (4 Schritte, Verbindungslinie)
10. Blog-Karten (Grid, Thumbnails)
11. Kontakt-Banner (Farbverlauf)
12. Fusszeile (4-Spalten-Grid)
13. Unterseiten-Heroes
14. Leistungsdetails (ServiceBlock)
15. Artikel-Detailseite
16. Scroll-Reveal-Animationen
17. Responsive Breakpoints (1024px, 768px, 480px)
18. Kontaktformular
19. Rechtliche Seiten
20. Kundenstimmen-Karussell
21. Galerie + Lightbox
22. FAQ-Akkordeon
23. WhatsApp-Button
24. Team-Seite
25. Barrierefreiheit (Fokus, Kontrast, Bewegung)
26. Druckstyles

### 10.3 Responsive Design

- **1024px:** 2-Spalten-Layouts werden zu 1-Spalte, Hero-Bild verschwindet
- **768px:** Mobile Navigation, volle Breite fuer alle Inhalte
- **480px:** Kompaktere Abstande, kleinere Schriften

### 10.4 Animationen

- **fadeUp:** Elemente gleiten von unten ein
- **fadeRight:** Hero-Bild gleitet von rechts ein
- **sealPop:** Siegel erscheint mit Bounce-Effekt
- **floatLeaf:** Blaetter schweben sanft auf und ab
- **pulse:** Gruener Punkt pulsiert
- **spinAnim:** Lade-Spinner dreht sich

---

## 11. Funktionen im Detail

### 11.1 Kontaktformular

**Ablauf:**
1. Nutzer fuellt Name, E-Mail, optional Telefon, Leistung, Nachricht aus
2. Optional: Rueckruf-Checkbox + Zeitfenster (Vormittags/Nachmittags/Flexibel)
3. Honeypot-Feld "website" bleibt leer (Spam-Schutz)
4. Bei Absenden: Daten werden in Supabase `contact_requests` gespeichert
5. Erfolg: Bestaetigungsmeldung mit gruener Box
6. Fehler: Fehlermeldung mit roter Box

### 11.2 Newsletter-Anmeldung

**Ablauf:**
1. E-Mail-Eingabe auf der Ratgeber-Seite
2. Insert in `newsletter_subscribers`
3. Bei Duplikat: Hinweismeldung "Sie sind bereits angemeldet"
4. Bei Erfolg: Bestaetigung

### 11.3 Vorher/Nachher-Galerie

**Funktionen:**
- 6 Projekte mit je 2 Bildern
- Toggle-Button wechselt zwischen Vorher und Nachher
- Klick auf Bild oeffnet Lightbox
- Lightbox zeigt beide Bilder nebeneinander
- Navigation mit Pfeiltasten oder Buttons
- Schliessen mit Escape oder X-Button

### 11.4 FAQ-Akkordeon

**Funktionen:**
- 7 Fragen, nur eine gleichzeitig geoeffnet
- Klick auf Frage oeffnet/schliesst Antwort
- Sanfte Hoehen-Animation
- Chevron-Icon dreht sich

### 11.5 Kundenstimmen-Karussell

**Funktionen:**
- 5 Bewertungen, eine gleichzeitig sichtbar
- Vor/Zurueck-Buttons
- Punkt-Navigation fuer Direktzugriff
- Sterne-Bewertung

### 11.6 PDF-Export (Konkurrenzanalyse)

**Funktionen:**
- Generiert mehrseitigen PDF-Bericht aus Canvas
- Enthaelt: Header, Staerken, 5 Wettbewerber-Analysen, Massnahmenplan
- Oeffnet Druckdialog des Browsers
- Verwendet Firmenfarben

### 11.7 Scroll-Reveal-Animationen

**Funktionen:**
- Elemente mit `.reveal`-Klasse starten unsichtbar
- IntersectionObserver erkennt Sichtbarkeit (Schwelle: 12%)
- Gestaffelte Animation mit 80ms Verzoegerung pro Geschwister
- `.visible`-Klasse loest CSS-Transition aus

---

## 12. Oeffentliche Dateien (Public)

### 12.1 Bilder

| Datei | Verwendung |
|---|---|
| Logo_Giesen.png | Firmenlogo (Navigation, Footer, Heroes, Siegel) |
| JuergenGiesen_(1).jpg | Portraitfoto auf der Teamseite |
| Landschaftsbaugiesen1-25,28.jpg | Projektfotos fuer Galerie, Leistungen, Blog |
| Nutursteinmauervorher.jpg | Vorher-Foto Natursteinmauer |
| Nutursteinmauernachher.jpg | Nachher-Foto Natursteinmauer |

### 12.2 SEO-Dateien

| Datei | Zweck |
|---|---|
| robots.txt | Steuerung der Suchmaschinen-Crawler |
| sitemap.xml | XML-Sitemap mit 16 URLs und Prioritaeten |
| llms.txt | Strukturierte Informationen fuer KI-Systeme |
| manifest.json | PWA-Manifest fuer mobile Geraete |

---

## Routing-Uebersicht

| Pfad | Seite | Indexiert |
|---|---|---|
| `/` | Startseite | Ja |
| `/leistungen` | Leistungen | Ja |
| `/ratgeber` | Ratgeber/Blog | Ja |
| `/ratgeber/thema/:category` | Ratgeber (gefiltert) | Ja |
| `/ratgeber/:slug` | Einzelner Artikel | Ja |
| `/team` | Team & Unternehmen | Ja |
| `/kontakt` | Kontakt | Ja |
| `/analyse` | Konkurrenzanalyse | Nein (noindex) |
| `/impressum` | Impressum | Ja |
| `/datenschutz` | Datenschutz | Ja |
| `*` | 404-Fehlerseite | Nein (noindex) |
