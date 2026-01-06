# HTR Project Portfolio: A Snapshot

**Document Version:** 5.0  
**Date:** 2 January 2026  
**Author:** Colin Greenstreet, Research Public Historian  
**Purpose:** Supporting documentation for Substack article "Opening the Ottoman Archive"  
**Author Reference:** Colin Greenstreet, "Introducing myself: Colin Greenstreet, research public historian," *Generative Lives* Substack, October 26, 2025. https://generativelives.substack.com/p/introducing-myself-colin-greenstreet

---

## 1. Executive Summary

This document captures the current state of a research program developing AI-powered Handwritten Text Recognition (HTR) and Optical Character Recognition (OCR) methodologies for historical documents from the late Ottoman Empire and its successor states. The work spans six language projects representing **five distinct script families**: Perso-Arabic (Ottoman Turkish), Cyrillic (Bulgarian), Greek, Roman alphabet (Albanian, Modern Turkish), and Armenian.

The research addresses a fundamental challenge in digital humanities: how to make vast, underutilized archival collections accessible to scholars who cannot read historical scripts. This is not merely a technical problem but an epistemological one—the methodology must balance forensic fidelity to source documents against the interpretive acts inherent in transliteration and translation.

**Key Innovation:** A two-stage pipeline separating visual script capture (using Google Gemini 3 Pro Preview with the V3-S-Minimal protocol) from semantic processing (using Claude with V3-T protocol variants), preventing interpretive contamination while leveraging each model's distinct strengths.

**Script Coverage:** The portfolio deliberately spans both right-to-left (RTL) and left-to-right (LTR) scripts, with the two-stage visual capture methodology currently implemented for Ottoman Turkish (Perso-Arabic), Bulgarian (Cyrillic), and Greek.

---

## 2. The Catalyst: Gemini 3 Pro Preview

On 18 November 2025, Google released Gemini 3 Pro Preview with substantially enhanced visual grounding capabilities. This represented an inflection point—a "Eureka moment"—for HTR research on low-resource historical languages.

### 2.1 The Resource Hierarchy Problem

Languages exist along a resource continuum for AI training:

| Resource Level | Characteristics | Examples |
|----------------|-----------------|----------|
| **High** | Abundant digitized texts, multiple OCR training sets, extensive parallel corpora | English, French, Modern Standard Arabic |
| **Medium** | Some digitized materials, limited training data, scholarly attention | Modern Turkish, Modern Greek |
| **Low** | Minimal or no training data, primarily manuscript sources, specialized paleographic knowledge required | Ottoman Turkish, historical Bulgarian, historical Albanian, Armenian |

Ottoman Turkish exemplifies the "low-resource" challenge: written in Perso-Arabic script with vocabulary drawing heavily from Arabic and Persian (estimates suggest up to 80% of high-register vocabulary), it requires not merely character recognition but deep understanding of three linguistic systems operating within Turkish grammatical structures.

### 2.2 Why Visual Grounding Matters

Previous multimodal models conflated two distinct operations:
1. **Visual capture:** What ink marks appear on the page?
2. **Semantic interpretation:** What do those marks mean?

Gemini 3 Pro Preview, when configured at extreme visual-grounding settings (temperature 0.2, thinking mode low, Top-P 0.15), can perform the first operation with minimal interpretive contamination. This enables a methodology where the AI reports *what it sees* before any model attempts to determine *what it means*.

### 2.3 Model-Agnostic Considerations

**Are the HTR skill files model-agnostic?**

The skill files are *partially* model-agnostic in theory, but practically differentiated:

1. **Semantic processing skill files (V3-T family)** transfer reasonably well across capable LLMs (Claude, GPT-4, Gemini) for semantic tasks. However, outputs differ based on training data composition, instruction-following fidelity, and handling of non-Latin scripts.

2. **Visual capture skill files (V3-S family)** are more model-dependent. The extreme grounding settings (T=0.2, Top-P=0.15) are Gemini-specific parameters.

3. **On alternative models:** As of January 2026, no other model has demonstrated equivalent visual grounding capability for the specific task of "report what you see without interpretation."

**Recommendation:** Skill files should include a "Model Configuration" section specifying tested models and parameters, treating transferability as an empirical question.

---

## 3. The Two-Stage Architecture

### 3.1 Design Principle: Separation of Concerns

```
┌─────────────────────────────────────────────────────────────────┐
│  STAGE 1: VISUAL CAPTURE                                        │
│  Model: Google Gemini 3 Pro Preview                             │
│  Settings: T=0.2, Top-P=0.15, Thinking=Low                      │
│  Protocol: V3-S-Minimal                                         │
│  Output: Raw script capture, no interpretation                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  STAGE 2: SEMANTIC PROCESSING                                   │
│  Model: Anthropic Claude                                        │
│  Settings: Higher temperature for creative/linguistic work      │
│  Protocol: V3-T variants (document-type specific)               │
│  Output: Transliteration, translation, NER, contextual summary  │
└─────────────────────────────────────────────────────────────────┘
```

**Languages currently using two-stage pipeline:** Ottoman Turkish, Bulgarian, Greek

### 3.2 The Skill File Paradox

A critical empirical discovery: complex skill files paradoxically *degrade* performance for visual capture tasks. When V3-S protocols included extensive linguistic guidance, Gemini's processing times increased dramatically while accuracy decreased.

**Solution:** Stripped-down "minimal" protocols for Stage 1, with all linguistic sophistication reserved for Stage 2.

---

## 4. Why Claude for Semantic Processing

Claude's architecture offers six distinct advantages for HTR semantic processing:

### 4.1 Responsiveness and Analytical Tone
Claude engages with ambiguous readings through measured, scholarly reasoning rather than overconfident assertions—essential when paleographic evidence is genuinely uncertain.

### 4.2 Project Infrastructure
Claude's project structure enables persistent context, accumulated learning, custom instructions, and generous storage for skill files and outputs.

### 4.3 Native Skills Architecture
Anthropic's skill file concept integrates naturally with user-created HTR skill files, enabling experimentation with combined approaches.

### 4.4 Research Historian Workflow Integration
The Socratic interaction pattern supports iterative refinement, hypothesis testing, and transparent reasoning about evidence.

### 4.5 Linguistic and Historical Depth
Claude demonstrates sophisticated handling of:
- Philological analysis across Ottoman Turkish, Arabic, Persian
- Bulgarian Cyrillic historical and modern forms
- Greek polytonic and monotonic systems
- Armenian script conventions (Eastern and Western variants)
- Comparative historical linguistics
- Contextual reading within diplomatic, bureaucratic, and personal correspondence genres

### 4.6 Collaborative Protocol Development
Claude can co-create rigorous workflows, design testing regimes (including Python-based CER/WER calculations), and perform variance analysis comparing multiple AI outputs.

---

## 5. Language Projects Portfolio

### 5.1 Ottoman Turkish HTR [PRIMARY]

**Status:** Most developed  
**Creation Order:** 1  
**Script:** Perso-Arabic (RTL)  
**Period Focus:** 1831–1920s  
**Resource Level:** Low  
**Two-Stage Pipeline:** Yes (V3-S-Minimal → V3-T variants)

#### 5.1.1 Historical Context (1830–1920s)

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1808–1839 | Reign of Sultan Mahmud II | Centralizing reforms; destruction of Janissaries (1826); founding of Takvîm-i Vekâyi (1831) |
| 1839–1876 | Tanzimat Reform Era | Modernization of administration; codification of law; expansion of press; multilingual government publications |
| 1856 | Hatt-ı Hümayun | Reform edict; equality of non-Muslims; relevant for NER of minority officials |
| 1876 | First Ottoman Constitution | Constitutional terminology; parliamentary vocabulary |
| 1876–1909 | Hamidian Era | Press restrictions; censorship vocabulary; exile communities |
| 1908 | Young Turk Revolution | Second Constitutional Period; explosion of press; political party terminology |
| 1914–1918 | World War I | Military vocabulary; Entente/Central Powers terminology; wartime censorship |
| 1918–1922 | Empire's Collapse | Armistice terminology; occupation vocabulary; nationalist movements |

**Linguistic Complexity:**
Ottoman Turkish functioned as the bureaucratic lingua franca but the empire operated multilingually. Government documents were routinely translated into Greek, Armenian, Bulgarian, and Arabic, particularly before the Tanzimat reforms. The 1876 Constitution established Ottoman Turkish as the official government language, but the concept of a single "official language" is itself a 19th-century invention associated with nationalism.

Low literacy rates (estimated 2–3% early 19th century, 15% by century's end) meant that high-register Ottoman Turkish with extensive Arabic and Persian vocabulary was accessible only to educated elites.

#### 5.1.2 Document Types

**Official Government Gazette:**

| Original Script | Transliteration | English |
|-----------------|-----------------|---------|
| تقویم وقایع | Takvîm-i Vekâyi | Calendar of Events |

- **Years published:** 1831–1922 (first series 1831–1840; second series 1840–1878; third series 1908–1922)
- **Languages:** Ottoman Turkish; historical editions also in French, Armenian, Greek, Arabic. Persian versions may have existed.
- **Significance:** First Ottoman newspaper; no systematic scholarly transliteration or English translation exists for early issues. This research produces genuinely original scholarship.
- **Digital Access:** Turkish National Library (1841–1919); Wikimedia Commons (1,427 PDF files); IRCICA Farabi Library (complete 7,030 issues)

**Major Newspapers of Record (1830s–1920s):**

| Original Script | Transliteration | English | Years | Character |
|-----------------|-----------------|---------|-------|-----------|
| طنین | Tanin | Echo | 1908–1925 | Semi-official CUP organ |
| اقدام | İkdam | Perseverance | 1894–1928 | Mass-circulation daily |
| صباح | Sabah | Morning | 1876–1922 | Major daily (Armenian-founded by Mihran Efendi) |
| وقت | Vakit | Time | 1917–1930s | Founded during WWI |
| ترجمان حقیقت | Tercüman-ı Hakîkat | Interpreter of Truth | 1878–1922 | Conservative daily |
| پیام | Peyam | Message | 1913–1914 | Political daily |

**French-Language Press (Constantinople):**
- Le Stamboul (1875–1962): Leading French daily
- Journal de Constantinople et des Intérêts Orientaux (1843–1930s): Oldest French paper
- La Turquie (1866–1930s)
- Extensive digitization via SALT Research/BnF/IFEA collaboration

**Armenian-Language Press (Constantinople):**

| Armenian Script | Transliteration | English | Years | Status |
|-----------------|-----------------|---------|-------|--------|
| Ժամանակ | Jamanak | Time | 1908–present | Only major Armenian daily confirmed publishing by November 1917; oldest continuously published Armenian-language daily in the world. Founded October 28, 1908 by Misak and Sarkis Koçunyan. |
| Ազատամարտ | Azadamart | Freedom's Battle | 1909–1915 | Major ARF newspaper; founded by writer Roupen Zartarian; ceased when staff arrested April 1915 |

*Note: The first Armenian periodical worldwide was Aztarar (Ազդարար, "Monitor"), published in Madras, India in 1794 by Father Harutyun Shmavonian—making it the first newspaper of any Near Eastern people.*

**Greek-Language Press in Ottoman Constantinople:**

| Greek Script | Transliteration | English | Years | Notes |
|--------------|-----------------|---------|-------|-------|
| Ἀνατολικὸς Ἀστήρ | Anatolikos Astēr | Eastern Star | 1861– | Constantinople Greek press |
| Κωνσταντινούπολις | Kōnstantinoupolis | Constantinople | 1867– | "Most widely read Greek paper in the Ottoman Empire" |

#### 5.1.3 Key Linguistic Challenges

- Perso-Arabic script ambiguity (underdotted letters, ligatures)
- Triple linguistic layer (Turkish grammar, Arabic/Persian vocabulary up to 80% in high register)
- Lithographic vs. movable type printing distinctions
- Triple calendar systems (Rumi/Hijri/Gregorian)
- Izafet constructions spanning Arabic, Persian, and Turkish grammatical rules

#### 5.1.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Sultan Mahmud II, Reşid Paşa, Enver Paşa | Titles and honorifics vary by period |
| **Institutions** | Bâb-ı Âli, Meclis-i Mebusan, Divan-ı Hümayun | Administrative terminology evolves through reforms |
| **Places** | Constantinople/Dersaadet, Rumeli, Anatolu | Multiple naming conventions |
| **Dates** | Rumi, Hijri, Gregorian | Triple calendar system requires conversion |
| **Ranks/Titles** | Paşa, Bey, Efendi, Kadı | Social hierarchy markers |
| **Political Parties** | İttihat ve Terakki, Hürriyet ve İtilaf | Post-1908 |

#### 5.1.5 HTR Project Corpus Analysed

- **Takvîm-i Vekâyi:** Issues 1, 181, 185 (complete transliteration/translation)
- **Second Constitutional Period newspapers:** Tanin, Peyam
- **Personal correspondence:** İSAM Archive, Hüseyin Hilmi Paşa Documents
- **Administrative documents and chronicles:** Şânîzâde Tarihi, Vekâyi-i Devlet-i Aliye
- **Cartographic materials:** Ottoman Map Inventory, Balkans 1890

#### 5.1.6 Protocols Developed

**Visual Capture (Stage 1):**
- V3-S-Minimal: Core visual capture protocol
- V3-S-Newspaper (v1.0, v1.1, v1.2): Newspaper-specific visual capture

**Semantic Processing (Stage 2):**
- V3-T: Core transliteration/translation
- V3-T-C: Correspondence variants (Personal, Administrative)
- V3-T-Chronicle: Biographical and historical texts
- V3-T-Newspaper: Second Constitutional Period journalism

---

### 5.2 Albanian HTR

**Status:** Early Development  
**Creation Order:** 2  
**Script:** Roman alphabet (modern); historically Arabic script (Elifba), Greek script  
**Script Direction:** LTR  
**Period Focus:** 1848–1920s  
**Resource Level:** Low  
**Two-Stage Pipeline:** Yes (five-stage implementation)

#### 5.2.1 Historical Context (1830–1920s)

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1830s–1840s | Albanian Rilindja begins | Diaspora publishing; multiple script experiments |
| 1844 | Naum Veqilharxhi's alphabet | First attempt at standardized Latin-based Albanian alphabet |
| 1878 | League of Prizren | Political organization vocabulary; territorial claims |
| 1908 | Congress of Monastir | Standardization of Albanian alphabet using Latin characters |
| 1912 | Albanian Independence | Declaration vocabulary; Ismail Qemali |
| 1914–1918 | WWI Occupations | Austria-Hungary (north), Italy (south), France (Korçë); no indigenous press |
| 1920 | Recognized independence | First stable government institutions |

**Critical Finding:** The Albanian press developed primarily in diaspora communities due to Ottoman restrictions on Albanian-language publishing. No indigenous Albanian press infrastructure existed within Albanian territories during 1917.

#### 5.2.2 Document Types

**Official Government Gazette:**
- None until after 1912—Albania had no functioning central government during Ottoman period
- Post-independence gazette development incomplete during research period

**Diaspora Press (Primary Sources for Albanian-language journalism):**

| Title | Script | Location | Years | Significance |
|-------|--------|----------|-------|--------------|
| L'Albanese d'Italia | Italian/Arbëresh | Naples | Feb–Jun 1848 | First Albanian newspaper; bilingual |
| Pellazgu | Greek script | Lamia, Greece | 1860 | First Albanian-language newspaper in Greek lands |
| Zëri i Shqipërisë | Greek script | Athens | 1879 | "Voice of Albania" |
| Dielli | Roman | Boston, USA | 1909–present | Published by Vatra Federation; edited by Fan Noli |

#### 5.2.3 Key Linguistic Challenges

- **Multiple historical scripts:** Albanian was written in Arabic script (Elbasan alphabet), Greek script, and various Latin-based systems before 1908 standardization
- **Dialect variation:** Gheg (north) vs. Tosk (south) with significant grammatical differences
- **Orthographic instability:** Pre-1908 documents use inconsistent spelling conventions
- **Extremely limited digitization** of historical materials

#### 5.2.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Ismail Qemali, Fan Noli, Naim Frashëri | Rilindja figures prominent |
| **Places** | Shkodër, Durrës, Korçë, Vlorë | Multiple naming conventions (Turkish, Italian, Albanian) |
| **Organizations** | Liga e Prizrenit, Vatra | National movement bodies |

#### 5.2.5 Protocols Developed

**Segmentation:**
- V0-SEG-ALB: Script zone segmentation for polyglot documents

**Visual Capture (Stage 1):**
- V3-S-ALB-L: Latin Albanian visual capture
- V3-S-ALB-E: Elifba (Arabic script) Albanian visual capture

**Semantic Processing (Stage 2):**
- V3-T-ALB: Latin Albanian transliteration and translation
- V3-T-ALB-E: Elifba Albanian transliteration and translation

#### 5.2.6 HTR Project Corpus Analysed

| Title | Script | Location | Years | Source | Key Discoveries |
|-------|--------|----------|-------|--------|-----------------|
| Drita | Latin Albanian (with Ottoman Turkish sections) | Sofia | 1907–1908 | İSAM Hüseyin Hilmi Pasha archive | Highly systematic pre-standardization orthography (ð for /ð/, ñ for /ɲ/); anti-Hamidian polemics predicting Ottoman regime's fall months before 1908 Young Turk Revolution |

**Key Finding:** Pre-standardization Albanian texts prove more systematic than assumed—editors employed consistent orthographic choices, challenging assumptions about "orthographic chaos" before the Congress of Monastir (1908).

---

### 5.3 Bulgarian HTR

**Status:** Early Development  
**Creation Order:** 3  
**Script:** Cyrillic (LTR)  
**Period Focus:** 1844–1920s  
**Resource Level:** Low–Medium  
**Two-Stage Pipeline:** Yes

#### 5.3.1 Historical Context (1830–1920s)

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1840s | Bulgarian National Revival press begins | Publications from diaspora (Smyrna, Leipzig, Constantinople) |
| 1844 | First Bulgarian periodical (Liuboslovie) | Published in Smyrna due to Ottoman restrictions |
| 1846 | First Bulgarian newspaper (Bulgarski orel) | Published in Leipzig; only 3 issues |
| 1848–1862 | Tsarigradski vestnik | First successful continuous Bulgarian newspaper (Constantinople) |
| 1870 | Bulgarian Exarchate established | Autocephalous church; religious NER implications |
| 1876 | April Uprising | Revolutionary vocabulary; martyrdom terminology |
| 1878 | Liberation; Treaty of Berlin | Independence vocabulary; Principality established |
| 1879 | Tarnovo Constitution | Constitutional terminology; State Gazette begins |
| 1885 | Unification with Eastern Rumelia | Territorial vocabulary |
| 1912–1913 | Balkan Wars | Military vocabulary; territorial changes |
| 1915–1918 | WWI (Central Powers ally) | German alliance vocabulary |

**Press Development:**
Over 100 Bulgarian periodicals appeared by 1878, but most were short-lived and published outside Bulgaria due to Ottoman restrictions. After independence, publishing grew rapidly—over 500 newspapers by 1900.

#### 5.3.2 Document Types

**Official Government Gazette:**

| Original Script | Transliteration | English |
|-----------------|-----------------|---------|
| Държавен вестник | Darzhaven Vestnik | State Gazette |

- **First issue:** July 28, 1879 (after independence)
- **Language:** Bulgarian
- **Digitization:** 1920–1947 via Ciela Norma AD; **1917 NOT digitized**
- **Physical:** SS. Cyril and Methodius National Library, Sofia

**Major Newspapers (1844–1920s):**

| Original Script | Transliteration | Location | Years | Notes |
|-----------------|-----------------|----------|-------|-------|
| Любословие | Liuboslovie | Smyrna | 1844 | First Bulgarian periodical |
| Български орел | Bulgarski orel | Leipzig | 1846 | First Bulgarian newspaper (3 issues) |
| Цариградски вестник | Tsarigradski vestnik | Constantinople | 1848–1862 | First successful continuous newspaper |
| Мир | Mir | Sofia | Post-1878 | Pro-government, Central Powers |
| Народни права | Narodni Prava | Sofia | Post-1878 | Political newspaper |

**German-Language Press (WWI period):**
- Deutsche Balkanzeitung (Sofia, 1917): Reflects German-Bulgarian alliance

**Key Digital Resources:**
- Bulgarian National Library Digital Collections: over 60 newspapers from National Revival Era (1844–1878) digitized
- Europeana Newspapers Project: Bulgarian serials 1878–1944
- Ivan Vazov Library (Plovdiv): 200+ Bulgarian periodicals

#### 5.3.3 Key Linguistic Challenges

- **Historical Cyrillic letterforms** vs. modern standardization
- **Church Slavonic influences** in ecclesiastical documents
- **Script reforms** following national independence (1878)
- **Pre-reform vs. post-reform orthography**
- Most 1917 materials **not digitized**

#### 5.3.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Georgi Rakovski, Hristo Botev, Ivan Vazov | Revival and liberation figures |
| **Institutions** | Bulgarian Exarchate, Narodno Sabranie | Religious and political bodies |
| **Places** | Sofia, Plovdiv, Eastern Rumelia | Post-1878 administrative divisions |
| **Events** | April Uprising, Liberation, Unification | Foundational national narratives |

#### 5.3.5 Protocols Developed

**Semantic Processing (Stage 2):**
- V1-B: Initial Bulgarian HTR skill file
- V1.1-B: Refined version with improved handling of pre-reform characters, article boundary tracking

#### 5.3.6 HTR Project Corpus Analysed

| Title | Script | Location | Year | Pages | Source | Key Discoveries |
|-------|--------|----------|------|-------|--------|-----------------|
| Балканъ (Balkan) | Pre-reform Cyrillic | Ruse | 1898 | 4 | British Library Endangered Archives | Unexpected frequency of iotated yus (ѭ) in 1898 press materials; pre-reform orthographic patterns differ from expectations |

**Key Finding:** Real-world testing on authentic historical materials reveals orthographic patterns that differ from expectations. Distinguishing semantic content from decorative visual elements proved crucial for accurate transcription.

---

### 5.4 Modern Turkish HTR

**Status:** Testing Phase  
**Creation Order:** 4  
**Script:** Roman alphabet (post-1928)  
**Script Direction:** LTR  
**Period Focus:** 1928–present (transition era focus)  
**Resource Level:** Medium  
**Two-Stage Pipeline:** Uses zero-shot experimental approach

#### 5.4.1 Historical Context (1920s)

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1923 | Republic of Turkey established | New state terminology; Ankara as capital |
| 1928 | Alphabet reform | Perso-Arabic script replaced with Latin alphabet |
| 1928–1930s | Language reform | Purging of Arabic/Persian vocabulary; neologisms |

The 1928 alphabet reform created a sharp discontinuity in the written record. Pre-1928 materials require Ottoman Turkish HTR skills; post-1928 materials are accessible to Modern Turkish readers but transition-era documents may contain mixed scripts.

#### 5.4.2 Key Linguistic Challenges

- **Transition-era documents** (1928–1930s) with mixed scripts
- **Vocabulary shifts** as Arabic/Persian terms replaced with Turkish neologisms
- **Reading pre-reform sources** requires separate Ottoman Turkish skills
- **Cursive letter forms** in handwritten materials
- **Word-final letters** present systematic HTR challenges
- **Domain-specific vocabulary** (e.g., agricultural terminology)

#### 5.4.3 Methodology

The Modern Turkish project employs a **zero-shot HTR experimental approach** with comprehensive JSON documentation. Key methodological elements:

- Diplomatic transcription with systematic confidence scoring
- Literal and flowing English translations
- Named entity extraction across persons, places, dates, organizations, and cultural references
- Detailed paleographic observations

#### 5.4.4 HTR Project Corpus Analysed

| Material Type | Date | Source | Confidence Achieved | Key Challenges |
|---------------|------|--------|---------------------|----------------|
| Personal correspondence (envelope + 2-page letter) | 1982 | İSAM Archive | 70–75% high-confidence | Compressed handwriting, agricultural vocabulary, cultural puzzles |

**Experiment 157 Finding:** Cultural and contextual analysis proves essential—e.g., correspondence filed as "from nephews" containing maternal salutations, references to traditional weather beliefs.

---

### 5.5 Greek HTR

**Status:** Early Development  
**Creation Order:** 5  
**Script:** Greek (LTR)  
**Period Focus:** 1830–1920s  
**Resource Level:** Medium  
**Two-Stage Pipeline:** Yes

#### 5.5.1 Historical Context (1830–1920s)

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1821–1829 | Greek War of Independence | Revolutionary vocabulary; Demotic Greek in early journalism |
| 1833 | Kingdom of Greece established | King Otto; Bavarian administration; bilingual Greek-German documents |
| 1833 | Government Gazette begins | First issue February 16, 1833; bilingual until 1835 |
| 1862 | Otto deposed | New dynasty; constitutional changes |
| 1864 | Ionian Islands ceded to Greece | Territorial expansion vocabulary |
| 1881 | Thessaly annexed | Ottoman-Greek boundary changes |
| 1897 | Greco-Turkish War | Military vocabulary; territorial issues |
| 1912–1913 | Balkan Wars | Major territorial expansion; Macedonia, Crete, Aegean islands |
| 1915–1917 | National Schism | Venizelos vs. Constantine I; Allied vs. Central Powers vocabulary |
| 1917 | Greece enters WWI | Entente alliance vocabulary |
| 1919–1922 | Greco-Turkish War | Asia Minor campaign; refugee vocabulary |
| 1922 | Asia Minor Catastrophe | Smyrna fire; population exchange; end of Greek presence in Anatolia |

**Language Question:**
Greek operated with a diglossia between Katharevousa (archaizing, official) and Demotic (vernacular). Official documents and many newspapers used Katharevousa; this distinction affects NER and translation approaches.

#### 5.5.2 Document Types

**Official Government Gazette:**

| Original Script | Transliteration | English |
|-----------------|-----------------|---------|
| Εφημερίς της Κυβερνήσεως | Efimeris tis Kyverniseos | Government Gazette |

- **First issue:** February 16, 1833
- **Languages:** Greek; bilingual Greek-German 1833–1835 (Bavarian regency); some Greek-French issues after 1835
- **Digital Access:** National Printing Office of Greece; Hellenic Parliament Library (back to 1812)

**Pre-Independence Press:**
- Efimeris (Vienna, 1790–1797): Oldest Greek newspaper with surviving issues
- Efimeris ton Athinon (Athens, 1824–1826): First newspaper published in Athens; used Demotic Greek; covered War of Independence

**Major Newspapers with Verified Digitization (National Library of Greece):**

| Original Script | Transliteration | Years | Political Orientation |
|-----------------|-----------------|-------|----------------------|
| Ἐμπρός | Empros | 1896–1969 | Anti-war, Pro-German (1917) |
| Μακεδονία | Makedonia | 1911–1981 | Pro-Venizelos (Thessaloniki) |
| Ριζοσπάστης | Rizospastis | 1917–present | Leftist (founded 1917) |
| Σκριπ | Skrip | 1893–1963 | Initially pro-royalist |
| Ἑστία | Estia | 1876–present | Pro-Entente (1917) |
| Ἀκρόπολις | Akropolis | 1883–1884 | Early digitized holdings |

**Smyrna Greek Press (limited digitization due to 1922 fire):**

| Original Script | Transliteration | Years |
|-----------------|-----------------|-------|
| Αμάλθεια | Amaltheia | 1838–1922 |
| Κόσμος | Kosmos | 1909–1922 |
| Τηλέγραφος | Telegraphos | 1911–1922 |

**French-Language Press:**
- Le Messager d'Athènes (1875–1957)

#### 5.5.3 Key Linguistic Challenges

- **Polytonic vs. monotonic orthography** (monotonic reform 1982; historical documents use polytonic)
- **Katharevousa vs. Demotic** register distinctions
- **Greek-language Ottoman administrative documents** (Phanariot tradition)
- **1922 Smyrna fire** destroyed significant archives

#### 5.5.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Eleftherios Venizelos, Constantine I | National Schism figures |
| **Institutions** | Vouli (Parliament), Patriarchate | Political and religious bodies |
| **Places** | Athens, Thessaloniki, Smyrna/Σμύρνη | Multiple naming conventions |
| **Events** | Megali Idea, National Schism | Irredentist and political terminology |

#### 5.5.5 Protocols Developed

**Visual Capture (Stage 1):**
- V3-S-Greek-Minimal: Minimal visual capture for Greek texts (learned from Ottoman Turkish: excessive length triggers unwanted semantic processing)

**Semantic Processing (Stage 2):**
- V3-T-Greek (v1.2): Comprehensive transliteration and translation protocol
  - **Transliteration standard:** Modified Scholarly conventions
  - **Output structure:** Line-by-line preservation across five analytical columns
  - **Derivation chain:** Polytonic original → Scholarly transliteration → Modern Greek (convenience) → Literal English → Modernized English

**Key Methodological Principle:** Transliterations must derive from polytonic originals rather than modern Greek equivalents, preserving critical features like rough breathing marks (῾) and iota subscripts (ᾳ).

#### 5.5.6 HTR Project Corpus Analysed

| Document Type | Script | Period | Content | Notes |
|---------------|--------|--------|---------|-------|
| Greek Government Gazette (Ἑφημερίς τῆς Κυβερνήσεως) | Polytonic Greek | 1833 | King Otto's royal proclamations | Katharevousa register; SOV word order patterns; perfect passive participle constructions |

**Key Finding:** Preserving distinctive Katharevousa grammatical structures (SOV word order, perfect passive participles) creates unique constructions in literal English translations that convey the formal register of the original.

---

### 5.6 Armenian HTR

**Status:** Initial Setup  
**Creation Order:** 6  
**Script:** Armenian (LTR)  
**Period Focus:** 1830–1920s  
**Resource Level:** Low–Medium  
**Two-Stage Pipeline:** To be confirmed

#### 5.6.1 Historical Context (1830–1920s)

**The Eastern/Western Armenia Division:**

Armenian territories were divided between the Ottoman Empire (Western Armenia) and the Russian Empire (Eastern Armenia, acquired from Persia in 1828). This created two distinct press traditions with different dialects, political contexts, and publication centers:

| Region | Ruling Power | Dialect | Press Centers |
|--------|--------------|---------|---------------|
| Western Armenia | Ottoman Empire | Western Armenian | Constantinople, Smyrna |
| Eastern Armenia | Russian Empire | Eastern Armenian | Tiflis (Tbilisi), Yerevan, Baku |

**Key Events Affecting Documents and NER:**

| Period | Event | Impact on Documents |
|--------|-------|---------------------|
| 1828 | Russia acquires Eastern Armenia from Persia | Division of Armenian press traditions |
| 1849 | Ararat journal (Tiflis) | First journal in modern Armenian vernacular |
| 1872–1920 | Mshak newspaper (Tiflis) | Major Eastern Armenian political daily; advocated reunification with Russia |
| 1887 | Hënchak party founded | Socialist revolutionary vocabulary |
| 1890 | Dashnaktsutyun founded | Armenian Revolutionary Federation terminology |
| 1894–1896 | Hamidian massacres | Violence vocabulary; refugee documentation |
| 1908 | Jamanak founded (Constantinople) | Last surviving major Western Armenian daily in Ottoman lands |
| 1909 | Azadamart founded (Constantinople) | Major Dashnak newspaper |
| 1909 | Adana massacre | Regional violence documentation |
| 1915 | April 24 | Arrest of Armenian intellectuals; genocide begins; press decimation |
| 1915–1917 | Armenian Genocide | Deportation vocabulary; survivor testimony; diaspora press emergence |
| 1918 | First Republic of Armenia | Brief independence; new state terminology |
| 1920 | Sovietization | End of independent Armenian Republic |

**Tiflis as Eastern Armenian Press Center:**
Under Russian rule, Tiflis (now Tbilisi, Georgia) became the major center of Eastern Armenian intellectual life. Armenian newspapers flourished there, including Mshak, which advocated for Armenian reunification under Russian protection. The literary revival was led by Mikael Nalbandian (language modernization) and the novelist Raffi.

**Impact of 1915:**
The Armenian press community in Constantinople was devastated by the events of 1915–1917. The April 24, 1915 arrests specifically targeted journalists and intellectuals. By November 1917, only Jamanak was confirmed still publishing as a major Armenian daily in Constantinople.

#### 5.6.2 Document Types

**Constantinople (Western Armenian):**

| Armenian Script | Transliteration | English | Years | Notes |
|-----------------|-----------------|---------|-------|-------|
| Ժամանակ | Jamanak | Time | 1908–present | Only major daily surviving by 1917 |
| Ազատամարտ | Azadamart | Freedom's Battle | 1909–1915 | Ceased when staff arrested |

**Tiflis / Russian Armenia (Eastern Armenian):**

| Armenian Script | Transliteration | English | Years | Notes |
|-----------------|-----------------|---------|-------|-------|
| Մշակ | Mshak | Cultivator | 1872–1920 | Major political daily; pro-Russian reunification |
| Արարատ | Ararat | — | 1849 | First journal in modern vernacular |
| Զանգ | Zang | The Ring | 1910–1922 | Hënchak party organ |

**Cairo Diaspora Press:**

| Armenian Script | Transliteration | English | Founded | Affiliation |
|-----------------|-----------------|---------|---------|-------------|
| Արև | Arev | The Sun | 1915 | Ramgavar (founded by Vahan Tekeyan) |
| Հուսաբեր | Husaber | News-bearer | 1913 | ARF/Dashnak |

#### 5.6.3 Key Linguistic Challenges

- **Distinct script** with long literary tradition (alphabet created 405 CE by Mesrop Mashtots)
- **Eastern vs. Western Armenian** orthographic and grammatical differences
- **Pre-Soviet vs. Soviet orthographic reforms** in Eastern Armenian
- **Limited historical digitization**
- **Grabar (Classical Armenian)** in religious texts vs. modern vernacular

#### 5.6.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Krikor Ardzrouni, Mikael Nalbandian, Raffi | Literary and political figures |
| **Institutions** | Armenian Patriarchate, Dashnaktsutyun, Hënchak | Religious and political bodies |
| **Places** | Tiflis/Tbilisi, Constantinople, Van, Erevan | Eastern vs. Western geography |
| **Events** | Hamidian massacres, 1915 Genocide, First Republic | Traumatic national events |

**Key Digital Resources:**
- ARAM Repository of Historical Newspapers (Association for Research and Archiving of Armenian Memory)
- Union Catalog of Armenian Continuing Resources
- National Library of Armenia digital collections
- UC Berkeley Armenian Studies Library Guide

#### 5.6.5 Project Foundation

The Armenian HTR project will build on foundational learnings from zero-shot Armenian HTR experiments documented in:

> Colin Greenstreet, "A New Lens into the Archive: You are in an archive. You find a document in a language you don't understand. You take a photo, input it into Gemini 3 Pro. 60 seconds later you have a transcription, transliteration, and translation," *Generative Lives* (Substack), December 4, 2025. https://substack.com/home/post/p-180702218

#### 5.6.6 Protocols Developed

*To be developed based on Ottoman Turkish V3 protocol adaptations*

**Anticipated Challenges:**
- Eastern vs. Western Armenian orthographic conventions
- Pre-Soviet vs. Soviet orthographic reforms (Eastern Armenian)
- Grabar (Classical Armenian) in religious texts vs. modern vernacular
- Limited training data for historical Armenian scripts

#### 5.6.7 HTR Project Corpus Analysed

*To be determined*

---

### 5.7 [Planned] Egyptian Arabic HTR

**Status:** Planned – Not Yet Created  
**Script:** Arabic (RTL)  
**Period Focus:** 1828–1920s  
**Two-Stage Pipeline:** To be confirmed

#### 5.7.1 Historical Context (1828–1920s)

**Key Periods and Events Affecting Documents:**

| Period | Ruler/Status | Key Events | Impact on Documents |
|--------|--------------|------------|---------------------|
| 1805–1848 | Muhammad Ali Pasha | Modernization; Bulaq Press (1821); Al-Waqa'i' al-Misriyya founded (Dec 3, 1828); educational missions to Europe | French/Italian influences; technical/military vocabulary; multilingual (Arabic, Turkish, French) |
| 1848–1854 | Abbas I | Reduced reform momentum; increased European commercial presence | Commercial terminology |
| 1854–1863 | Said Pasha | Suez Canal concession (1854); Alexandria-Cairo railway (1856) | French engineering vocabulary; infrastructure terminology |
| 1863–1879 | Ismail Pasha (Khedive) | Suez Canal opening (Nov 17, 1869); Al-Ahram founded (Aug 5, 1876); Khedival Library (1870); massive debt | Financial vocabulary; European loanwords; expanded journalistic vocabulary |
| 1879–1882 | Tewfik Pasha | Urabi Revolt (1879–1882); British bombardment of Alexandria (July 11, 1882); British occupation begins | Nationalist vocabulary; military terminology; constitutional language |
| 1882–1914 | British Occupation (Veiled Protectorate) | Lord Cromer (1883–1907); Al-Muqattam founded (1888); Dinshaway Incident (1906); Al-Liwa founded (1900) | Censorship vocabulary; nationalist discourse; English administrative terms; bilingual documents |
| 1914–1918 | British Protectorate | Egypt severed from Ottoman Empire (Dec 18, 1914); wartime censorship; Balfour Declaration in Arabic (Nov 10, 1917) | Pro-Allied vocabulary; anti-Ottoman terminology |
| 1919–1922 | Revolution and Independence | 1919 Revolution (Saad Zaghloul); Wafd Party; British declaration of independence (Feb 28, 1922) | Revolutionary vocabulary; independence terminology |
| 1922–1929 | Kingdom of Egypt | 1923 Constitution; parliamentary politics; continued British influence | Constitutional vocabulary; parliamentary terminology |

**Press Development:**

Egypt's press history began with Muhammad Ali's modernization program. The Bulaq Press (1821) was the first government printing press, and Al-Waqa'i' al-Misriyya (1828) became the first official newspaper—predating the Ottoman Takvîm-i Vekâyi by three years. The press expanded dramatically under Ismail Pasha, with Al-Ahram (1876) becoming the newspaper of record. The British occupation (1882–1922) shaped press development through censorship and the emergence of both pro-British and nationalist publications.

#### 5.7.2 Document Types (Preliminary)

**Official Government Gazette:**

| Original Script | Transliteration | English |
|-----------------|-----------------|---------|
| الوقائع المصرية | Al-Waqa'i' al-Misriyya | Egyptian Events / Official Gazette |

- **Founded:** December 3, 1828 (first official Egyptian newspaper; predates Ottoman Takvîm-i Vekâyi)
- **Founder:** Muhammad Ali Pasha
- **Languages:** Arabic (historically also Turkish and French)

**Major Newspapers:**

| Original Script | Transliteration | English | Founded | Character | Digitization |
|-----------------|-----------------|---------|---------|-----------|--------------|
| الأهرام | Al-Ahram | The Pyramids | August 5, 1876 | Major daily newspaper of record; founders Salim and Bishara Takla (Lebanese Christians) | **FULLY DIGITIZED** 1876–2018 (East View Global Press Archive) |
| المقطم | Al-Muqattam | The Muqattam (hills) | 1888 | Pro-British daily; founders Faris Nimr, Yaqub Sarruf (Syrian Christians) | **1917 NOT digitized**; LOC microfilm; published first Arabic text of Balfour Declaration (Nov 10, 1917) |
| اللواء | Al-Liwa | The Banner/Standard | 1900 | Nationalist newspaper; founder Mustafa Kamil | Limited digitization |

#### 5.7.3 Key Linguistic Challenges

- **Register variation:** Formal Modern Standard Arabic (fuṣḥā) in official documents vs. Egyptian Arabic influences in popular press
- **Foreign vocabulary layers:** Turkish (administrative, pre-1914), French (legal, technical), English (post-1882 administration), Italian (commercial, especially Alexandria)
- **Calendar systems:** Hijri and Gregorian (increasingly dominant post-1875)
- **Bilingual documents:** Arabic-French or Arabic-English in official contexts

#### 5.7.4 NER Framework Considerations

| Category | Examples | Notes |
|----------|----------|-------|
| **Persons** | Muhammad Ali, Ismail Pasha, Saad Zaghloul, Mustafa Kamil | Rulers, nationalists |
| **Institutions** | Khedivate, Wafd Party, Mixed Courts | Political and legal bodies |
| **Places** | Cairo, Alexandria, Suez Canal | Administrative and strategic locations |
| **Events** | Urabi Revolt, Dinshaway Incident, 1919 Revolution | Foundational nationalist events |

#### 5.7.5 Protocols Developed

*To be developed*

#### 5.7.6 HTR Project Corpus Analysed

*To be determined*

---

## 6. Script Families and Directionality

The portfolio spans **five distinct script families**:

| Script Family | Direction | Projects | Two-Stage Pipeline |
|---------------|-----------|----------|-------------------|
| **Perso-Arabic** | RTL | Ottoman Turkish, [Egyptian Arabic] | Yes; [TBD] |
| **Cyrillic** | LTR | Bulgarian | Yes |
| **Greek** | LTR | Greek | Yes |
| **Armenian** | LTR | Armenian | TBD |
| **Roman** | LTR | Albanian, Modern Turkish | Yes; Zero-shot experimental |

RTL scripts present distinct challenges for AI processing:
- Line-breaking and text flow assumptions in training data
- Bidirectional text handling when Arabic/Persian vocabulary appears within Turkish syntax
- Visual grounding models potentially trained predominantly on LTR materials

---

## 7. Methodology: Forensic A Priori Study and Empirical Testing

Effective HTR protocol development requires both:

### 7.1 A Priori Forensic Study
Before processing any document, understanding:
- Paleographic conventions of the period and genre
- Printing technology (lithograph, movable type, manuscript)
- Expected vocabulary register and linguistic layers
- Calendar and dating systems in use
- Genre conventions (official gazette vs. personal letter vs. chronicle)

### 7.2 Empirical Testing
Systematic validation through:
- Character Error Rate (CER) and Word Error Rate (WER) calculations
- Multiple-run variance analysis (e.g., five Gemini outputs from same image)
- Character-by-character, word-by-word, and semantic-concept comparison
- "Cold reading" experiments to test anchoring bias

*Cold reading: A verification methodology where a second reader examines source images without prior exposure to AI-generated transcriptions, preventing the first output from "anchoring" subsequent readings. This tests whether human verifiers unconsciously confirm AI outputs rather than independently assessing the source.*

**Key Finding:** AI model outputs cluster in unexpected patterns, suggesting paleographic ambiguity in source documents rather than pure stochastic variance.

---

## 8. Collaborative Context

### 8.1 AI + History Collaboratory

**GitHub:** https://github.com/Addaci/ai-and-history-collaboratory/

The AI + History Collaboratory is an online forum with synchronous and asynchronous components. We meet monthly online and maintain a GitHub repository (with wiki and discussion board) for asynchronous communication between sessions. The 2025/26 season runs for six monthly sessions from December 2025 to May 2026, with a possible History Hackathon in June 2026.

The HTR research will be presented to the Collaboratory on **20 January 2026**, in a session focused on HTR methodologies.

**Team Members:**
Gavin Beinart-Smollan | Maurice Brenner | David Brown | Abi Cunningham | Marc Eagle | Jacob Forward | Colin Greenstreet (convenor) | Thiago Krause | Oren Okhovat | Mark L. Thompson | Sam Kaislaniemi

### 8.2 Future Directions
A multilingual HTR demonstration project is in development, responding to a challenge posed by Professor Tim Hitchcock. Further details will be circulated to collaboratory members prior to the January 20th session.

---

## 9. Next Steps

1. **Corpus Expansion:** Additional Takvîm-i Vekâyi issues from 1834–1836 period
2. **Post-Processing Layer:** Conceptual-historical analysis workflows (kept separate from forensic capture protocols)
3. **Cold Reading Experiments:** Testing anchoring bias in verification stages
4. **Cross-Language Development:** Advancing Bulgarian, Greek, and Armenian projects
5. **Model Configuration Documentation:** Adding tested model/parameter specifications to skill files

---

## Appendix A: Project File Inventory

*[See accompanying JSON file: HTR_Project_Appendix_20260102.json]*

---

## Appendix B: Claude Project Configurations

*[See accompanying JSON file: HTR_Project_Appendix_B_20260102_v2.json]*

Contains: Project definitions, memories, instructions, skill files, and corpus details for all seven language projects (Ottoman Turkish, Albanian, Bulgarian, Modern Turkish, Greek, Armenian, [Planned] Egyptian Arabic).

---

## Document Control

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-02 | Initial draft overview |
| 2.0 | 2026-01-02 | Incorporated corrections: creation order, two-stage pipeline languages, linguistic scope; added document types with original scripts |
| 3.0 | 2026-01-02 | Corrected to five script families; expanded historical context (1830–1920s) for each language with events affecting documents and NER; added Tiflis/Eastern Armenian press; comprehensive newspaper/gazette coverage |
| 4.0 | 2026-01-02 | Fixed Armenian script (Ադ etc.); added Greek script for Constantinople press; renamed "Corpus Coverage" to "HTR Project Corpus Analysed"; added cold-reading explanation; removed Frameworks subsection; updated AI + History Collaboratory with GitHub link |
| 5.0 | 2026-01-02 | Completed all language sections with protocols and corpus analysed from project memories; confirmed two-stage pipeline status for Albanian, Bulgarian, Greek; added Modern Turkish methodology and experiment results; added Armenian foundational reference; expanded Egyptian Arabic historical context (1828–1920s); created comprehensive Appendix B JSON |

