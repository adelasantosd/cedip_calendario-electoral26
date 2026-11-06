# Ruta a la LXVII Legislatura

An interactive vertical timeline of the 2026–2027 Mexican federal electoral process, the replacement of the President of the National Electoral Institute (INE), and the legislative calendar of the Chamber of Deputies. It is designed for the Centro de Estudios de Derecho e Investigaciones Parlamentarias (CEDIP).

The interface is in Spanish. This documentation is in English.

- **Live site:** <https://cedipcalendario-electoral26.vercel.app>
- **Data cut-off:** 5 November 2026 (Mexico City time)
- **Events:** 93, each with its legal basis and sources
- **Research dossier:** [`INVESTIGACION.md`](INVESTIGACION.md)
- **Change history:** [`CHANGELOG.md`](CHANGELOG.md)

---

## Public release 1.0.0

Author: Adela Santos Domínguez. Release preparation date: 6 November 2026.
Public repository (publication destination): <https://github.com/adelasantosd/cedip_calendario-electoral26>.
Data cut-off: 2026-11-05. This snapshot contains 93 events, of which 4 retain a primary-source verification flag.

This edition is an independent publication snapshot. The live website may change after this release. The publication review checks packaging and internal consistency; it does not constitute a new verification of the legal or factual claims in the supplied dataset.

## AI assistance disclosure

Se utilizaron Codex (OpenAI) y Claude (Anthropic) como herramientas de asistencia para el diseño de la interfaz pública.

## Reuse and citation

The original HTML, CSS and JavaScript in `index.html` are distributed under the MIT License; see `LICENSE`. The original dataset compilation in `datos/eventos.json` and the documentation are available under Creative Commons Attribution 4.0 International (CC BY 4.0); see `LICENSE-DATA.md`. Both permit reuse, modification and redistribution, including commercial use, subject to their terms.

The CEDIP logo in `assets/cedip-logo.png` is excluded from these licenses. Its inclusion does not grant permission to reuse it or imply institutional endorsement. Third-party materials and linked sources retain their own terms. Public-domain material is not made subject to new exclusive rights by this publication.

Use `CITATION.cff` for citation. `.zenodo.json` supplies metadata for the software record, with MIT as the code license and the separate data and documentation terms described explicitly. A DOI must be added after Zenodo assigns it. No DOI or ORCID has been fabricated.

## Contents

1. [What the timeline shows](#what-the-timeline-shows)
2. [Repository structure](#repository-structure)
3. [Running it locally](#running-it-locally)
4. [Updating the data](#updating-the-data)
5. [Data model](#data-model)
6. [Methodology and verification](#methodology-and-verification)
7. [Design and accessibility](#design-and-accessibility)
8. [Deployment](#deployment)
9. [Known limitations](#known-limitations)

---

## What the timeline shows

The page has four tracks, and each track has its own colour:

| Track (`carril`) | Label on the page | Colour | Side |
|---|---|---|---|
| `electoral` | Elección 2027 | Green `#3F7D54` | Left |
| `ine` | Presidencia del INE | Blue `#3D6B9E` | Left |
| `legislativo` | Congreso | Burgundy `#7F1D3A` | Right |
| `ambos` | Nueva Cámara | Ochre `#8A6413` | Centre, across the axis |

The shape of each marker shows how firm a date is. Its colour shows who acts.

| Status (`estado`) | Label on the page | Marker |
|---|---|---|
| `confirmado` | Ya ocurrió o ya es oficial | Filled circle |
| `plazo_legal` | Lo fija la ley | Filled square |
| `programado` | Agendado | Ring |
| `estimado` | Tentativo | Dashed ring |
| `calculado` | Fecha calculada | Filled circle |
| `pendiente` | Sin fecha | Dotted ring |

Main features:

- **Today marker.** It is computed in the `America/Mexico_City` time zone. It updates at midnight if the page stays open, and again whenever the tab regains focus. The central axis is solid up to today and dashed afterwards. Past events are dimmed. Events in progress carry an *en curso* label and a progress bar.
- **Counters.** Days to election day (6 June 2027) and to the constituent session (29 August 2027), plus the next four deadlines. Selecting a deadline scrolls to that event.
- **Filters.** Tracks can be switched on and off; Shift-click shows one track only. There is a free-text search, which ignores accents, and an *upcoming only* toggle.
- **Plain language.** Each event has a plain-language title (`claro`), with the technical title beneath it. A glossary of 62 terms underlines jargon and acronyms; tapping or hovering explains them.
- **Month minimap** on wide screens, showing how many events each month holds on each track.

## Repository structure

```
.
├── index.html            Single-page application (HTML, CSS and JS inline; no build step)
├── datos/
│   └── eventos.json      All events: the only file to edit for content changes
├── assets/
│   └── cedip-logo.png    CEDIP logo (238 × 108 px, transparent background)
├── INVESTIGACION.md      Research dossier: findings, corrections, open discrepancies
├── CHANGELOG.md          Dated record of changes
└── README.md
```

There are no dependencies to install. The page uses system fonts only: Iowan Old Style on Apple devices and Palatino Linotype on Windows, with Georgia as fallback.

## Running it locally

The page reads `datos/eventos.json` with `fetch`. Browsers block that when a file is opened directly from disk, so it needs a local server:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Updating the data

All content lives in `datos/eventos.json`. You do not need to edit `index.html` to add, correct or confirm an event.

### Confirming an event marked *falta confirmar*

1. Find the event by its `id`.
2. Set `"verificar_primaria": false`.
3. Add the official URL to `fuentes`, such as the Gaceta Parlamentaria, the Diario de los Debates or the DOF. If the source has no URL, describe it in `fuente_texto`.
4. If the event has happened, set `"estado": "confirmado"`.

### Adding an event

Copy an existing event and change every field. Rules:

- `id` must be unique. Use the prefix of the track: `e` electoral, `i` INE presidency, `l` legislative, `r` constitutional or legal reform.
- Dates use the `YYYY-MM-DD` format. Leave `fin` as `null` for one-day events.
- Keep `claro` under about 70 characters, in plain Spanish, and focused on what happens.
- Write `fundamento` with the acronyms the glossary recognises (`CPEUM`, `LGIPE`, `LGSMIME`, `LOCGEUM`, `RCD`, `LFPRH`, `LFRCF`). The page then links the current PDF of that law automatically.

Events do not need to be kept in order: the page sorts them by date. Before committing, check that the JSON is valid:

```bash
python3 -m json.tool datos/eventos.json > /dev/null && echo "JSON válido"
```

Also update `corte` (the data cut-off date) at the top of the file. The page shows it in the header and footer.

### Editorial conventions

- Every mention of Ricardo Monreal reads: *el diputado Ricardo Monreal, coordinador del GP MORENA*.
- Do not describe estimates as decisions. If a date comes from a political statement and no formal act exists yet, its status is `estimado`.

## Data model

`datos/eventos.json` contains three top-level keys: `corte` (date), `notas` (methodology note) and `eventos` (array).

| Field | Type | Required | Description |
|---|---|---|---|
| `id` | string | yes | Unique identifier |
| `carril` | enum | yes | `electoral`, `ine`, `legislativo`, `ambos` |
| `cat` | string | yes | Sub-category, e.g. `credencial`, `presupuesto`, `comparecencias` |
| `inicio` | date or `null` | yes | Start date. `null` places the event under *Sin fecha fija* |
| `fin` | date or `null` | yes | End date for ranges |
| `claro` | string | yes | Plain-language title shown first |
| `titulo` | string | yes | Technical title shown beneath |
| `detalle` | string | no | Explanation shown when the card is opened |
| `fundamento` | string | no | Legal basis, e.g. `CPEUM art. 41 V-A` |
| `estado` | enum | yes | See the status table above |
| `verificar_primaria` | boolean | yes | `true` means no official document has confirmed the event yet |
| `fuentes` | string[] | yes | Source URLs, official sources first |
| `fuente_texto` | string | no | Source without a URL, e.g. information supplied by CEDIP staff |

## Methodology and verification

Every event was checked against at least one of the following sources, in order of precedence:

1. **Current legal texts** published by the Chamber of Deputies (LeyesBiblio), as amended to the following dates: CPEUM 7 Oct 2026, LGIPE 2 Jun 2026, LGSMIME 14 Nov 2025, LOCGEUM 7 Jul 2025, Reglamento de la Cámara de Diputados 7 May 2025, LFPRH 9 Apr 2026, LFRCF 14 May 2026.
2. **INE's integrated calendar** for the 2026–2027 federal electoral process (agreement INE/CG479/2026) and INE press releases on Central Electoral.
3. **Chamber of Deputies records**: the Gaceta Parlamentaria, the Sistema de Información Legislativa and the press office.
4. **Press reports** for recent political facts that have no formal act yet.

The 4 events still flagged `verificar_primaria: true` can be listed with the command below. Each one names, in its `detalle` or in `INVESTIGACION.md`, the document that would confirm it.

```bash
python3 -c "import json;[print(e['id'],e['claro']) for e in json.load(open('datos/eventos.json'))['eventos'] if e['verificar_primaria']]"
```

Key findings that shape the content:

- The 2027 judicial election was moved to June 2028 (constitutional amendment, DOF 2 June 2026). In 2027 only federal deputies and local offices are elected.
- The appointment of a new INE President has no subsequent ratification. Article 41 V-A of the Constitution sets the sequence: an evaluation committee, a two-thirds vote in the Chamber, and a lottery in the Chamber or the Supreme Court if that vote fails.
- Bills without a committee report lapse when the LXVI Legislature ends on 31 August 2027 (Reglamento de la Cámara de Diputados, art. 184.2).

## Design and accessibility

- A single light theme on warm paper (`#F8F8F5`), shared with the author's other visual arguments. Headings and reading text use a book serif (Iowan Old Style or Palatino); controls use a sans serif. No web fonts are downloaded.
- Colours are muted and not tied to any party: in Mexico almost every saturated hue is associated with a political party. Small coloured text is darkened to reach a readable contrast against the pearl-grey background.
- Track and status are never shown by colour alone: side, position and marker shape carry the same information.
- All controls work with a keyboard. Cards open with Enter or Space, and glossary terms show their definition on keyboard focus.
- Animations are switched off when the user has asked the system for reduced motion.
- On phones the page becomes a single chronological column, without horizontal scrolling. The search box uses 16 px text so iOS does not zoom in, and touch targets are at least 42 px tall.
- Tested at iPhone 13, Pixel 7, iPad, 1440 × 900 (MacBook) and 1366 × 768 (Windows laptop) viewports.

## Deployment

The site is static and is served by Vercel from the `main` branch, with no build command.

1. Import the GitHub repository in Vercel. The framework preset is **Other** and no build command is needed.
2. Every push to `main` publishes to production. Pushes to other branches may create preview deployments; their access depends on the hosting configuration.

Content changes therefore only require editing `datos/eventos.json` and merging to `main`.

## Known limitations

- The Gaceta Parlamentaria (`gaceta.diputados.gob.mx`) serves an incomplete TLS certificate chain. Automated tools reject it, so Gaceta records have to be checked by hand.
- The CEDIP logo is a 238 px wide raster. A vector (SVG) version is needed for larger sizes.
- Dates of political events, such as the INE presidency vote, are estimates until the Chamber issues the call for candidates.

---

Prepared for CEDIP, Chamber of Deputies, LXVI Legislature. The CEDIP logo belongs to its respective rights holder and is excluded from the open licenses. This packaging review does not establish permission to redistribute the logo.
