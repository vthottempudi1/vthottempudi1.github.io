# SEIP Portfolio: Competitor Analysis by Project

## Project 1: Scientific Evidence Intelligence Platform (Chemistry)

### Shortlisted Repos

| Repo | Competition Level | Notes |
|------|------------------|-------|
| Future-House/paper-qa | **HIGH** | Closest match on citation-grounded scientific QA + RCS. Directly competes on literature synthesis. |
| ur-whitelab/chemcrow-public | **MEDIUM** | Chemistry-agent tooling (RDKit/PubChem/papers). Partial overlap on chemistry workflows, not on evidence verification. |
| langchain-ai/langgraph | **NONE** | Infrastructure dependency for critic/verifier loops. Not a competitor. |
| qdrant/qdrant | **NONE** | Vector store backbone. Not a competitor. |
| UKPLab/sentence-transformers | **NONE** | Embedding baseline library. Not a competitor. |

### Your Differentiation

✓ Molecule-first production UX (name/SMILES/InChIKey/CAS → report)  
✓ Live ingestion pipeline with refresh + dedup lifecycle  
✓ Explicit contradiction/consensus section (not just one answer)  
✓ Verifier/critic gating before output (grounding + retraction checks)  
✓ Tested against distractor/noise sets (near-miss chemistry papers)  
✓ Domain-config architecture (Chemistry now, Drug Discovery next)  

---

## Project 2: Drug Discovery Copilot

### Shortlisted Repos

| Repo | Competition Level | Notes |
|------|------------------|-------|
| OpenBabel/openbabel | **NONE** | Cheminformatics toolkit. Dependency, not competitor. |
| rdkit/rdkit | **NONE** | Core molecule parsing library. Foundational dependency. |
| chemprop/chemprop | **INDIRECT** | Competes only on property prediction model performance (ADMET). Not a full copilot product. |
| deepchem/deepchem | **INDIRECT** | ML framework ecosystem. Not a product-level copilot competitor unless assembled into full app. |
| TherapeuticsDataCommons/TDC | **NONE** | Benchmark/dataset ecosystem. Used for evaluation, not competition. |
| ChEMBL/ChEMBL_Structure_Pipeline | **NONE** | Data curation utility. Supports ingestion quality. |

### Your Differentiation

✓ Citation-grounded decision support (not black-box scores)  
✓ Explicit evidence strength + contradiction surfacing  
✓ Traceable "advance/discard" rationale linked to sources  
✓ Clear boundary between preclinical vs clinical evidence  
✓ Production workflow integration (refresh, monitoring, eval harness)  
✓ Decision Support Layer with citation-grounded signals  

---

## Project 3: Regulatory Affairs Copilot

### Shortlisted Repos

| Repo | Competition Level | Notes |
|------|------------------|-------|
| openFDA/api-examples | **NONE** | Official API examples. Data source, not competitor product. |
| RudolfCardinal/python-hl7 | **NONE** | HL7 parsing library. Infrastructure utility. |
| dbt-labs/dbt-core | **NONE** | Data transformation framework. ETL infrastructure. |
| great-expectations/great_expectations | **NONE** | Data quality testing framework. Pipeline infrastructure. |

### Your Differentiation

✓ Regulatory reasoning over multiple sources (guidance + warnings + labels)  
✓ Superseded/withdrawn guidance detection (version-aware reasoning)  
✓ Citation-grounded outputs with full audit trail  
✓ Production-ready workflows (refresh, validation, monitoring)  
✓ Temporal reasoning across guidance versions  
✓ No licensing gap (openFDA/EMA guidance are public data)  

---

## Project 4: Retrosynthesis Planner

### Shortlisted Repos

| Repo | Competition Level | Notes |
|------|------------------|-------|
| MolecularAI/aizynthfinder | **HIGH** | Direct competitor. Template + policy + MCTS architecture nearly identical to your plan. Production system by AstraZeneca. |
| ASKCOS/askcos-core | **HIGH** | Direct competitor. MIT's broad retrosynthesis ecosystem. Established reference implementation. |
| rxn4chemistry/rxnmapper | **NONE** | Atom mapping component tool. Used inside pipelines, not a full planner. |
| pschwllr/MolecularTransformer | **MEDIUM** | Competes with your stretch transformer tier (seq2seq). Not full planner stack by itself. |
| wengong-jin/icml18-jtnn | **LOW** | Molecular generation context. Less direct than route-planning systems. Reference for understanding landscape. |

### Your Differentiation

✓ Built on proven patterns (AiZynthFinder/ASKCOS lineage), not novel  
✓ Rigorous evaluation (top-k exact match + round-trip accuracy + expert spot-checks)  
✓ Integration with SEIP evidence layer (route + safety/literature context in one flow)  
✓ Capstone deployment as part of unified lab assistant  
✓ Both template-based AND transformer-based tiers for head-to-head comparison  

---

## Summary

| Project | High Competition | Medium | Indirect | None |
|---------|------------------|--------|----------|------|
| **1. SEIP Chemistry** | paper-qa | ChemCrow | — | 3 repos |
| **2. Drug Discovery** | — | chemprop, deepchem | — | 4 repos |
| **3. Regulatory Affairs** | — | — | — | 4 repos (all infra) |
| **4. Retrosynthesis** | AiZynthFinder, ASKCOS | MolTransformer | JTNN | 2 repos |

### Key Takeaway

- **Projects 1 & 4** have real product-level competitors.
- **Projects 2 & 3** have mostly component/infrastructure competition.
- Your moat across all projects: **production-grade deployment, evidence grounding, and explicit confidence/contradiction handling** — not claimed uniquely by any of these repos.

---

## 12-Week Execution Plan (Projects 1–4)

### Strategy

- **Deep builds:** Project 1 (SEIP), Project 4 (Retrosynthesis)
- **Scoped proofs:** Project 2 (Drug Discovery), Project 3 (Regulatory Affairs)

### Weeks 1–4: Project 1 (SEIP) — Flagship

#### Week 1 — Production MVP path

**Deliverables**
- Molecule input → resolver → ingestion → retrieval → cited report (end-to-end live)
- Minimal deployed API/UI on AWS
- Source list in output (PMID/DOI links)

**Definition of Done (DoD)**
- 10 live molecule queries run successfully
- No uncited claims in output format

#### Week 2 — Retrieval quality

**Deliverables**
- Hybrid retrieval (dense + BM25) + reranker
- Metadata-aware filtering (year, section, retraction flag)

**DoD**
- Baseline vs hybrid comparison on 20 test queries
- Retrieval precision report committed in repo

#### Week 3 — Verifier + contradiction

**Deliverables**
- Contradiction/consensus module
- Critic/verifier node with retry loop
- Confidence language policy (strong/moderate/limited evidence)

**DoD**
- Planted contradiction test passes
- Ungrounded claim rejection works in automated test

#### Week 4 — Eval + reliability hardening

**Deliverables**
- Gold set (15–20 questions) + distractor/noise test harness
- CloudWatch dashboards/alarms
- README with architecture + boundaries

**DoD**
- Metrics page in repo (precision, citation accuracy, contradiction handling)
- Deployed URL + uptime evidence

### Weeks 5–8: Project 4 (Retrosynthesis) — Architecture Range Proof

#### Week 5 — Data + template engine

**Deliverables**
- USPTO-50k preprocessing
- Template extraction + application pipeline

**DoD**
- Can generate valid precursor candidates for sample targets

#### Week 6 — Expansion policy model

**Deliverables**
- Train policy/ranker for precursor prioritization
- Evaluation script for top-k single-step prediction

**DoD**
- Top-k metrics logged + reproducible run script

#### Week 7 — MCTS multi-step planning

**Deliverables**
- MCTS controller + pruning strategy
- Multi-step route generation

**DoD**
- Produces complete routes for benchmark subset

#### Week 8 — Validation + deploy

**Deliverables**
- Round-trip check (forward model validation)
- Basic route visualization + deployed API

**DoD**
- top-1/top-5/top-10 + round-trip metrics published
- Demo endpoint live

### Weeks 9–10: Project 2 (Drug Discovery) — Scoped Extension

#### Week 9 — Domain config + sources

**Deliverables**
- Reuse SEIP core; swap in Drug Discovery config
- Add structured metadata (target, indication, MoA, phase)

**DoD**
- 10 drug-discovery queries with grounded sources

#### Week 10 — Decision support layer

**Deliverables**
- Binary advance/discard recommendation with rationale
- Explicit preclinical vs clinical evidence separation

**DoD**
- Every recommendation links to supporting citations
- “Insufficient evidence” fallback implemented

### Weeks 11–12: Project 3 (Regulatory Affairs) — Scoped Extension

#### Week 11 — Regulatory ingestion + temporal logic

**Deliverables**
- openFDA + FDA guidance ingestion
- Version/superseded status checks in metadata

**DoD**
- Query can distinguish current vs superseded guidance

#### Week 12 — Regulatory report + polish

**Deliverables**
- Guidance-change summary template
- Submission-readiness checklist output
- Final portfolio packaging across all 4 projects

**DoD**
- 8–10 regulatory benchmark questions pass grounding checks
- Final comparison matrix + demo video links in master README

### Weekly Cadence (Strict)

- **Monday:** implement core feature
- **Tuesday:** tests + edge cases
- **Wednesday:** eval + metrics
- **Thursday:** deploy + observability
- **Friday:** README/docs/demo clip + backlog prune

### Hard Rules (Critical)

1. No new scope unless current week DoD is complete.
2. Every project must have: live demo + eval table + failure mode examples.
3. Prefer boring reliability over flashy extra features.
4. Keep Projects 2 and 3 scoped to one high-value workflow each.
