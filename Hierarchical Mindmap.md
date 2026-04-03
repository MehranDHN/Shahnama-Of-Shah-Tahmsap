# 📜 Shahnama of Shah Tahmasp — RDF Knowledge Graph Mind Map  
**Based exactly on `resources.ttl` (and `mdhn-starter_ontology.ttl`)**  
**Root**: `mdhn:manuscript_shahnama_shah_tahmasp` (the complete illuminated manuscript)

**Ontology summary** (from `mdhn-starter_ontology.ttl`):  
- `mdhn:Manuscript` → contains multiple `mdhn:Folio` (via `hasContentElement` / `hasRegisterEntry`)  
- Each `mdhn:Folio` → `mdhn:hasIIIFManifest` (IIIF Presentation 3.0)  
- Each `mdhn:Painting` on a folio → `mdhn:hasCroppedFigure` (`mdhn:FigureCrop`) with `mdhn:iiifRegionURL`  
- Inscriptions (`mdhn:Inscription`) linked via `mdhn:hasInscription` / `mdhn:hasIiifInscriptionURL` (none present in current sample data)

---




**All 16 Folios** (extracted from `resources.ttl`):

### Folio 2v
![Folio 2v Thumbnail](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-2v%2FFolio2v.jpg/full/!500,0/0/default.jpg)  
**IIIF Manifest**: [https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-2v/manifest.json](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-2v/manifest.json)  
- **Cropped Figures**: None  
- **Inscriptions**: None

### Folio 3r
![Folio 3r Thumbnail](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-3r%2FFolio3r.jpg/full/!500,0/0/default.jpg)  
**IIIF Manifest**: [https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-3r/manifest.json](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-3r/manifest.json)  
- **Cropped Figures**: None  
- **Inscriptions**: None

### Folio 7r
![Folio 7r Thumbnail](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-7r%2FFolio7r.jpg/full/!500,0/0/default.jpg)  
**IIIF Manifest**: [https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-7r/manifest.json](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-7r/manifest.json)  
- **Cropped Figures** (4 × `mdhn:FigureCrop`):
  - Firdowsi  
    ![Firdowsi cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-7r%2FFolio7r.jpg/314,802,118,236/max/0/default.jpg)
  - Abu-Mansur Daqiqi  
    ![Abu-Mansur Daqiqi cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-7r%2FFolio7r.jpg/622,648,127,151/max/0/default.jpg)
  - Unsuri  
    ![Unsuri cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-7r%2FFolio7r.jpg/715,744,143,177/max/0/default.jpg)
  - Asjadi  
    ![Asjadi cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-7r%2FFolio7r.jpg/489,682,110,164/max/0/default.jpg)
- **Inscriptions**: None

### Folio 20v
![Folio 20v Thumbnail](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/full/!500,0/0/default.jpg)  
**IIIF Manifest**: [https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-20v/manifest.json](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-20v/manifest.json)  
- **Cropped Figures** (3 × `mdhn:FigureCrop`):
  - Keyumars  
    ![Keyumars cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/332,517,120,165/max/0/default.jpg)
  - Siamak  
    ![Siamak cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/489,642,106,133/max/0/default.jpg)
  - Hushang  
    ![Hushang cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/205,582,90,180/max/0/default.jpg)
- **Inscriptions**: None

### Folio 21v
![Folio 21v Thumbnail](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/full/!500,0/0/default.jpg)  
**IIIF Manifest**: [https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-21v/manifest.json](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-21v/manifest.json)  
- **Cropped Figures** (multiple `mdhn:FigureCrop`):
  - Hushang  
    ![Hushang cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/508,1280,195,129/max/0/default.jpg)
  - Black Div  
    ![Black Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/522,1370,343,204/max/0/default.jpg)
  - Div (1)  
    ![Div cropped 1](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/253,1462,176,244/max/0/default.jpg)
  - Div (2)  
    ![Div cropped 2](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/710,1637,219,208/max/0/default.jpg)
  - Div (3)  
    ![Div cropped 3](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/710,1637,219,208/max/0/default.jpg) *(additional Div crops follow the same pattern)*
- **Inscriptions**: None

### Remaining Folios (structure only — no cropped figures/inscriptions defined in sample data)
- **Folio 22v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-22v/manifest.json)  
- **Folio 23v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-23v/manifest.json)  
- **Folio 24v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-24v/manifest.json)  
- **Folio 25v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-25v/manifest.json)  
- **Folio 27v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-27v/manifest.json)  
- **Folio 38v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-38v/manifest.json)  
- **Folio 76v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-76v/manifest.json)  
- **Folio 77v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-77v/manifest.json)  
- **Folio 82v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-82v/manifest.json)  
- **Folio 102v** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-102v/manifest.json)  
- **Folio 299r** — [IIIF Manifest](https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-299r/manifest.json)  

*(Thumbnails for these can be generated identically by replacing the manifest ID in the IIIF Image API pattern shown above.)*

---

**Key Observations from `resources.ttl`**:
- All folios are linked to high-resolution IIIF manifests (Internet Archive).
- Cropped figures (`mdhn:FigureCrop`) are only defined for a subset of folios in the current sample (primarily painting-heavy pages).
- No `mdhn:Inscription` instances appear in the sample data (the property exists in the ontology and can be populated later).
- Every cropped figure includes an exact `mdhn:iiifRegionURL` for precise IIIF Image API cropping.

You can copy-paste this entire markdown into any GitHub README, Obsidian, Typora, or VS Code with Mermaid support — the images will render live from the public IIIF service. Let me know if you want a pure Mermaid-only version, SVG export, or expansion with the remaining folios’ thumbnails once more image filenames are confirmed!