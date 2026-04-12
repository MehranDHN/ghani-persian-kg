# Ghani Persian Cultural Heritage Knowledge Graph

**An Open Linked Data Edition of the Ghassem Ghani Collection (MS 235) at Yale University**

![Project Banner](https://pbs.twimg.com/profile_banners/222009940/1770956354/1080x360)  


### Preface

The **Ghassem Ghani Collection** is one of the richest archives of Qajar-era Persian documents, containing over 1,000 handwritten and typed materials spanning political, social, economic, and cultural life in 19th- and early 20th-century Iran. Held at Yale University’s Manuscripts and Archives (Sterling Memorial Library), the collection includes royal correspondence, official reports, private letters, petitions from ordinary citizens, and important historical documents related to the Constitutional Revolution, reformist movements, and key personalities of the period.

[The original online repository at Yale](https://ghani.macmillan.yale.edu/) suffers from a dramatically poor digital design: no API, no bulk export, rudimentary search, and metadata locked in static HTML tables. This project transforms that inaccessible resource into a clean, open, machine-readable, and fully linked knowledge graph preserving every relation between documents, people, places, technical terms, chronology, transcriptions, and PDFs.
  
This repository serves as a **standalone public mirror** and the foundation for an iteratively extensible Persian Digital Cultural Heritage Knowledge Graph.

### Project Goals

- Create a complete, high-fidelity open mirror with **100% preserved relations** between all metadata, transcriptions, and PDFs.
- Build a minimal yet extensible RDF/Linked Data model suitable for cultural heritage.
- Provide permanent, citable access via GitHub and Internet Archive.
- Enable reuse by researchers, digital humanists, historians, and AI applications focused on Persian heritage.
- Follow an iterative development approach: start minimal, extend gradually.

### Pipeline Overview

```mermaid
flowchart TD
    A[1. Discover Categories<br/>GI • GII • GIII • GIIIA • GIV • ...] 
    --> B[2. Scrape All Pages with Pagination<br/>?page=0, ?page=1, ...]
    --> C[3. Extract Table Metadata<br/>Description, Personalities(FHKB/WikiData Support), Places(TGN),<br/>Technical Terms, Chronology<br/>Phisicall Structures(Boxes/Files/...)<br/>Document types based on AAT]
    --> D[4. Enrich Detail Pages<br/>Full Persian Transcription]
    --> E[5. Download Transcription PDFs<br/>+ Compute SHA-256 Hash]
    --> F[6. Build Central Manifest JSON<br/>Single Source of Truth]
    --> G[7. Generate RDF Turtle Files<br/>Using Minimal Ontology]
    --> H[8. Upload PDFs + Metadata<br/>to Internet Archive(IIIF Support)]
    --> I[9. Publish Full Repository<br/>on GitHub]

    style A fill:#e3f2fd,stroke:#1976d2
    style G fill:#f3e5f5,stroke:#7b1fa2
    style I fill:#e8f5e9,stroke:#388e3c
```

### Repository Structure   


```
ghani-persian-kg/
├── README.md
├── LICENSE
├── scripts/
│   ├── p1Cataloge.py          # Full scraper with pagination & error handling
│   └── rdf_generator.py       # Converts manifest → RDF (coming soon)
├── data/
│   ├── raw/
│   │   ├── ghani_collection_manifest.json
│   │   └── failed_or_skipped.json
│   └── rdf/                   # Generated .ttl files
├── pdfs/                      # Local PDF copies (optional via Git LFS)
├── vocab/
│   └── ghani.ttl              # Minimal custom ontology
└── docs/
    └── process.md             # Detailed technical notes (optional)


```
Made with ❤️ with the help of Grok and Claude AI Engine for Persian Digital Cultural Heritage
