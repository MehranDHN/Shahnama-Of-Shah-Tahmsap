# شاهنامه شاه طهماسب — Shahnama of Shah Tahmasp
## A LOUD / FAIR Knowledge Graph in RDF / OWL

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![OWL Version](https://img.shields.io/badge/Ontology-v3.0.0-blue)](mdhn-starter_ontology.ttl)
[![Wikidata](https://img.shields.io/badge/Wikidata-Q3114572-orange)](https://www.wikidata.org/wiki/Q3114572)

---

## Introduction

The **Shahnama of Shah Tahmasp** (شاهنامه شاه طهماسب) is widely regarded as the most magnificent illustrated manuscript ever created. Produced in Tabriz between approximately **1522 and 1535 CE** under the patronage of the Safavid ruler Shah Tahmasp I (r. 1524–1576), it is a royal edition of the *Shahnameh* ("Book of Kings") — the Iranian national epic composed by the poet Ferdowsi (c. 977–1010 CE). The manuscript originally contained **258 folios of text** and an extraordinary cycle of **268 full-page paintings**, executed by some of the most celebrated artists of the Safavid court, including Sultan Muhammad, Āqā Mīrak, and Qadimi.

After residing in the Safavid royal library, the manuscript was gifted to the Ottoman Sultan Selim II in 1568, held at the Topkapı Palace Library for over three centuries, and acquired in 1959 by American collector **Arthur A. Houghton Jr.**, who disbind it — donating 78 folios to the Metropolitan Museum of Art and selling the remainder through Christie's in 1970. Today, folios are dispersed across **more than 30 collections** worldwide.

This repository models the manuscript, its folios, paintings, narrative episodes, iconographic entities, scribes, painters, and institutional holders as a richly interlinked **knowledge graph** following:

- **LOUD** (Linked Open Usable Data) — Turtle serialisation accessible to both humans and machines
- **FAIR** (Findable, Accessible, Interoperable, Reusable) — authoritative identifiers from Wikidata, Getty AAT/ULAN/TGN, and IIIF
- **CIDOC-CRM 7.1** — international museum standard for cultural heritage event modelling
- **Linked Art** — community profile for art objects
- **IIIF Presentation API 3** — deep-zoom, region-based image access for every folio and character crop
- **FHKB (Family History Knowledge Base)** — formal OWL encoding of the *Shahnameh*'s dynastic genealogies

---

## Repository Structure

```
.
├── mdhn-starter_ontology.ttl   # MDHN OWL ontology (v3.0.0) — classes and properties
├── fhkb.ttl                    # FHKB genealogy ontology — kinship model
├── fhkb-integration.svg        # Architecture diagram (embedded below)
├── resources.ttl               # Sample instance data (folios 7r, 20v–23v, 38v)
└── README.md                   # This file
```

---

## Ontology Walkthrough

The ontology is declared in the `mdhn:` namespace (`http://example.com/mdhn/ontology#`) at **version 3.0.0**. It imports OWL, RDFS, SKOS, Dublin Core, FOAF, CIDOC-CRM, Linked Art, IIIF, Getty vocabularies, and Wikidata.

### Namespace Conventions

- **Hierarchy in IRI paths** uses `/` as part of the base URI, e.g. `folio:20v` → `<http://example.com/mdhn/resource/folio/20v>`
- **Compound local names** use `_` (underscore) exclusively — never hyphens or camelCase

| Prefix | Namespace | Purpose |
|---|---|---|
| `mdhn:` | `…/ontology#` | Class & property definitions |
| `folio:` | `…/resource/folio/` | Folio instances |
| `painting:` | `…/resource/painting/` | Painting instances |
| `episode:` | `…/resource/episode/` | Narrative episodes |
| `character:` | `…/resource/character/` | Epic characters |
| `crop:` | `…/resource/crop/` | Figure crops |
| `agent:` | `…/resource/agent/` | Persons & organisations |
| `entry:` | `…/resource/entry/` | Register entries |
| `ownership:` | `…/resource/ownership/` | Ownership intervals |
| `fhkb:` | `…/genealogy.owl#` | FHKB kinship axioms |

---

### Class Hierarchy

#### The Manuscript

`mdhn:Manuscript` (AAT `aat:300028569`) is the top-level physical object. The single named individual `mdhn:manuscript_shahnama_shah_tahmasp` carries Dublin Core metadata, Wikidata links, and pointers to its ownership history and painting register.

#### Folio Model

```
mdhn:Folio
 ├── mdhn:Recto            — front (right-hand) side, labelled 'r'
 ├── mdhn:Verso            — back (left-hand) side, labelled 'v'
 ├── mdhn:AlternateFolio   — replacement or variant at a given position
 └── mdhn:OttomanAnnotationLeaf — Ottoman-period annotation leaves
```

Every folio instance carries `mdhn:folioNumber`, `mdhn:isFolioOf`, `mdhn:nextFolio`/`mdhn:previousFolio`, `mdhn:hasContentElement`, `mdhn:hasIIIFManifest`, `mdhn:keptIn`, and `mdhn:hasRegisterEntry`.

`mdhn:FolioType` enumerates all documentary forms: `painted`, `illuminated`, `text_only`, `mixed`, `double_page_spread`, `unvan`, `sarlowh`, `colophon`, `ottoman_annotation`, and `flyleaf`.

#### Content Elements

```
mdhn:ContentElement
 ├── mdhn:Painting         (≡ crm:E36_Visual_Item; AAT aat:300033799)
 │    └── mdhn:FigureCrop  — IIIF region crop isolating one character
 ├── mdhn:Illumination     (AAT aat:300053433)
 │    ├── mdhn:IlluminatedUnwan
 │    └── mdhn:Shamseh
 ├── mdhn:LinguisticObject
 │    ├── mdhn:PoeticText
 │    └── mdhn:ProseText
 └── mdhn:Inscription      (AAT aat:300028702)
```

`mdhn:FigureCrop` (subclass of `mdhn:Painting`, introduced v3) represents a cropped IIIF region isolating one character. Key properties: `mdhn:isExtractedFrom` → parent painting, `mdhn:representsEntity` → iconographic entity, and `mdhn:iiifRegionURL` (full IIIF Image API URL with pixel region).

#### Iconographic Entities

```
mdhn:IconographicEntity
 ├── mdhn:NarrativeEpisode    — a scene or event from the epic
 ├── mdhn:LegendaryCharacter  — mythological hero or villain
 ├── mdhn:HistoricalFigure    — identifiable historical person
 └── mdhn:MythologicalCreature — divs, angels, Simorgh, etc.
```

All entities are reconciled to Wikidata via `mdhn:wikidataItem` (a subproperty of `skos:exactMatch`).

#### Agents and Attribution Roles

| Property | Inverse | Role |
|---|---|---|
| `mdhn:hasPainter` | `mdhn:participatesAsPainter` | Primary painter |
| `mdhn:hasWorkshop_director` | `mdhn:participatesAsWorkshop_director` | Atelier director |
| `mdhn:hasIlluminator` | `mdhn:participatesAsIlluminator` | Illuminator |
| `mdhn:hasScriber` | `mdhn:participatesAsScriber` | Calligrapher |
| `mdhn:hasAuthor` | `mdhn:participatesAsAuthor` | Poet / author |
| `mdhn:hasBinder` | `mdhn:participatesAsBinder` | Bookbinder |

#### Provenance — Ownership Intervals

`mdhn:OwnershipInterval` (subclass of `crm:E8_Acquisition`) records periods of ownership with `mdhn:owner`, `mdhn:ownershipStart`/`End` (xsd:gYear), and `mdhn:transferType` (`gift | purchase | auction | confiscation | bequest | dispersal | deposit`).

| Interval | Owner | Years | Transfer |
|---|---|---|---|
| `mdhn:safavid_library` | Shah Tahmasp I | 1522–1568 | Gift to Ottoman Sultan |
| `mdhn:ottoman_topkapi` | Sultan Selim II | 1568–1903 | — |
| `mdhn:houghton_collection` | Arthur A. Houghton Jr. | 1959–1972 | Purchase; partial donation |

#### Painting Register

`mdhn:PaintingRegister` (subclass of `crm:E31_Document`) is the authoritative checklist of all 268 expected paintings. A `mdhn:RegisterEntry` with no `mdhn:hasRegisterEntry` inverse link signals a **missing** painting — a core research question the graph is designed to answer.

---

## FHKB Genealogy Ontology Integration

> **This is a critical and foundational component of the project.** The narrative logic of the *Shahnameh* is inseparable from dynastic genealogy. Characters appear together in paintings precisely because of their kinship: Hushang avenges his father Siamak who was murdered by the Black Div; Faridun's three sons Salm, Tur, and Iraj divide the world before Salm and Tur murder Iraj in envy. Without a formal model of these relationships, the knowledge graph captures *who is depicted* but cannot explain *why they are depicted together*. The FHKB provides that missing explanatory layer.

### What is FHKB?

The **Family History Knowledge Base** (`fhkb.ttl`) is a well-known OWL 2 ontology designed to model human genealogy as a benchmark for OWL reasoning. It defines a rich lattice of kinship classes and property chains from which a reasoner can infer extended family relationships automatically:

- `fhkb:Person` — root class; `fhkb:Man` and `fhkb:Woman` are disjoint subclasses defined via sex restrictions
- `fhkb:Marriage` — reified marriage event with `fhkb:hasMalePartner` / `fhkb:hasFemalePartner`
- Direct kinship: `fhkb:hasFather`, `fhkb:hasMother`, `fhkb:hasSon`, `fhkb:hasDaughter` (all functional)
- Sibling relations: `fhkb:isSiblingOf` (symmetric, transitive), `fhkb:isBrotherOf`, `fhkb:isSisterOf`
- Generational chains: `fhkb:hasGrandParent`, `fhkb:hasGreatGrandParent` defined as OWL property chains (`hasParent ∘ hasParent`, etc.)
- Extended kin: `fhkb:hasUncle`, `fhkb:hasAunt`, `fhkb:isFirstCousinOf`, `fhkb:isSecondCousinOf`, `fhkb:isThirdCousinOf`
- Ancestor closure: `fhkb:hasAncestor` (transitive), `fhkb:isAncestorOf`

The critical feature is **OWL property chain inference**: once `fhkb:hasFather` and `fhkb:hasMother` triples are asserted for a character, a reasoner automatically computes grandparents, great-grandparents, siblings, cousins, and the full ancestor graph without additional assertions.

---

### Integration Architecture

<p align="center">
  <img src="./fhkb-integration.svg" alt="FHKB Integration Architecture" width="100%"/>
</p>

The integration proceeds in three tiers:

**Tier 1 — FHKB Ontology** provides the formal kinship axioms. The `fhkb:Person` hierarchy (Man/Woman via sex restrictions), the kinship object property lattice, and OWL 2 property chain axioms form a self-contained reasoning substrate.

**Tier 2 — Integration Bridge** establishes the mappings between namespaces. The core assertion: `mdhn:EpicEntity` is treated as equivalent to `fhkb:Person` for genealogical reasoning. Any epic character can be typed as `fhkb:Man` or `fhkb:Woman` and linked via FHKB kinship properties, allowing the sex-restricted property chains to fire correctly.

**Tier 3 — Knowledge Graph Enrichment** is the payoff: an OWL reasoner (HermiT, Pellet, or Stardog's built-in reasoner) infers the full dynastic lineage of every character, making all family relationships available as SPARQL-queryable triples and enabling iconographic queries grounded in genealogical explanation.

---

### Class and Property Mappings

| MDHN concept | FHKB mapping | Notes |
|---|---|---|
| `mdhn:EpicEntity` | ≡ `fhkb:Person` | Via `owl:equivalentClass` |
| Male epic characters | `rdf:type fhkb:Man` | e.g. Keyumars, Hushang, Faridun |
| Female epic characters | `rdf:type fhkb:Woman` | e.g. Faranak, Arnavaz, Shahrnaz |
| Father–son link | `fhkb:hasFather` | Functional property |
| Mother–child link | `fhkb:hasMother` | Functional property |
| Sibling bond | `fhkb:isSiblingOf` | Symmetric + transitive |
| Spousal union | `fhkb:Marriage` + partners | Reified event |
| Ancestor chain | `fhkb:hasAncestor` | Transitive; inferred |
| Cousin relation | `fhkb:isFirstCousinOf` | Via property chain |

---

### Integration Example — The Mythological Dynasty (Turtle)

The following snippet encodes the three-generation lineage from Keyumars to Hushang. After loading into a reasoner, `fhkb:hasGrandParent`, `fhkb:hasAncestor`, and `fhkb:isSiblingOf` triples are automatically inferred:

```turtle
@prefix mdhn: <http://example.com/mdhn/ontology#> .
@prefix fhkb: <http://www.example.com/genealogy.owl#> .

mdhn:Keyumars  a mdhn:EpicEntity, fhkb:Man .
mdhn:Siamak    a mdhn:EpicEntity, fhkb:Man .
mdhn:Hushang   a mdhn:EpicEntity, fhkb:Man .
mdhn:Faridun   a mdhn:EpicEntity, fhkb:Man .
mdhn:Faranak   a mdhn:EpicEntity, fhkb:Woman .
mdhn:Salm      a mdhn:EpicEntity, fhkb:Man .
mdhn:Tur       a mdhn:EpicEntity, fhkb:Man .
mdhn:Iraj      a mdhn:EpicEntity, fhkb:Man .

# Generation 1 → 2: Keyumars → Siamak
mdhn:Siamak    fhkb:hasFather mdhn:Keyumars .

# Generation 2 → 3: Siamak → Hushang
mdhn:Hushang   fhkb:hasFather mdhn:Siamak .

# Faridun's sons (the fratricidal triad)
mdhn:Salm  fhkb:hasFather mdhn:Faridun ; fhkb:hasMother mdhn:Faranak .
mdhn:Tur   fhkb:hasFather mdhn:Faridun ; fhkb:hasMother mdhn:Faranak .
mdhn:Iraj  fhkb:hasFather mdhn:Faridun ; fhkb:hasMother mdhn:Faranak .
```

**Automatically inferred triples (no additional assertions needed):**
- `mdhn:Hushang fhkb:hasGrandParent mdhn:Keyumars`
- `mdhn:Hushang fhkb:hasAncestor mdhn:Keyumars`
- `mdhn:Salm fhkb:isSiblingOf mdhn:Tur`
- `mdhn:Salm fhkb:isBrotherOf mdhn:Iraj`
- `mdhn:Tur fhkb:isSiblingOf mdhn:Iraj`

---

### SPARQL Queries — Genealogy-Aware

Add `PREFIX fhkb: <http://www.example.com/genealogy.owl#>` to the base prefix block below.

#### Q-G1 — Find all paintings depicting at least two sibling characters

```sparql
SELECT DISTINCT ?painting ?folioNumber ?char1Label ?char2Label
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasReferredTo ?char1 ;
            mdhn:hasReferredTo ?char2 .
  ?char1 fhkb:isSiblingOf ?char2 .
  FILTER(?char1 != ?char2)
  ?char1 rdfs:label ?char1Label . FILTER(LANG(?char1Label)="en")
  ?char2 rdfs:label ?char2Label . FILTER(LANG(?char2Label)="en")
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

#### Q-G2 — Find paintings depicting a character and any of their ancestors

```sparql
SELECT ?painting ?folioNumber ?characterLabel ?ancestorLabel
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasReferredTo ?character ;
            mdhn:hasReferredTo ?ancestor .
  ?character fhkb:hasAncestor ?ancestor .
  FILTER(?character != ?ancestor)
  ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en")
  ?ancestor  rdfs:label ?ancestorLabel  . FILTER(LANG(?ancestorLabel)="en")
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

#### Q-G3 — Retrieve the full dynastic lineage of a character by generation

```sparql
SELECT ?ancestor ?ancestorLabel ?generation
WHERE {
  {
    SELECT ?ancestor (1 AS ?generation)
    WHERE { mdhn:Hushang fhkb:hasParent ?ancestor . }
  } UNION {
    SELECT ?ancestor (2 AS ?generation)
    WHERE { mdhn:Hushang fhkb:hasGrandParent ?ancestor . }
  } UNION {
    SELECT ?ancestor (3 AS ?generation)
    WHERE { mdhn:Hushang fhkb:hasGreatGrandParent ?ancestor . }
  }
  ?ancestor rdfs:label ?ancestorLabel . FILTER(LANG(?ancestorLabel)="en")
}
ORDER BY ?generation
```

#### Q-G4 — Find all fraternal (sibling) co-appearance paintings

```sparql
SELECT ?painting ?folioNumber ?sib1Label ?sib2Label ?episodeLabel
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasReferredTo ?sib1 ;
            mdhn:hasReferredTo ?sib2 .
  ?sib1 fhkb:isBrotherOf ?sib2 .
  FILTER(?sib1 != ?sib2)
  OPTIONAL { ?painting mdhn:hasNarrativeEpisode ?ep . ?ep rdfs:label ?episodeLabel . FILTER(LANG(?episodeLabel)="en") }
  ?sib1 rdfs:label ?sib1Label . FILTER(LANG(?sib1Label)="en")
  ?sib2 rdfs:label ?sib2Label . FILTER(LANG(?sib2Label)="en")
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
}
```

#### Q-G5 — List all paintings where protagonist confronts an ancestrally related figure

```sparql
SELECT ?painting ?folioNumber ?heroLabel ?antagonistLabel
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasReferredTo ?hero ;
            mdhn:hasReferredTo ?antagonist .
  ?hero fhkb:hasAncestor ?antagonist .
  FILTER(?hero != ?antagonist)
  ?hero rdfs:label ?heroLabel . FILTER(LANG(?heroLabel)="en")
  ?antagonist rdfs:label ?antagonistLabel . FILTER(LANG(?antagonistLabel)="en")
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

---

## Fine-Grained Iconography

The existing iconographic model captures content at the level of narrative episodes, character co-occurrences, and IIIF figure crops. The richness of Safavid manuscript painting calls for a substantially more granular vocabulary. Below is the current state, followed by concrete proposals for enhancement.

### Current State

- `mdhn:IconographicEntity` with four subclasses (NarrativeEpisode, LegendaryCharacter, HistoricalFigure, MythologicalCreature)
- `mdhn:FigureCrop` with IIIF region URLs for character-level image extraction
- `mdhn:depicts` / `mdhn:hasReferredTo` / `mdhn:hasNarrativeEpisode` on paintings
- `mdhn:attributionCertainty` (`certain | probable | possible | disputed | unknown`)
- Wikidata reconciliation via `mdhn:wikidataItem`

### Proposed Enhancements

---

#### 1. Scene Type Taxonomy

Persian manuscript paintings follow a limited set of canonical compositions. Formal scene types enable computational clustering and cross-manuscript comparisons:

```turtle
mdhn:SceneType a owl:Class ;
    rdfs:label "Scene type"@en ;
    skos:exactMatch aat:300015637 .

mdhn:hasSceneType a owl:ObjectProperty ;
    rdfs:domain mdhn:Painting ;
    rdfs:range  mdhn:SceneType ;
    rdfs:label  "has scene type"@en .

mdhn:sceneType_enthronement     a mdhn:SceneType ; rdfs:label "Enthronement"@en .
mdhn:sceneType_battle           a mdhn:SceneType ; rdfs:label "Battle"@en .
mdhn:sceneType_hunt             a mdhn:SceneType ; rdfs:label "Royal hunt"@en .
mdhn:sceneType_court            a mdhn:SceneType ; rdfs:label "Court assembly"@en .
mdhn:sceneType_lamentation      a mdhn:SceneType ; rdfs:label "Lamentation"@en .
mdhn:sceneType_divine_visitation a mdhn:SceneType ; rdfs:label "Divine visitation"@en .
mdhn:sceneType_tribute          a mdhn:SceneType ; rdfs:label "Tribute scene"@en .
mdhn:sceneType_duel             a mdhn:SceneType ; rdfs:label "Single combat"@en .
```

---

#### 2. Visual Attribute and Iconographic Prop Taxonomy

Characters in the *Shahnameh* are identified by distinctive attributes: Kayumars by leopard-skin garments, Tahmuras by his demon-binding rope, Hushang by flint-struck fire. Encoding these as typed resources enables iconographic identification across images even when inscriptions are absent:

```turtle
mdhn:VisualAttribute a owl:Class ;
    rdfs:label "Visual attribute"@en .

mdhn:Garment         a owl:Class ; rdfs:subClassOf mdhn:VisualAttribute ;
    rdfs:label "Garment"@en ; skos:exactMatch aat:300266639 .
mdhn:IconographicProp a owl:Class ; rdfs:subClassOf mdhn:VisualAttribute ;
    rdfs:label "Iconographic prop"@en .
mdhn:GesturePosture  a owl:Class ; rdfs:subClassOf mdhn:VisualAttribute ;
    rdfs:label "Gesture / posture"@en ; skos:exactMatch aat:300055127 .

mdhn:hasVisualAttribute a owl:ObjectProperty ;
    rdfs:domain [ owl:unionOf (mdhn:FigureCrop mdhn:Painting) ] ;
    rdfs:range  mdhn:VisualAttribute ;
    rdfs:label  "has visual attribute"@en .

mdhn:prop_leopardSkinRobe  a mdhn:Garment ; rdfs:label "Leopard-skin robe"@en .
mdhn:prop_demonBindingRope a mdhn:IconographicProp ; rdfs:label "Demon-binding rope"@en .
mdhn:prop_flintRock        a mdhn:IconographicProp ; rdfs:label "Flint rock (fire discovery)"@en .
mdhn:prop_crown_kayani     a mdhn:IconographicProp ; rdfs:label "Kayani crown"@en ; skos:exactMatch aat:300046300 .
mdhn:gesture_enthroned     a mdhn:GesturePosture  ; rdfs:label "Seated enthroned"@en .
mdhn:gesture_mounted       a mdhn:GesturePosture  ; rdfs:label "Mounted on horseback"@en .
mdhn:gesture_prostrate     a mdhn:GesturePosture  ; rdfs:label "Prostrate in submission"@en .
```

---

#### 3. Figure Scale and Compositional Hierarchy

In Persian painting, **hierarchical figure scaling** is the primary device for expressing status: the most important figure is the largest regardless of spatial perspective. Encoding relative scale enables analysis of visual hierarchy across the manuscript:

```turtle
mdhn:figureScale a owl:DatatypeProperty ;
    rdfs:domain mdhn:FigureCrop ;
    rdfs:range  xsd:string ;
    rdfs:comment "Controlled: 'dominant' | 'secondary' | 'tertiary' | 'crowd'."@en .

mdhn:CompositionZone a owl:Class ;
    rdfs:label "Composition zone"@en .

mdhn:hasCompositionZone a owl:ObjectProperty ;
    rdfs:domain mdhn:FigureCrop ;
    rdfs:range  mdhn:CompositionZone .

mdhn:zone_foreground   a mdhn:CompositionZone ; rdfs:label "Foreground"@en .
mdhn:zone_middleground a mdhn:CompositionZone ; rdfs:label "Middle-ground"@en .
mdhn:zone_background   a mdhn:CompositionZone ; rdfs:label "Background"@en .
mdhn:zone_upper_margin a mdhn:CompositionZone ; rdfs:label "Upper margin"@en .
```

---

#### 4. Landscape and Architectural Frame Elements

Safavid paintings are characterised by distinctive landscape conventions (rocky outcrops, flowering meadows, gold-leaf skies) and architectural frames (tiled pavilions, arched iwans). These are iconographically significant and link paintings to specific workshop styles and dating:

```turtle
mdhn:EnvironmentalElement a owl:Class ;
    rdfs:label "Environmental element"@en ;
    rdfs:subClassOf mdhn:ContentElement .

mdhn:LandscapeFeature  a owl:Class ; rdfs:subClassOf mdhn:EnvironmentalElement ;
    rdfs:label "Landscape feature"@en .
mdhn:ArchitecturalFrame a owl:Class ; rdfs:subClassOf mdhn:EnvironmentalElement ;
    rdfs:label "Architectural frame"@en ; skos:exactMatch aat:300000885 .

mdhn:hasEnvironmentalElement a owl:ObjectProperty ;
    rdfs:domain mdhn:Painting ;
    rdfs:range  mdhn:EnvironmentalElement .

mdhn:env_rockyOutcrop    a mdhn:LandscapeFeature  ; rdfs:label "Rocky outcrop"@en .
mdhn:env_floweringMeadow a mdhn:LandscapeFeature  ; rdfs:label "Flowering meadow"@en .
mdhn:env_goldenSky       a mdhn:LandscapeFeature  ; rdfs:label "Gold-leaf sky"@en .
mdhn:env_iwan            a mdhn:ArchitecturalFrame ; rdfs:label "Iwan arch"@en ; skos:exactMatch aat:300002844 .
mdhn:env_tiledPavilion   a mdhn:ArchitecturalFrame ; rdfs:label "Tiled pavilion"@en .
```

---

#### 5. Iconographic Program

A group of paintings may form a coherent **iconographic program** — a planned visual cycle conveying a thematic argument across multiple folios. The Shahnama of Shah Tahmasp has a clearly identifiable "Mythological Age" cycle (ff. 20v–38v) and several heroic cycles:

```turtle
mdhn:IconographicProgram a owl:Class ;
    rdfs:label "Iconographic program"@en ;
    skos:exactMatch aat:300067450 .

mdhn:partOfProgram a owl:ObjectProperty ;
    rdfs:domain mdhn:Painting ;
    rdfs:range  mdhn:IconographicProgram .

mdhn:program_mythological_age a mdhn:IconographicProgram ;
    rdfs:label "Mythological Age cycle (ff. 20v–38v)"@en .
mdhn:program_rustam_cycle a mdhn:IconographicProgram ;
    rdfs:label "Rustam heroic cycle"@en .
```

---

#### 6. Cross-Manuscript Parallels

Linking paintings to iconographically parallel scenes in other *Shahnameh* manuscripts enables comparative art-historical analysis across the tradition:

```turtle
mdhn:hasParallelIn a owl:ObjectProperty, owl:SymmetricProperty ;
    rdfs:domain mdhn:Painting ;
    rdfs:range  mdhn:Painting ;
    rdfs:label  "has iconographic parallel in"@en .

mdhn:parallelConfidence a owl:DatatypeProperty ;
    rdfs:range xsd:string ;
    rdfs:comment "Values: 'direct_copy' | 'close_variant' | 'shared_prototype' | 'thematic_parallel'."@en .
```

---

#### 7. Pigment and Material Analysis

Where technical analysis (XRF, Raman spectroscopy) has identified specific pigments, linking those results to the knowledge graph enables provenance and workshop attribution studies:

```turtle
mdhn:PigmentAnalysis a owl:Class ;
    rdfs:subClassOf crm:E13_Attribute_Assignment ;
    rdfs:label "Pigment analysis"@en ;
    skos:exactMatch aat:300389306 .

mdhn:hasPigmentAnalysis a owl:ObjectProperty ;
    rdfs:domain mdhn:Painting ;
    rdfs:range  mdhn:PigmentAnalysis .

mdhn:identifiedPigment a owl:ObjectProperty ;
    rdfs:domain mdhn:PigmentAnalysis ;
    rdfs:range  owl:Thing ;
    rdfs:comment "Link to Getty AAT pigment concept, e.g. aat:300011098 (lapis lazuli)."@en .

mdhn:analysisMethod a owl:DatatypeProperty ;
    rdfs:domain mdhn:PigmentAnalysis ;
    rdfs:range  xsd:string .
```

---

#### 8. Expanded Supernatural Creature Taxonomy

`mdhn:MythologicalCreature` currently covers all non-human entities. The *Shahnameh* has a rich taxonomy of supernatural beings with distinct iconographic conventions that merit subclassing:

```turtle
mdhn:Div a owl:Class ;
    rdfs:subClassOf mdhn:MythologicalCreature ;
    rdfs:label "Div (demon)"@en , "ديو"@fa ;
    skos:exactMatch wd:Q1157107 .

mdhn:Simorgh a owl:Class ;
    rdfs:subClassOf mdhn:MythologicalCreature ;
    rdfs:label "Simorgh"@en , "سيمرغ"@fa ;
    skos:exactMatch wd:Q193590 .

mdhn:Ahriman_class a owl:Class ;
    rdfs:subClassOf mdhn:MythologicalCreature ;
    rdfs:label "Ahriman"@en , "اهريمن"@fa ;
    skos:exactMatch wd:Q193928 .

mdhn:Angel a owl:Class ;
    rdfs:subClassOf mdhn:MythologicalCreature ;
    rdfs:label "Angel (Yazata)"@en , "فرشته"@fa ;
    skos:exactMatch wd:Q235113 .
```

---

### Fine-Grained Iconography SPARQL Queries

#### Q-I1 — Find all paintings of a given scene type

```sparql
SELECT ?painting ?folioNumber ?painterLabel
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasSceneType mdhn:sceneType_enthronement .
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
  OPTIONAL { ?painting mdhn:hasPainter ?p . ?p rdfs:label ?painterLabel . }
}
ORDER BY ?folioNumber
```

#### Q-I2 — Retrieve all figure crops carrying a specific iconographic prop

```sparql
SELECT ?cropLabel ?characterLabel ?folioNumber
WHERE {
  ?crop a mdhn:FigureCrop ;
        mdhn:hasVisualAttribute mdhn:prop_leopardSkinRobe ;
        mdhn:hasReferredTo ?character .
  ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en")
  OPTIONAL { ?crop rdfs:label ?cropLabel . FILTER(LANG(?cropLabel)="en") }
  ?painting mdhn:hasFigureCrop ?crop .
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
}
```

#### Q-I3 — List all paintings in the Mythological Age iconographic program

```sparql
SELECT ?painting ?folioNumber ?episodeLabel ?painterLabel
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:partOfProgram mdhn:program_mythological_age .
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber .
  OPTIONAL { ?painting mdhn:hasNarrativeEpisode ?ep . ?ep rdfs:label ?episodeLabel . FILTER(LANG(?episodeLabel)="en") }
  OPTIONAL { ?painting mdhn:hasPainter ?p . ?p rdfs:label ?painterLabel . }
}
ORDER BY ?folioNumber
```

#### Q-I4 — Find all foreground figures in a specific painting

```sparql
SELECT ?characterLabel ?scale ?iiifRegion
WHERE {
  ?folio mdhn:folioNumber "20v" ;
         mdhn:hasContentElement ?painting .
  ?painting mdhn:hasFigureCrop ?crop .
  ?crop mdhn:hasCompositionZone mdhn:zone_foreground .
  OPTIONAL { ?crop mdhn:figureScale ?scale . }
  OPTIONAL { ?crop mdhn:iiifRegionURL ?iiifRegion . }
  OPTIONAL { ?crop mdhn:hasReferredTo ?char . ?char rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en") }
}
```

#### Q-I5 — Count paintings per scene type (iconographic distribution)

```sparql
SELECT ?sceneTypeLabel (COUNT(?painting) AS ?count)
WHERE {
  ?painting a mdhn:Painting ;
            mdhn:hasSceneType ?sceneType .
  ?sceneType rdfs:label ?sceneTypeLabel . FILTER(LANG(?sceneTypeLabel)="en")
}
GROUP BY ?sceneType ?sceneTypeLabel
ORDER BY DESC(?count)
```

#### Q-I6 — Find cross-manuscript parallels with confidence level

```sparql
SELECT ?folio1 ?folio2 ?confidence
WHERE {
  ?painting1 mdhn:hasParallelIn ?painting2 .
  OPTIONAL { ?painting1 mdhn:parallelConfidence ?confidence . }
  ?f1 mdhn:hasContentElement ?painting1 ; mdhn:folioNumber ?folio1 .
  ?f2 mdhn:hasContentElement ?painting2 ; mdhn:folioNumber ?folio2 .
  FILTER(?painting1 != ?painting2)
}
```

---

## Instance Data — Current Coverage (`resources.ttl`)

| Folio | Subject | Painter | Current Location |
|---|---|---|---|
| 7r | Firdausi Encounters the Court Poets of Ghazna | Āqā Mīrak | Aga Khan Museum |
| 20v | The Court of Kayumars | Sultan Muhammad | Aga Khan Museum |
| 21v | Hushang Slays the Black Div | Sultan Muhammad | S. C. Welch Family Collection |
| 22v | The Feast of Sada | Sultan Muhammad | Metropolitan Museum of Art |
| 23v | Tahmuras Defeats the Divs | Sultan Muhammad | Metropolitan Museum of Art |
| 38v | The Court of Faridun — Faranak Sends Gifts | Qadimi | Khalili Collection |

---

## SPARQL Query Samples — Base Ontology

Prepend this prefix block to all queries:

```sparql
PREFIX mdhn:  <http://example.com/mdhn/ontology#>
PREFIX fhkb:  <http://www.example.com/genealogy.owl#>
PREFIX folio: <http://example.com/mdhn/resource/folio/>
PREFIX rdfs:  <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX xsd:   <http://www.w3.org/2001/XMLSchema#>
PREFIX wd:    <http://www.wikidata.org/entity/>
PREFIX skos:  <http://www.w3.org/2004/02/skos/core#>
PREFIX crm:   <http://www.cidoc-crm.org/cidoc-crm/>
```

---

### Q1 — List all folios with types and current GLAM holder

```sparql
SELECT ?folio ?folioNumber ?type ?holderLabel
WHERE {
  ?folio a ?type ; mdhn:folioNumber ?folioNumber ; mdhn:keptIn ?holder .
  ?holder rdfs:label ?holderLabel .
  FILTER(?type IN (mdhn:Recto, mdhn:Verso, mdhn:AlternateFolio))
}
ORDER BY ?folioNumber
```

### Q2 — Retrieve all paintings with painter and workshop director

```sparql
SELECT ?painting ?painterLabel ?directorLabel
WHERE {
  ?painting a mdhn:Painting .
  OPTIONAL { ?painting mdhn:hasPainter ?p . ?p rdfs:label ?painterLabel . }
  OPTIONAL { ?painting mdhn:hasWorkshop_director ?d . ?d rdfs:label ?directorLabel . }
}
```

### Q3 — Find all paintings attributed to Sultan Muhammad

```sparql
SELECT ?folioNumber ?painting
WHERE {
  ?painting a mdhn:Painting ; mdhn:hasPainter mdhn:Sultan_Muhammad .
  ?folio mdhn:hasContentElement ?painting ; mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

### Q4 — List narrative episodes and the folios on which they appear

```sparql
SELECT ?episodeLabel ?folioNumber
WHERE {
  ?episode a mdhn:NarrativeEpisode .
  OPTIONAL { ?episode rdfs:label ?episodeLabel . FILTER(LANG(?episodeLabel)="en") }
  ?painting mdhn:hasNarrativeEpisode ?episode .
  ?folio mdhn:hasContentElement ?painting ; mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

### Q5 — Get all epic characters depicted, with their Wikidata items

```sparql
SELECT DISTINCT ?characterLabel ?wikidataItem
WHERE {
  ?painting a mdhn:Painting ; mdhn:hasReferredTo ?character .
  ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en")
  OPTIONAL { ?character mdhn:wikidataItem ?wikidataItem . }
}
ORDER BY ?characterLabel
```

### Q6 — List all figure crops with their IIIF region URLs

```sparql
SELECT ?cropLabel ?characterLabel ?iiifRegion
WHERE {
  ?crop a mdhn:FigureCrop ; mdhn:hasReferredTo ?character ; mdhn:iiifRegionURL ?iiifRegion .
  OPTIONAL { ?crop rdfs:label ?cropLabel . FILTER(LANG(?cropLabel)="en") }
  OPTIONAL { ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en") }
}
ORDER BY ?characterLabel
```

### Q7 — Retrieve the full provenance chain of the manuscript

```sparql
SELECT ?intervalLabel ?ownerLabel ?start ?end ?transferLabel
WHERE {
  mdhn:manuscript_shahnama_shah_tahmasp mdhn:hasOwnershipInterval ?interval .
  ?interval rdfs:label ?intervalLabel ; mdhn:owner ?owner ; mdhn:ownershipStart ?start .
  ?owner rdfs:label ?ownerLabel .
  OPTIONAL { ?interval mdhn:ownershipEnd ?end . }
  OPTIONAL { ?interval mdhn:transferType ?t . ?t rdfs:label ?transferLabel . FILTER(LANG(?transferLabel)="en") }
}
ORDER BY ?start
```

### Q8 — Find missing / unlocated paintings (unlinked register entries)

```sparql
SELECT ?entryLabel ?folioNumber
WHERE {
  ?entry a mdhn:RegisterEntry ; mdhn:entryFolioNumber ?folioNumber .
  OPTIONAL { ?entry rdfs:label ?entryLabel . FILTER(LANG(?entryLabel)="en") }
  FILTER NOT EXISTS { ?folio mdhn:hasRegisterEntry ?entry . }
}
ORDER BY ?folioNumber
```

### Q9 — Navigate the folio sequence

```sparql
SELECT ?folioNumber ?nextFolioNumber
WHERE {
  ?folio mdhn:folioNumber ?folioNumber ; mdhn:nextFolio ?nextFolio .
  ?nextFolio mdhn:folioNumber ?nextFolioNumber .
}
ORDER BY ?folioNumber
```

### Q10 — List poetic text objects with their verse ranges

```sparql
SELECT ?folioNumber ?startVerse ?endVerse
WHERE {
  ?text a mdhn:LinguisticObject ; mdhn:startVerse ?startVerse ; mdhn:endVerse ?endVerse .
  ?folio mdhn:hasContentElement ?text ; mdhn:folioNumber ?folioNumber .
}
ORDER BY xsd:integer(?startVerse)
```

### Q11 — Count figure crops per character

```sparql
SELECT ?characterLabel (COUNT(?crop) AS ?cropCount)
WHERE {
  ?crop a mdhn:FigureCrop ; mdhn:hasReferredTo ?character .
  OPTIONAL { ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en") }
}
GROUP BY ?character ?characterLabel
ORDER BY DESC(?cropCount)
```

### Q12 — Retrieve all folios held by a specific institution

```sparql
SELECT ?folioNumber
WHERE {
  ?folio mdhn:keptIn mdhn:Metropolitan_Museum_of_Art ; mdhn:folioNumber ?folioNumber .
}
ORDER BY ?folioNumber
```

### Q13 — Find paintings depicting both Hushang and a Div

```sparql
SELECT ?painting ?folioNumber
WHERE {
  ?painting a mdhn:Painting ; mdhn:hasReferredTo mdhn:Hushang ; mdhn:hasReferredTo ?div .
  ?div a mdhn:EpicEntity .
  FILTER(STRSTARTS(STR(?div), "http://example.com/mdhn/ontology#Div"))
  ?folio mdhn:hasContentElement ?painting ; mdhn:folioNumber ?folioNumber .
}
```

### Q14 — Retrieve all IIIF manifests with register entry descriptions

```sparql
SELECT ?folioNumber ?manifest ?description
WHERE {
  ?folio mdhn:folioNumber ?folioNumber ; mdhn:hasIIIFManifest ?manifest .
  OPTIONAL {
    ?folio mdhn:hasRegisterEntry ?entry .
    ?entry rdfs:comment ?description . FILTER(LANG(?description)="en")
  }
}
ORDER BY ?folioNumber
```

### Q15 — List all persons involved in creation with their roles

```sparql
SELECT DISTINCT ?personLabel ?role ?wikidataItem
WHERE {
  VALUES (?prop ?role) {
    (mdhn:hasPainter "Painter")
    (mdhn:hasWorkshop_director "Workshop Director")
    (mdhn:hasIlluminator "Illuminator")
    (mdhn:hasScriber "Scribe / Calligrapher")
    (mdhn:hasAuthor "Author / Poet")
  }
  ?content ?prop ?person .
  ?person rdfs:label ?personLabel . FILTER(LANG(?personLabel)="en")
  OPTIONAL { ?person mdhn:wikidataItem ?wikidataItem . }
}
ORDER BY ?role ?personLabel
```

### Q16 — Full summary card for a single folio

```sparql
SELECT ?folioNumber ?type ?holder ?manifest ?painter ?episode ?verse_start ?verse_end
WHERE {
  BIND(folio:20v AS ?folio)
  ?folio mdhn:folioNumber ?folioNumber ; a ?type ; mdhn:keptIn ?holderUri ; mdhn:hasIIIFManifest ?manifest .
  ?holderUri rdfs:label ?holder .
  OPTIONAL {
    ?folio mdhn:hasContentElement ?painting .
    ?painting a mdhn:Painting .
    OPTIONAL { ?painting mdhn:hasPainter ?p . ?p rdfs:label ?painter . }
    OPTIONAL { ?painting mdhn:hasNarrativeEpisode ?ep . ?ep rdfs:label ?episode . FILTER(LANG(?episode)="en") }
  }
  OPTIONAL {
    ?folio mdhn:hasContentElement ?text .
    ?text a mdhn:LinguisticObject ; mdhn:startVerse ?verse_start ; mdhn:endVerse ?verse_end .
  }
}
```

### Q17 — Trace a character across all paintings (character filmography)

```sparql
SELECT ?characterLabel ?folioNumber ?episodeLabel ?painterLabel ?manifest
WHERE {
  BIND(mdhn:Hushang AS ?character)
  ?character rdfs:label ?characterLabel . FILTER(LANG(?characterLabel)="en")
  ?painting mdhn:hasReferredTo ?character .
  ?folio mdhn:hasContentElement ?painting ;
         mdhn:folioNumber ?folioNumber ;
         mdhn:hasIIIFManifest ?manifest .
  OPTIONAL { ?painting mdhn:hasNarrativeEpisode ?ep . ?ep rdfs:label ?episodeLabel . FILTER(LANG(?episodeLabel)="en") }
  OPTIONAL { ?painting mdhn:hasPainter ?p . ?p rdfs:label ?painterLabel . }
}
ORDER BY ?folioNumber
```

---

## External Vocabulary Alignments

| Internal | External | Vocabulary |
|---|---|---|
| `mdhn:Manuscript` | `aat:300028569` | Getty AAT |
| `mdhn:Painting` | `aat:300033799` | Getty AAT |
| `mdhn:Illumination` | `aat:300053433` | Getty AAT |
| `mdhn:PoeticText` | `aat:300026366` | Getty AAT |
| `mdhn:Inscription` | `aat:300028702` | Getty AAT |
| `mdhn:FigureCrop` | `aat:300404983` | Getty AAT |
| `mdhn:Painting` | `crm:E36_Visual_Item` | CIDOC-CRM |
| `mdhn:PaintingRegister` | `crm:E31_Document` | CIDOC-CRM |
| `mdhn:OwnershipInterval` | `crm:E8_Acquisition` | CIDOC-CRM |
| Manuscript instance | `wd:Q3114572` | Wikidata |
| Shah Tahmasp I | `ulan:500344029` | Getty ULAN |

---

## Contributing

Contributions are welcome in the form of additional folio instances, FHKB kinship assertions for epic characters, new `mdhn:RegisterEntry` records for unmodelled paintings, Wikidata reconciliation of episodes and entities, IIIF manifest links and figure crop region URLs, and scene type / visual attribute annotations.

All data contributions are released under **CC BY 4.0**.

---

## Licence

Ontology and data: [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)

Primary scholarly reference: Dickson, Martin B. and Welch, Stuart Cary. *The Houghton Shahnameh*. Harvard University Press, 1981.

---

*Knowledge graph design and ontology: Mehran DHN, 2026*