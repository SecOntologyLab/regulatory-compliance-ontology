# Six-Step Methodology for Dual-Use AI System Regulatory Compliance Requirements Specification

This document summarises the ontology-based methodology proposed in the paper. For full details, including validation results and case study analysis, refer to the publication.

## Scope

The methodology takes civilian and defence regulations as input, performs regulatory compliance analysis, and specifies requirements organised by:

- **Deployment domain**: Civilian use vs. Defence use
- **Lifecycle phase**: Design & Development (pre-deployment) vs. Usage & Maintenance (post-deployment)
- **Requirement category**: Privacy-related vs. Security-related
- **Design principle**: Privacy-by-Design (GDPR Art. 25) vs. Security-by-Design (GDPR Art. 32)

## Steps

### Step 1: Problem Framing and Regulatory Scoping

**Focus:** Establish dual-use context and identify applicable regulatory landscape.

**Activities:**
- Define the technology and its deployment contexts (civilian, defence, or both)
- Identify applicable civilian regulations (GDPR, NIS2, EU AI Act, CRA, national laws)
- Identify applicable defence frameworks (NATO NIAP, NSP, Cyber Defence Policy, TEMPEST, STANAG)
- Document where requirements overlap, diverge, or conflict

**Output:** Regulatory scope document listing all applicable frameworks by domain, with initial mapping of regulatory hierarchies (international → EU/NATO → national).

---

### Step 2: Conceptual Framework Development

**Focus:** Translate regulatory scoping into a structured conceptual model.

**Activities:**
- Create visual representation showing two top-level compliance domains, regulatory source hierarchies, lifecycle phase decomposition, and requirement categorisation
- Map design principles to lifecycle phases
- Define structural parallelism: both domains follow identical phase and category organisation

**Output:** Conceptual diagram (see paper Figure 1) and structural template (domain × phase × category).

---

### Step 3: Ontology Design and Implementation

**Focus:** Formalise the conceptual model as a machine-readable ontology in RDF/Turtle.

**Activities:**
- Define namespace: `rc: <http://l3ce.lt/ontology/regulatory-compliance#>`
- Create class hierarchy: `RegulatoryCompliance` → domain classes → regulatory framework classes → specific regulations
- Define structural classes: `LifecyclePhase`, `DesignPrinciple`, `RequirementCategory`, `Requirement`
- Define object properties: `governedBy`, `hasPhase`, `hasRequirement`, `derivedFrom`, `hasRequirementCategory`, `appliesToDomain`, `hasDefenceEquivalent` / `hasCivilianEquivalent`
- Define datatype properties: `requirementIdentifier`, `articleReference`, `legalBasis`

**Output:** RDF/Turtle ontology file → `ontology/epmwdc-dual-use-ontology-v2.ttl`

---

### Step 4: Domain-Specific Requirements Population

**Focus:** Instantiate concrete regulatory requirements within the ontological framework.

**Activities:**
- For each domain (civilian, defence), create requirement instances following the structural template:
  - Design/Development phase: one privacy-related (R1), one security-related (R2)
  - Usage/Maintenance phase: one privacy-related (R3), one security-related (R4)
- Populate each instance with: identifier, label, derivedFrom, articleReference, legalBasis, hasRequirementCategory, appliesToDomain
- Where regulations support decomposition, create sub-requirements (e.g., DEF-R4 → DEF-R4-ART3, DEF-R4-ART5, DEF-R4-ART7)

**Output:** 8 primary requirements (CIV-R1–R4, DEF-R1–R4) plus 3 sub-requirements, derived from 7 regulatory sources.

---

### Step 5: Knowledge Graph Deployment

**Focus:** Load ontology into a triplestore and verify structural integrity.

**Activities:**
- Create database in target platform (e.g., Stardog Cloud)
- Load RDF/Turtle ontology file
- Verify triple count and structural integrity
- Configure visualisation for knowledge graph exploration

**Output:** Deployed knowledge graph accessible for querying → see `visualisations/EPMwDC-Knowledge-Graph.html` for interactive representation.

---

### Step 6: SPARQL-Based Validation and Cross-Domain Analysis

**Focus:** Validate framework through structured queries and demonstrate analytical capabilities.

**Activities:**
- Validation queries verifying all instances are correctly typed, domain-tagged, phase-associated, and source-linked
- Cross-domain comparison queries pairing civilian and defence requirements by structural position
- Iterative refinement based on query results

**Output:** Validated query results (paper Tables 2–5), cross-domain comparison tables, SPARQL query library → `queries/sparql-queries.sparql`

## Summary Table

| Step | Focus | Key Output |
| --- | --- | --- |
| 1 | Problem Framing & Regulatory Scoping | Regulatory scope document |
| 2 | Conceptual Framework Development | Visual model and structural template |
| 3 | Ontology Design & Implementation | RDF/Turtle ontology file |
| 4 | Domain-Specific Requirements Population | Populated civilian and defence modules |
| 5 | Knowledge Graph Deployment | Deployed, navigable knowledge graph |
| 6 | SPARQL-Based Validation & Analysis | Validated results and query library |

## Key Innovation

The methodology transforms regulatory requirements into **executable compliance logic** rather than static documentation. This enables:

1. **Query-based compliance verification** — SPARQL retrieves applicable obligations dynamically by deployment context
2. **Cross-domain alignment** — structural pairing supports automated gap analysis
3. **Hierarchical decomposition with traceability** — article-level sub-requirements map to specific system components
4. **Conditional applicability modelling** — domain tagging represents context-dependent regulatory scope

## Case Study Validation

The methodology was validated through application to an AI-powered espionage detection system — see `visualisations/EPMwDC-Case-Study.html` for an interactive demonstration of component-to-requirement mapping across civilian and defence domains.

## Citation

**Sabaliauskaitė, G., Paskauskas, R. A., Bružė, E., Matulytė, R., & Lavišius, T.** (2026). Automated Regulatory Compliance for AI Systems in Security Domain: From the EU AI Act to Dual-Use Deployment Contexts. *Open Research Europe* (forthcoming).
