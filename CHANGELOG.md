# Changelog

Dates use Mexico City time.

## 1.0.0 (2026-11-06)

- Prepared an independent public snapshot with citation and Zenodo metadata.
- Applied MIT to code and CC BY 4.0 to original data and documentation, excluding the institutional logo.
- Updated the repository link and added an interface-design AI assistance disclosure.
- Aligned documentation counts with the included dataset.


## 2026-11-05 (later)

### Changed
- Visual identity aligned with the author's visual-argument series: warm paper, navy ink, rust accent, book serif. Single light theme.
- Tracks recoloured: green (election), blue (INE), CEDIP burgundy (Congress), ochre (new Chamber).

### Fixed
- *Solo lo que viene* now brings the Today marker into view instead of leaving the reader at the bottom of a shorter page.
- Months with nothing left to show disappear from the minimap.
- iOS no longer zooms into the search box; larger touch targets on phones and tablets.

## 2026-11-05

### Added
- Interactive timeline (`index.html`) with four tracks, a daily *today* marker, counters, filters, search and a month minimap.
- Plain-language titles for all events, and a glossary of 62 terms.
- CEDIP logo and a link to this repository in the footer.
- Hearings (comparecencias) supplied by CEDIP staff: Finance Secretary before the Senate (6 Oct), Federal Electricity Commission (CFE, 5 Nov), and the postponed Science hearing (4 Nov).
- Professional documentation: `README.md` and this changelog.

### Changed
- Palette: pearl grey and graphite base, with olive, petrol, burgundy and bronze tracks.
- Security hearing (8 Oct) and Women's Affairs hearing (28 Oct) confirmed.
- Every mention of Ricardo Monreal now reads *el diputado Ricardo Monreal, coordinador del GP MORENA*.

### Verified
- First research pass: dataset of 67 events (`datos/eventos.json`).
- Cross-checked against INE/CG479/2026 and current legal texts. 8 dates or legal citations corrected, and 23 events added (see `INVESTIGACION.md`).
