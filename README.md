# 🌳 Shajjra (شجرہ) — The Living Digital Genealogy & 45-Generation Lineage Archive

> An open-access genealogical archive, 45-generation lineage atlas, and high-performance interactive family tree engine preserving South Asian, Arab, and Islamic ancestry (*Shajra-e-Nasab*).

[![Live Platform](https://img.shields.io/badge/Live_Archive-shajjra.com-00d26a?style=for-the-badge&logo=google-chrome&logoColor=white)](https://shajjra.com)
[![Interactive Tree](https://img.shields.io/badge/Canvas_Tree-Interactive_Explorer-326CE5?style=for-the-badge&logo=d3.js&logoColor=white)](https://shajjra.com)
[![Pedigree Charts](https://img.shields.io/badge/Pedigree_Charts-Ancestral_Lineage-8A2BE2?style=for-the-badge)](https://shajjra.com)
[![Lineage Directory](https://img.shields.io/badge/Ancestral_Directory-1080+_Members-38BDF8?style=for-the-badge)](https://shajjra.com)
[![Architect](https://img.shields.io/badge/Curator-Naveed_Kumbhar-ff69b4?style=for-the-badge&logo=github&logoColor=white)](https://naveedkumbhar.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

---

## 🎯 Why This Platform Exists

Traditional genealogical platforms (Ancestry, MyHeritage, FamilySearch) are fundamentally tailored for Western nuclear family structures. They struggle with:
- **Patrilineal Shajra-e-Nasab (شجرہ نسب):** Preserving unbroken patrilineal descents connecting contemporary families back across 40+ generations.
- **Complex Consanguinity & Cousin Marriages:** Multi-parental cyclic unions and pedigree collapse (*implex*) that break standard binary family tree renderers.
- **Honorific Titles & Religious Epithets:** Specialized handling for sacred prefixes and honorifics (`(a.s)`, `(r.a)`, Syed, Alvi, Hashmi, Kumbhar).
- **Historical Migration Records:** Tracking clan proliferation from the Arabian Peninsula through Persia into Sindh, Punjab, and South Asia.

**[Shajjra.com](https://shajjra.com)** was engineered to bridge this gap: an enterprise-grade digital archive documenting **over 1,080 connected family members across 45 generations** with dynamic pan-and-zoom tree canvases, 5-generation pedigree charts, and structured descendant directories.

---

## 🚀 Live Companion Platform

Experience the live platform and genealogical explorer:

| Component | URL | Core Features |
|:---|:---|:---|
| 🌐 **Main Digital Archive** | [`shajjra.com`](https://shajjra.com) | Global ancestral search, real-time lineage discovery, and verified historical records. |
| 🌳 **Interactive Tree Canvas** | [`shajjra.com/users/1/tree`](https://shajjra.com) | Drag-to-pan canvas, floating zoom controls (25%–200%), and dynamic `[ ↑ Up to Father ]` navigation. |
| 📊 **Pedigree Chart Explorer** | [`shajjra.com/users/1/chart`](https://shajjra.com) | Direct 5-generation vertical pedigree chains with sibling cards and quick jump points. |
| 💍 **Marriage Registry** | [`shajjra.com/marriages`](https://shajjra.com) | Cross-branch marital connections, spouse biographies, and inter-clan alliances. |
| 📖 **Ancestral Directory** | [`shajjra.com/directory`](https://shajjra.com) | Complete indexed directory organized alphabetically, by generation, and by branch color. |
| 🎂 **Family Milestones** | [`shajjra.com/birthdays`](https://shajjra.com) | Community calendar tracking generational milestones and memorial dates. |

---

## 🏛️ Lineage Architecture: 45 Generations

The Shajjra archive traces an unbroken patrilineal chain spanning over fourteen centuries:

```
[Generation 1: Root Patriarch — Classical Antiquity]
         │
         ▼
[Generations 2–15: Early Arab & Classical Islamic Predecessors]
         │
         ▼
[Generations 16–28: Scholar, Guild & Artisan Migrations across Persia / Khorasan]
         │
         ▼
[Generations 29–38: Indus Valley Settlements in Sindh & Punjab]
         │
         ▼
[Generations 39–45: Contemporary Living Lineages & Global Diaspora]
```

### Key Preserved Heritage Pillars
- **76 Curated Branch Colors:** Distinct clan and branch identifiers for instant visual kinship differentiation.
- **Honorific Integrity:** Automated typographic rules ensuring honorifics (`(a.s)`, `(r.a)`, `(rh)`) remain intact during title-casing.
- **Privacy-First Public Architecture:** Living members' PII (contact numbers, personal emails, physical residences) are strictly segregated from public indexing.

---

## 📚 Technical & Cultural Documentation

Explore the in-depth guides included in this repository:

1. [**Shajra-e-Nasab Preservation Guide**](guides/shajra-nasab-preservation-guide.md): Historical foundations, oral tradition documentation, and migration geography.
2. [**Pedigree Charting & Tree Visualization Algorithms**](guides/pedigree-charting-algorithms.md): Rendering deep genealogies using CSS transforms, canvas coordinate mapping, and responsive connectors.
3. [**Consanguinity, Pedigree Collapse & Recursive Graphs**](guides/consanguinity-and-graph-recursion.md): Resolving cousin marriages and cyclic paths in relational SQL and graph databases.

---

## 🧬 Open Genealogical Data Model (JSON Schema)

To promote open-source genealogical preservation, public tree nodes follow the standardized specification defined in [`schema/shajjra-node.schema.json`](schema/shajjra-node.schema.json):

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "ShajjraMemberNode",
  "type": "object",
  "properties": {
    "id": { "type": "string", "example": "1" },
    "name": { "type": "string", "example": "Hazrat Imam Ali (a.s)" },
    "nickname": { "type": "string", "example": "Abu Turab" },
    "gender_id": { "type": "integer", "enum": [1, 2] },
    "father_id": { "type": "string", "example": "2" },
    "mother_id": { "type": "string", "example": "3" },
    "generation": { "type": "integer", "example": 1 },
    "text_color": { "type": "string", "example": "#ffffff" },
    "bg_color": { "type": "string", "example": "#166534" },
    "profile_url": { "type": "string", "format": "uri" }
  },
  "required": ["id", "name", "gender_id"]
}
```

A sample public dataset with classical foundational lineage records is available in [`data/sample-classical-lineage.json`](data/sample-classical-lineage.json).

---

## 🎨 Open-Source Tree CSS

Looking to build your own lightweight, responsive genealogical tree without heavy JavaScript charting libraries?  
Check out [`assets/tree-modern.css`](assets/tree-modern.css) — a pure CSS solution with elegant gold connectors, flexbox layouts, and mobile-friendly nodes.

---

## 🛠️ Technology Stack

The production application powering [shajjra.com](https://shajjra.com) utilizes:

- **Application Framework:** PHP 8.2-FPM / Laravel 10 (RESTful routing, Eloquent Mutators for title-casing)
- **Database Engine:** MariaDB 10.6 with relational foreign key constraints
- **Frontend Canvas:** CSS Modern Grid & Flexbox, SVG Viewport Scaling, Vanilla Touch/Pointer Drag-Pan
- **Infrastructure:** Ubuntu 22.04 LTS on AWS EC2, Nginx Reverse Proxy with Brotli/Gzip compression, HTTP/2 SSL
- **SEO & Discoverability:** Dynamic XML Sitemaps (3,200+ indexed URLs), JSON-LD `Person`, `BreadcrumbList`, and `WebSite` schemas

---

## 🤝 Contributing & Lineage Submissions

Have records, historical documents, or lineage corrections for your branch?
1. Check the existing directory on [shajjra.com](https://shajjra.com).
2. Open an [Issue](https://github.com/naveedkumbhar/shajjra.com/issues) or submit family records formatted according to the [Open Schema](schema/shajjra-node.schema.json).
3. Review our [Lineage Verification & Privacy Guidelines](CONTRIBUTING.md).

---

## 👨‍💻 Architect & Maintenance

Curated and engineered by **[Naveed Kumbhar](https://naveedkumbhar.com)**.  
For inquiries, lineage additions, or API access, visit [shajjra.com](https://shajjra.com).
