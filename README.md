# EPMwDC: Dual-Use Regulatory Compliance Ontology

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Ontology-based regulatory compliance requirements specification for dual-use AI systems**

This repository contains the **research artefacts** and **validation materials** for the EPMwDC (Espionage Prevention and Monitoring with Dual Compliance) framework — an ontology-based methodology for automated regulatory compliance requirements specification across civilian and defence deployment contexts.

## Publication

**Sabaliauskaitė, G., Paskauskas, R. A., Bružė, E., Matulytė, R., & Lavišius, T.** (2026). Automated Regulatory Compliance for AI Systems in Security Domain: From the EU AI Act to Dual-Use Deployment Contexts. *Open Research Europe* (forthcoming).

## Repository Contents

### `/ontology/` — Core OWL Ontology

| File | Description |
| --- | --- |
| `epmwdc-dual-use-ontology-v2.ttl` | Core RDF/Turtle ontology (v2.0) defining classes, properties, and 11 requirement instances across civilian and defence domains |

### `/ontology/v1/` — Development History

| File | Description |
| --- | --- |
| `base-civil-defence-ontology.ttl` | v1.0 base ontology with cross-domain regulatory hierarchy |
| `baseline-civil-pattern.ttl` | v1.0 civilian compliance pattern (requirement groups) |
| `baseline-defence-pattern.ttl` | v1.0 defence compliance pattern (requirement groups) |
| `baseline-domain-tags.ttl` | v1.0 domain applicability assertions |

### `/queries/` — SPARQL Query Library

| File | Description |
| --- | --- |
| `sparql-queries.sparql` | All SPARQL queries referenced in the paper, including: (A) retrieve all requirements across both domains, (B) cross-domain pairing, (C) defence domain requirements, (D) DEF-R4 hierarchical decomposition, (E) deployment-specific checklist generation |

### `/visualisations/` — Interactive Demonstrations

| File | Description |
| --- | --- |
| `EPMwDC-Knowledge-Graph.html` | Knowledge graph visualisation (corresponds to Figure 2) |
| `EPMwDC-Case-Study.html` | Espionage detection system component-to-requirement mapping |

### `/docs/` — Documentation

| File | Description |
| --- | --- |
| `methodology.md` | Six-step methodology summary with cross-references to paper sections |

## Framework Overview

The EPMwDC ontology models regulatory compliance for dual-use AI technologies across two deployment domains:

- **Civilian domain** — governed by EU regulations (GDPR, NIS2 Directive, EU AI Act, CER Directive)
- **Defence domain** — governed by NATO frameworks (NIAP, NSP, NATO Cyber Defence Policy, TEMPEST) plus applicable GDPR obligations

Requirements are organised by:

- **Lifecycle phase**: Design & Development (pre-deployment) vs. Usage & Maintenance (post-deployment)
- **Category**: Privacy-related vs. Security-related
- **Design principle**: Privacy-by-Design (GDPR Art. 25) vs. Security-by-Design (GDPR Art. 32)

### Key Findings

1. **GDPR applies across both domains** — privacy requirements (R1, R3) derive from GDPR regardless of deployment context
2. **Security frameworks diverge** — civilian deployments use NIS2; defence deployments require NATO-specific controls
3. **Defence compliance is additive, not substitutive** — all applicable civilian requirements plus NATO-specific obligations

## Quick Start

### Load the Ontology

Import `ontology/epmwdc-dual-use-ontology-v2.ttl` into [Protégé](https://protege.stanford.edu/) or any OWL-compatible editor.

### Run SPARQL Queries

Load the ontology into [Stardog Cloud](https://cloud.stardog.com/) or another SPARQL endpoint, then execute queries from `/queries/`.

### Explore Interactively

Open the HTML files in `/visualisations/` in any modern browser.

## Namespace

| Prefix | URI |
| --- | --- |
| `rc:` | `http://l3ce.lt/ontology/regulatory-compliance#` |

## Related Resources

- **5G Hybrid Threats Ontology:** <https://github.com/SecOntologyLab/5G-hybrid-threats>
- **HIPSTer Ontological Framework:** <https://github.com/SecOntologyLab/hipster-ontology>

## Citation

```bibtex
@article{sabaliauskaite2026epmwdc,
  title={Ontology-Based Regulatory Compliance Requirements Specification for Dual-Use AI Systems},
  author={Sabaliauskaite, Giedre and Paskauskas, R. Andrew and Bruze, Evaldas and Matulyte, Raminta and Lavisius, Tomas},
  journal={Open Research Europe},
  year={2026}
}
```

## Acknowledgements

This research was prepared as part of the project "Implementation of Mission-Based Science and Innovation Programs" (Project No. 02-002-P-0001), financed by the European Union through the Recovery and Resilience Facility (2021–2027 programming period, New Generation Lithuania plan), and co-funded by the state budget of the Republic of Lithuania administered via the Research Council of Lithuania (Lietuvos Mokslo Taryba).

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). See the [LICENSE](LICENSE) file for details.
