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
  - mdhn:Tree
  - mdhn:Plant
  - mdhn:Cloud
  - mdhn:Bird
  - mdhn:Leopard
  - mdhn:Lion
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




### Folio 21v (Hushang Slays the Black Div)
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

### Folio 82v (One Blow, Sam Recounts How He Slew a Dragon)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-82v/manifest.json)
- **Tehran Museum of Contemporary Art** 
  - Instance of Illuminated Folio (None)
- **Narrative Episode**
  - WD:Q138799749
- **Depicts**
  - mdhn:Sam
  - mdhn:Dragon
- **Visual Items** 
  - mdhn:Body_Armour
  - mdhn:Combat_Helmet
  - mdhn:Bow_and_Arrow
  - mdhn:Turban
  - mdhn:Mace
  - mdhn:Fire
  - mdhn:Rock
  - mdhn:Saddle
  - mdhn:HorseStirrup
  - mdhn:Sword
  - mdhn:Plant
  - mdhn:Tree
  - mdhn:Wind
  - mdhn:Axe
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُQadimi** WD:Q113680330
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Sam  
        ![Sam cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-82v%2FFolio82v.jpg/1434,2782,852,838/max/0/default.jpg) 
      - Dragon  
        ![Dragon cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-82v%2FFolio82v.jpg/311,2237,1188,1528/max/0/default.jpg)                                           
  - **Inscriptions**: None
  - **Illuminated Unwan**: None
  - **LinguisticObject**: Verse 2968-2976 based on Ganjoor



### Folio 102v (Qaran Slays Barman)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-102v/manifest.json)
  - Has Zoomed Scene 
    - ![Scene 1](https://iiif.archive.org/image/iiif/3/AKingsBookofKingsTheShahnamehofShahTahmasp%2FAKingsBookofKingsTheShahnamehofShahTahmasp_jp2.zip%2FAKingsBookofKingsTheShahnamehofShahTahmasp_jp2%2FAKingsBookofKingsTheShahnamehofShahTahmasp_0138.jp2/full/300,/0/default.jpg)
      - [Full Size](https://iiif.archive.org/image/iiif/3/AKingsBookofKingsTheShahnamehofShahTahmasp%2FAKingsBookofKingsTheShahnamehofShahTahmasp_jp2.zip%2FAKingsBookofKingsTheShahnamehofShahTahmasp_jp2%2FAKingsBookofKingsTheShahnamehofShahTahmasp_0138.jp2/full/max/0/default.jpg)
- **Victoria and Albert Museum** 
  - Instance of Illuminated Folio WD:Q64690773
- **Narrative Episode**
  - WD:Q138847591
- **Depicts**
  - mdhn:Qaran
  - mdhn:Barman
  - mdhn:Qubad
- **Visual Items** 
  - mdhn:Body_Armour
  - mdhn:Combat_Helmet
  - mdhn:Bow_and_Arrow
  - mdhn:Spear
  - mdhn:Horse_Armour
  - mdhn:Battle_Field
  - mdhn:CurvedSorna
  - mdhn:Sorna
  - mdhn:Horse
  - mdhn:Camel
  - mdhn:Tamborim
  - mdhn:Flag
  - mdhn:Fire
  - mdhn:Shield
  - mdhn:Saddle
  - mdhn:HorseStirrup
  - mdhn:Dagger
  - mdhn:Sword
  - mdhn:Moon
  - mdhn:Star
  - mdhn:Blossom
  - mdhn:Tree
  - mdhn:Wind
  - mdhn:Flower
  - mdhn:Rock
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **Abd al Aziz** WD:Q21663724
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Qaran  
        ![Qaran cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-102v%2FFolio102v.jpeg/647,1997,724,675/max/0/default.jpg) 
      - Barman 
        ![Barman cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-102v%2FFolio102v.jpeg/1189,2209,891,531/max/0/default.jpg)   
                                            
  - **Inscriptions**: None
  - **Illuminated Unwan** None
  - **LinguisticObject**: Verse 3781-3791 based on Ganjoor  




### Folio 339r (Planning for the Joust of the Twelve Rooks)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-339r/manifest.json)
  - Has Alternate 
    - [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-339r-alt/manifest.json)
- **National Museum of Asian Art** 
  - Instance of Illuminated Folio WD:Q29385197
- **Narrative Episode**
  - WD:Q5935469
- **Depicts**
  - mdhn:KayKhosrow
  - mdhn:Goudarz
  - mdhn:Afrasiab
  - mdhn:PiranViseh
- **Visual Items** 
  - mdhn:Tent
  - mdhn:LongNeckedBottle
  - mdhn:LongNeckedJar
  - mdhn:Dagger
  - mdhn:Sword
  - mdhn:Headgear
  - mdhn:Horse
  - mdhn:SunShade
  - mdhn:Carpet
  - mdhn:Flower
  - mdhn:Plant
  - mdhn:Tree
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُMirza Ali** WD:Q2783517
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Goudarz  
        ![Goudarz cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-339r-alt%2FFolio339r_alt.jpg/1504,1731,436,717/max/0/default.jpg) 
      - Piran Viseh  
        ![Piran Viseh cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-339r-alt%2FFolio339r_alt.jpg/1178,1859,304,581/max/0/default.jpg)   
                                            
  - **Inscriptions**: None
  - **Illuminated Unwan**: None
  - **LinguisticObject**: Verse 18750-18758 based on Ganjoor


### Folio 341v (The First 'Joust of the Rooks': Fariburz versus Kalbad)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-341v/manifest.json)
- **Aga Khan Museum** 
  - Instance of Illuminated Folio WD:Q113699030
- **Narrative Episode**
  - WD:Q5935469 and WD:Q138949719
- **Depicts**
  - mdhn:KayKhosrow
  - mdhn:Goudarz
  - mdhn:Afrasiab
  - mdhn:Fariburz
  - mdhn:Colbad_Viseh
- **Visual Items** 
  - mdhn:Bow_and_Arrow
  - mdhn:Sword
  - mdhn:Shield
  - mdhn:Horse_Armour
  - mdhn:Helmet 
  - mdhn:Battle_Field
  - mdhn:Duel
  - mdhn:Flag
  - mdehn:Horse
  - mdhn:Saddle
  - mdhn:HorseStirrup
  - mdhn:Rock
  - mdhn:Tree
  - mdhn:Flower
  - mdhn:Plant
  - mdhn:Goat
  - mdhn:Bird
  - mdhn:Bird_Nest
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **ُMirza Ali** WD:Q4522484
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Fariburz  
        ![Firuz cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-341v%2FFolio341v.jpg/791,1384,513,500/max/0/default.jpg) 
      - Piran Viseh  
        ![Kalbad cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-341v%2FFolio341v.jpg/344,1385,505,527/max/0/default.jpg)   
                                            
  - **Inscriptions**: None
  - **Illuminated Unwan**
      - Slaying Kalbad By Fariburz 
        ![Slaying Kalbad By Fariburz](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-341v%2FFolio341v.jpg/552,708,503,228/max/0/default.jpg)
  - **LinguisticObject**: Verse 18780-18783 based on Ganjoor


### Folio 342r (The Fourth 'Joust of the Rooks': Faruhil versus Zangula)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-342r/manifest.json)
  - Has Alternate 
    - [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-342r-alt/manifest.json)
- **Metropolitan Museum Of Art** 
  - Instance of Illuminated Folio WD:Q139055183
- **Narrative Episode**
  - WD:Q5935469 and WD:Q138964109
- **Depicts**
  - mdhn:KayKhosrow
  - mdhn:Goudarz
  - mdhn:Afrasiab
  - mdhn:Ferehoul
  - mdhn:Zangaleh
- **Visual Items** 
  - mdhn:Bow_and_Arrow
  - mdhn:Sword
  - mdhn:Horse_Armour
  - mdhn:Helmet 
  - mdhn:Battle_Field
  - mdhn:Duel
  - mdhn:Flag
  - mdehn:Horse
  - mdhn:Saddle
  - mdhn:HorseStirrup
  - mdhn:Rock
  - mdhn:Tree
  - mdhn:Cloud
  - mdhn:Flower
  - mdhn:Plant
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **Qasim ibn Ali** WD:Q60311831
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Ferehoul  
        ![Ferehoul cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-342r-alt%2FFolio342r_alt.jpg/335,1918,836,901/max/0/default.jpg) 
      - Zangaleh 
        ![Zangaleh cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-342r-alt%2FFolio342r_alt.jpg/1269,1833,938,843/max/0/default.jpg)   
                                            
  - **Inscriptions**: None
  - **Illuminated Unwan**
      - Slaying Zangaleh By Ferehoul 
        ![Slaying Zangaleh By Ferehoul](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-342r-alt%2FFolio342r_alt.jpg/788,284,942,393/max/0/default.jpg)
  - **LinguisticObject**: Verse 18887-18898 based on Ganjoor  



### Folio 343r (The Seventh 'Joust of the Rooks': Hajir versus Sipahram)
- [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-343r/manifest.json)
  - Has Alternate 
    - [IIIF Manifest](https://demo.viewer.glycerine.io/viewer?iiif-content=https://iiif.archive.org/iiif/3/shahnama-shah-tahmasp-343r-alt/manifest.json)
- **Metropolitan Museum Of Art** 
  - Instance of Illuminated Folio WD:Q139073014
- **Narrative Episode**
  - WD:Q5935469 and WD:Q139072642
- **Depicts**
  - mdhn:KayKhosrow
  - mdhn:Goudarz
  - mdhn:Afrasiab
  - mdhn:Hojir
  - mdhn:Sepahram
- **Visual Items** 
  - mdhn:Bow_and_Arrow
  - mdhn:Sword
  - mdhn:Horse_Armour
  - mdhn:Helmet 
  - mdhn:Battle_Field
  - mdhn:Duel
  - mdhn:Flag
  - mdehn:Horse
  - mdhn:Saddle
  - mdhn:HorseStirrup
  - mdhn:Rock
  - mdhn:Tree
  - mdhn:Cloud
  - mdhn:Flower
  - mdhn:Plant
- **Content Elements**
  - **Painting** (`mdhn:Painting`) 
    - **Abd al Vahhab** WD:Q59482128
    - **Cropped Figures** (multiple `mdhn:FigureCrop`)
      - Hojir  
        ![Hojir cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-343v-alt%2FFolio343v_alt.jpg/1177,2064,825,796/max/0/default.jpg) 
      - Sepahram 
        ![Sepahram cropped](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-343v-alt%2FFolio343v_alt.jpg/445,2021,835,598/max/0/default.jpg)   
                                            
  - **Inscriptions**: None
  - **Illuminated Unwan**
      - Slaying Sepahram By Sepahram
        ![Slaying Sepahram By Sepahram](https://iiif.archive.org/image/iiif/3/shahnama-shah-tahmasp-343v-alt%2FFolio343v_alt.jpg/744,254,932,308/max/0/default.jpg)
  - **LinguisticObject**: Verse 18933-18945 based on Ganjoor  
