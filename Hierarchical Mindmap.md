# 📜 Shahnama of Shah Tahmasp — RDF Knowledge Graph Mind Map  
**Based exactly on `resources.ttl` (and `mdhn-starter_ontology.ttl`)**  
**Root**: `mdhn:manuscript_shahnama_shah_tahmasp` (the complete illuminated manuscript)

**Ontology summary** (from `mdhn-starter_ontology.ttl`):  
- `mdhn:Manuscript` → contains multiple `mdhn:Folio` (via `hasContentElement` / `hasRegisterEntry`)  
- Each `mdhn:Folio` → `mdhn:hasIIIFManifest` (IIIF Presentation 3.0)  
- Each `mdhn:Painting` on a folio → `mdhn:hasCroppedFigure` (`mdhn:FigureCrop`) with `mdhn:iiifRegionURL`  
- Each `mdhn:Painting` on a folio → `mdhn:hasVisualItem` (`mdhn:MaterialObject`)  
- Inscriptions (`mdhn:Inscription`) linked via `mdhn:hasInscription` / `mdhn:hasIiifInscriptionURL` (none present in current sample data)

---
**Key Observations from `resources.ttl`**:
- All folios are linked to high-resolution IIIF manifests (Internet Archive).
- Cropped figures (`mdhn:FigureCrop`) are only defined for a subset of folios in the current sample (primarily painting-heavy pages).
- No `mdhn:Inscription` instances appear in the sample data (the property exists in the ontology and can be populated later).
- Every cropped figure includes an exact `mdhn:iiifRegionURL` for precise IIIF Image API cropping.

You can copy-paste this entire markdown into any GitHub README, Obsidian, Typora, or VS Code with Mermaid support — the images will render live from the public IIIF service. Let me know if you want a pure Mermaid-only version, SVG export, or expansion with the remaining folios’ thumbnails once more image filenames are confirmed!



**Folios** (An ongoing process extracted from `resources.ttl`):


### Folio 20v (The Court of Kayumars)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-20v/manifest.json)
- **Aga Khan Museum** 
  - Instance of Illuminated Folio WD:Q64665898
- **Narrative Episode**
  - WD:Q138719971
- **Depicts**
  - mdhn:Keyumars
  - mdhn:Siamak
  - mdhn:Hushang
- **Visual Items**
  - mdhn:Royal_Court
  - mdhn:LeopardSkinDress
  - mdhn:Throne
  - mdhn:Enthronement
  - mdhn:Turban
  - mdhn:Rock
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُSultan Muhammad** WD:Q6712884
    - **Cropped Figures** (3 × `mdhn:FigureCrop`)
      - Keyumars  
        ![Keyumars cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/332,517,120,165/max/0/default.jpg)
      - Siamak  
        ![Siamak cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/489,642,106,133/max/0/default.jpg)
      - Hushang  
        ![Hushang cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-20v%2F20v.jpg/205,582,90,180/max/0/default.jpg)    
  - **LinguisticObject**: Verse 232-236 based on Ganjoor




### Folio 21v
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-21v/manifest.json)
- **S C Welch Family Collection** 
  - Instance of Illuminated Folio WD:Q131281679
- **Narrative Episode**
  - WD:Q138757163
- **Depicts**
  - mdhn:Hushang
  - mdhn:BlackDiv
  - mdhn:Siamak
- **Visual Items** 
  - mdhn:Blowing_Horn
  - mdhn:LeopardSkinDress
  - mdhn:Headgear
  - mdhn:Deer
  - mdhn:Gazzele
  - mdhn:Battle
  - mdhn:Lion
  - mdhn:Bird
  - mdhn:Horse
  - mdhn:Plant
  - mdhn:Tree
  - mdhn:Cloud
  - mdhn:Blossom
  - mdhn:Flower
  - mdhn:Bird_Nest
  - mdhn:Club 
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُSultan Muhammad** WD:Q6712884
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Hushang  
        ![Hushang cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/508,1280,195,129/max/0/default.jpg)
      - Black Div  
        ![Black Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/522,1370,343,204/max/0/default.jpg)
      - Div (1)  
        ![Div cropped 1](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/253,1462,176,244/max/0/default.jpg)
      - Div (2)  
        ![Div cropped 2](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/710,1637,219,208/max/0/default.jpg)
      - Div (3)  
        ![Div cropped 3](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/240,1239,268,227/max/0/default.jpg)
      - Div (4)  
        ![Div cropped 4](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/657,1228,275,151/max/0/default.jpg) 
      - Angel (1)  
        ![Angel cropped 1](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/238,949,474,188/max/0/default.jpg)    
      - Angel (2)  
        ![Angel cropped 2](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/524,926,136,100/max/0/default.jpg)              
  - **Inscriptions**: None
  - **Illuminated Unwan**
      - Battle of Hushang against the Divs  
        ![Battle of Hushang against the Divs](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-21v%2F21v.jpg/402,737,407,133/max/0/default.jpg)
  - **LinguisticObject**: Verse 277-289 based on Ganjoor



### Folio 22v (The Feast of Sada)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-22v/manifest.json)
- **Metropolitan Museum of Art** 
  - Instance of Illuminated Folio WD:Q29385197
- **Narrative Episode**
  - WD:Q138757360
- **Depicts**
  - mdhn:Hushang
- **Visual Items** 
  - mdhn:Feasting
  - mdhn:Cloud
  - mdhn:Rock
  - mdhn:LeopardSkinDress
  - mdhn:Turban
  - mdhn:Fire
  - mdhn:Blossom
  - mdhn:Flower
  - mdhn:Tree
  - mdhn:Sheep
  - mdhn:Goat
  - mdhn:Deer
  - mdhn:Gazzele
  - mdhn:Bird
  - mdhn:LongNeckedBottle
  - mdhn:Bowl
  - mdhn:Leopard
  - mdhn:LongNeckedJar
  - mdhn:GoldVessel
  - mdhn:Carpet
  - mdhn:GemEncrustedBelt
  - mdhn:GemEncrustedCrown
  - mdhn:Dagger
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُSultan Muhammad** WD:Q6712884
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Hushang  
        ![Hushang cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-22v%2F22v.jpg/954,1390,378,445/max/0/default.jpg)          
  - **Inscriptions**: None
  - **Illuminated Unwan**: None
  - **LinguisticObject**: Verse 320-333 based on Ganjoor

### Folio 23v (Tahmuras Defeats the Divs)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-23v/manifest.json)
- **Metropolitan Museum of Art** 
  - Instance of Illuminated Folio WD:Q29385197
- **Narrative Episode**
  - WD:Q138676508
- **Depicts**
  - mdhn:Tahmuras
  - mdhn:Div1
  - mdhn:Div2
  - mdhn:Div3
  - mdhn:Div4
- **Visual Items** 
  - mdhn:Mace
  - mdhn:Body_Armour
  - mdhn:Soldier
  - mdhn:Battle
  - mdhn:Wind
  - mdhn:Cloud
  - mdhn:Horse
  - mdhn:Lasso
  - mdhn:Turban
  - mdhn:Flower
  - mdhn:Tree
  - mdhn:Rock
  - mdhn:Blossom
  - mdhn:Bird
  - mdhn:Gazzele
  - mdhn:Plant
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُSultan Muhammad** WD:Q6712884
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Tahmuras  
        ![Tahmuras cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-23v%2F23v.jpg/875,1372,579,536/max/0/default.jpg) 
      - Div 1  
        ![Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-23v%2F23v.jpg/416,1582,497,451/max/0/default.jpg)   
      - Div 2  
        ![Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-23v%2F23v.jpg/771,2074,195,373/max/0/default.jpg)   
      - Div 3  
        ![Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-23v%2F23v.jpg/318,2019,299,426/max/0/default.jpg)   
      - Div 4  
        ![Div cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-23v%2F23v.jpg/923,1847,333,306/max/0/default.jpg)                                            
  - **Inscriptions**: None
  - **Illuminated Unwan**: None
  - **LinguisticObject**: Verse 370-381 based on Ganjoor




