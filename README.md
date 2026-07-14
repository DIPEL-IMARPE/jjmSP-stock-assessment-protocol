<p align="center">
  <img src="https://img.shields.io/badge/IMARPE-DIPEL--IMARPE-0B2D4D?style=for-the-badge" alt="DIPEL-IMARPE"/>
  <img src="https://img.shields.io/badge/JJM-Model%20Protocol-007C89?style=for-the-badge" alt="JJM Model Protocol"/>
  <img src="https://img.shields.io/badge/Status-Draft-6B7280?style=for-the-badge" alt="Draft status"/>
</p>

<p align="center">
  <strong>Dirección de Investigaciones del Subsistema Pelágico</strong><br>
  <strong>Instituto del Mar del Perú — IMARPE</strong>
</p>

# Joint Jack Mackerel Model Protocol

## User guide and mathematical specification of the JJM model

This repository contains a version-controlled technical protocol for understanding, installing, configuring, running, and interpreting the **Joint Jack Mackerel model (JJM)** used for jack mackerel (*Trachurus murphyi*) stock assessment in the South Pacific.

The document was developed as an IMARPE proposal to support current and prospective users of the model. It describes the internal mathematical structure of JJM, its input and control files, parameter estimation, biological reference points, projections, and a reproducible case study.

> **Important:** This repository is an independent technical contribution from IMARPE. The authoritative JJM source code is maintained by SPRFMO and should be consulted when verifying the current model implementation.

## Repository name

```text
jjm-sp-model-protocol
```

The repository name follows the institutional naming convention:

```text
jjm       = jack mackerel
sp        = South Pacific scope
model     = Joint Jack Mackerel assessment model
protocol  = version-controlled technical procedure and specification
```

## Current version

| Field | Value |
|---|---|
| Current draft version | `v0.0.0` |
| Version date | `2024-12-08` |
| Document edition | `01` |
| Document revision | `00` |
| Document language | English |
| Source format | LaTeX |
| Model implementation | AD Model Builder |
| Status | Draft technical proposal |

Version `v0.0.0` should be treated as an initial draft. The first technically reviewed and institutionally approved version should be published as `v1.0.0`.

## Purpose

The protocol is intended to:

- provide a concise technical overview of the JJM model;
- document the assumptions underlying stock, fishery, and observation processes;
- describe the mathematical equations implemented in the model;
- explain the structure and role of data and control files;
- identify the main model parameters and optimization phases;
- describe likelihood components, penalties, and prior distributions;
- explain the calculation of Maximum Sustainable Yield;
- explain biological reference points and stock-status quantities;
- document replacement-yield and projection procedures;
- provide installation and model-running instructions;
- demonstrate the model through a reproducible case study;
- support training, review, collaboration, and future protocol revisions.

## Scope

The protocol covers the following technical areas:

1. JJM model history and principal assumptions
2. Stock and fishery structure
3. Population dynamics
4. Numbers at age
5. Spawning-stock biomass
6. Catches and fishing mortality
7. Recruitment and stock–recruit relationships
8. Growth and weight-at-length relationships
9. Maturity
10. Age-to-length conversion
11. Survey predictions
12. Fishery predictions
13. Selectivity
14. Likelihood components
15. Prior distributions and penalties
16. Replacement yield
17. Maximum Sustainable Yield
18. Biological reference points
19. Unfished abundance and depletion
20. Future projections
21. Data and control files
22. Model installation and execution
23. Case-study implementation
24. Interpretation of model outputs

## Model overview

The JJM model is a statistical age-structured stock-assessment model developed for jack mackerel in the South Pacific.

The model can integrate:

- fishery catches;
- fishing effort;
- abundance indices;
- catch-at-age data;
- catch-at-length data;
- survey age compositions;
- survey length compositions;
- weight-at-age information;
- maturity-at-age information;
- growth parameters;
- natural mortality;
- recruitment regimes;
- time-varying selectivity;
- projection scenarios.

The model is implemented in **AD Model Builder (ADMB)** and estimates parameters by minimizing a penalized negative log-likelihood.

## Principal model components

The model contains four major components:

```text
Stock dynamics
      +
Fishery dynamics
      +
Observation models
      +
Parameter estimation
```

### Stock dynamics

The stock-dynamics component includes:

- recruitment;
- survival;
- natural mortality;
- fishing mortality;
- numbers at age;
- spawning-stock biomass;
- total biomass;
- regime-dependent productivity;
- future population projections.

### Fishery dynamics

The fishery component includes:

- fishery-specific fishing mortality;
- fishery-specific selectivity;
- catchability;
- observed and predicted catch;
- age and length composition;
- time-varying fishing processes.

### Observation models

The model can fit:

- total catch;
- abundance indices;
- age-frequency observations;
- length-frequency observations;
- stock–recruit relationships.

Observation error and effective sample-size assumptions are specified through input and control files.

### Parameter estimation

Model parameters are estimated through phased optimization.

The objective function may include:

- catch likelihood;
- abundance-index likelihood;
- fishery age-composition likelihood;
- fishery length-composition likelihood;
- survey age-composition likelihood;
- survey length-composition likelihood;
- recruitment likelihood;
- selectivity penalties;
- fishing-mortality penalties;
- prior distributions;
- smoothing penalties.

## Key outputs

The protocol explains how JJM produces or derives quantities such as:

- numbers at age;
- recruitment;
- total biomass;
- spawning-stock biomass;
- fishing mortality;
- depletion;
- unfished biomass;
- replacement yield;
- Maximum Sustainable Yield;
- fishing mortality at MSY;
- biomass at MSY;
- spawning-potential ratio;
- biological reference points;
- acceptable biological catch;
- overfishing limit;
- projected catch;
- projected spawning biomass;
- catch under alternative fishing-mortality scenarios.

## Authoritative model source

The protocol was developed through a technical review of the JJM source code maintained by SPRFMO:

```text
https://github.com/SPRFMO/jjm
```

The model template analysed by the protocol is located at:

```text
https://github.com/SPRFMO/jjm/blob/main/src/jjm.tpl
```

When the source code and this protocol differ, the current authoritative model code takes precedence.

Any detected discrepancy should be documented through a GitHub issue and corrected in a reviewed protocol revision.

## Repository structure

### Current structure

```text
├── README.md
├── main.tex
├── referencias.bib
├── for_runmodel.R
├── graficofases2.jpg
├── stock1.png
├── stock2.png
└── WhatsApp Image 2024-07-05 at 4.08.37 PM.jpeg
```

### Recommended standardized structure

```text
├── README.md
├── CHANGELOG.md
├── CITATION.cff
├── LICENSE
│
├── protocol
│   ├── jjm-model-protocol.tex
│   ├── references.bib
│   ├── appendices
│   └── sections
│
├── case-study
│   ├── README.md
│   ├── scripts
│   │   └── run-jjm-case-study.R
│   ├── inputs
│   │   ├── data
│   │   └── control
│   └── outputs
│
├── figures
│   ├── optimization-phases.jpg
│   ├── stock-structure-1.png
│   ├── stock-structure-2.png
│   └── jjm-model-diagram.png
│
├── metadata
│   ├── protocol.yml
│   ├── model-version.yml
│   ├── contributors.yml
│   └── version-history.yml
│
├── archive
│   └── previous-versions
│
└── .github
    ├── CODEOWNERS
    ├── pull_request_template.md
    └── workflows
        ├── build-latex.yml
        └── link-check.yml
```

## Current-to-standardized file mapping

| Current file | Recommended file |
|---|---|
| `main.tex` | `protocol/jjm-model-protocol.tex` |
| `referencias.bib` | `protocol/references.bib` |
| `for_runmodel.R` | `case-study/scripts/run-jjm-case-study.R` |
| `graficofases2.jpg` | `figures/optimization-phases.jpg` |
| `stock1.png` | `figures/stock-structure-1.png` |
| `stock2.png` | `figures/stock-structure-2.png` |
| `WhatsApp Image 2024-07-05 at 4.08.37 PM.jpeg` | `figures/jjm-model-diagram.jpg` |

File migration should be implemented through a dedicated branch and pull request so that LaTeX references remain traceable.

## Requirements

### LaTeX

A LaTeX distribution is required.

Recommended options include:

```text
TeX Live
MiKTeX
MacTeX
```

The protocol currently requires packages for:

- mathematical notation;
- algorithms and pseudocode;
- bibliography management;
- hyperlinks;
- figures;
- source-code listings;
- section formatting.

The bibliography uses:

```text
biblatex
biber
```

### AD Model Builder

AD Model Builder is required to compile and run the JJM model.

The installed version should be documented in:

```text
metadata/model-version.yml
```

### R

R is used to support the case study and post-process model results.

The R version and package dependencies should be documented and, where possible, controlled with `renv`.

## Building the protocol

### Recommended compilation

From the repository root:

```bash
latexmk -pdf -use-biber main.tex
```

After migration to the standardized structure:

```bash
latexmk -pdf -use-biber protocol/jjm-model-protocol.tex
```

### Manual compilation

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

### Clean generated files

```bash
latexmk -c
```

Before publication, verify:

- all equations compile correctly;
- all citations are resolved;
- all figures are available;
- all hyperlinks are valid;
- all algorithm environments render correctly;
- the table of contents is complete;
- the edition and revision numbers are correct;
- the model version analysed by the protocol is documented.

## Installing and running JJM

The exact installation steps depend on the operating system and the current SPRFMO model implementation.

The general procedure is:

```text
1. Install AD Model Builder.
2. Clone or download the authoritative JJM repository.
3. Compile the JJM template.
4. Prepare the data file.
5. Prepare the control file.
6. Place the executable and input files in the run directory.
7. Run the model.
8. Review convergence and diagnostic files.
9. Process outputs.
10. Archive the complete model run.
```

A typical ADMB compilation command is:

```bash
admb jjm.tpl
```

A typical model run is:

```bash
./jjm -ind model
```

On Windows, the executable may be invoked as:

```powershell
.\jjm.exe -ind model
```

Actual filenames and command-line options must be checked against the current authoritative JJM implementation.

## Input files

The protocol documents two principal input-file types.

### Data file

```text
*.dat
```

The data file may contain:

- model dimensions;
- years;
- stocks;
- fisheries;
- observed catches;
- abundance indices;
- age compositions;
- length compositions;
- weight-at-age matrices;
- maturity information;
- survey timing;
- projection settings.

### Control file

```text
*.ctl
```

The control file may define:

- stock structure;
- parameter phases;
- selectivity options;
- recruitment regimes;
- natural mortality;
- growth options;
- priors;
- penalties;
- catchability;
- likelihood weights;
- projection scenarios;
- model-control flags.

Every case-study run should record the exact versions and checksums of both files.

## Model outputs

A JJM run may produce:

```text
*.rep
*.std
*.cor
*.par
*.log
*.eva
*.mc2
```

The exact output set depends on the model configuration and ADMB options.

The case-study documentation should explain:

- which outputs are required;
- how convergence is evaluated;
- how uncertainty is interpreted;
- how reference points are extracted;
- how projections are summarized;
- how outputs are converted into tables and figures.

## Case study

The repository includes a case study intended to illustrate model installation, configuration, execution, and interpretation.

The case study should document:

- the JJM code version;
- the data-file version;
- the control-file version;
- the operating system;
- the ADMB version;
- the R version;
- the model command;
- convergence status;
- warnings;
- output checksums;
- principal results.

The case study is educational and should not be interpreted as an official stock-assessment result unless explicitly approved and identified as such.

## Reproducibility

Each protocol release should be linked to:

- a Git commit;
- an exact protocol version;
- the JJM source-code commit reviewed;
- the ADMB version;
- the case-study input files;
- the case-study output files;
- the R environment;
- a compiled protocol PDF;
- a Git tag;
- a GitHub Release.

Recommended metadata:

```yaml
protocol:
  repository: "jjm-sp-model-protocol"
  version: "v0.0.0"
  edition: "01"
  revision: "00"
  date: "2024-12-08"

model:
  name: "Joint Jack Mackerel model"
  acronym: "JJM"
  authoritative_repository: "SPRFMO/jjm"
  source_commit: null

software:
  admb_version: null
  r_version: null
```

## Versioning

The repository should use semantic versioning:

```text
MAJOR.MINOR.PATCH
```

| Component | Meaning |
|---|---|
| `MAJOR` | Major restructuring or substantive revision of the documented model |
| `MINOR` | New compatible section, equation group, case study, or implementation guidance |
| `PATCH` | Typographical, formatting, citation, or non-substantive correction |

Examples:

```text
v0.0.0  Initial draft
v0.1.0  First complete internal review draft
v0.2.0  Revised mathematical specification
v1.0.0  First approved protocol
v1.0.1  Typographical correction
v1.1.0  New compatible case-study section
v2.0.0  Major update following a substantial JJM model revision
```

## Branching model

Recommended branches:

```text
main
release/v1.0
release/v2.0
```

Short-lived development branches should describe the change:

```text
docs/revise-population-dynamics
docs/add-input-file-guide
method/update-msy-equations
case-study/update-example
fix/correct-selectivity-equation
release/prepare-v1.0
```

Approved versions must be preserved through annotated tags and GitHub Releases.

## Change documentation

Every release should include a changelog.

Recommended structure:

```markdown
## Added

- New sections, equations, examples, or procedures.

## Changed

- Revised mathematical notation or model interpretation.

## Fixed

- Typographical, compilation, citation, or equation-reference corrections.

## Deprecated

- Procedures retained temporarily but no longer recommended.

## Removed

- Obsolete content.
```

A methodological correction should identify:

- the affected model component;
- the previous statement or equation;
- the corrected statement or equation;
- the corresponding source-code location;
- the scientific or computational justification;
- the JJM code version affected;
- the reviewers;
- the approval date.

## Review workflow

Recommended review sequence:

```text
Issue
  ↓
Technical branch
  ↓
Source-code verification
  ↓
Protocol modification
  ↓
Successful LaTeX compilation
  ↓
Pull request
  ↓
Mathematical and computational review
  ↓
Approval
  ↓
Merge
  ↓
Tag and GitHub Release
```

Before merging, verify:

- [ ] The documented equation matches the referenced JJM source code.
- [ ] Variable names are defined consistently.
- [ ] Indices and dimensions are correct.
- [ ] Input-file references are accurate.
- [ ] Algorithms and pseudocode match the implemented procedure.
- [ ] Citations are resolved.
- [ ] The LaTeX document compiles successfully.
- [ ] The case study is reproducible.
- [ ] Changes are documented in `CHANGELOG.md`.
- [ ] The protocol version is updated when required.

## File-naming convention

Repository files should use English names.

Recommended examples:

```text
jjm-model-protocol.tex
references.bib
run-jjm-case-study.R
optimization-phases.jpg
stock-structure-1.png
stock-structure-2.png
```

Avoid:

```text
main-final.tex
new-guide.pdf
figure-final2.png
document-corrected.tex
WhatsApp Image 2024-07-05 at 4.08.37 PM.jpeg
```

Source files should retain stable names. Version numbers should appear in tags, releases, and published artifact filenames.

Recommended PDF filename:

```text
jjm-sp-model-protocol-v1.0.0.pdf
```

## Citation

Users should cite the exact protocol version consulted.

Recommended provisional citation:

```text
Geronimo, M., Lujan, C., Torrejon, J., and Quispe, E.
The Joint Jack Mackerel Model: A User Guide.
Instituto del Mar del Perú, Callao, Peru.
```

The final citation should include:

- publication year;
- protocol version;
- edition and revision;
- institutional unit;
- repository URL;
- DOI, if assigned.

Citation metadata should be maintained in:

```text
CITATION.cff
```

## Contributors

Initial contributors listed in the protocol source are:

- Mirian Geronimo
- Criscely Lujan
- Josymar Torrejon
- Elmer Quispe

Contributor roles and affiliations should be recorded in:

```text
metadata/contributors.yml
```

## Collaboration

The protocol is open to technically reviewed contributions that improve:

- mathematical accuracy;
- correspondence with the JJM source code;
- input-file documentation;
- installation procedures;
- model diagnostics;
- case-study reproducibility;
- interpretation of outputs;
- training materials.

Proposed changes should be submitted through issues and pull requests.

## Data and confidentiality policy

The repository may contain:

- protocol source files;
- bibliography;
- mathematical figures;
- approved model diagrams;
- public case-study data;
- public model inputs;
- reproducible scripts;
- compiled protocol documents;
- version metadata.

It must not contain:

- restricted fishery data;
- confidential assessment inputs;
- personal credentials;
- access tokens;
- unpublished institutional results;
- sensitive operational information.

## Disclaimer

This protocol is intended as technical guidance.

It does not replace:

- the authoritative SPRFMO JJM source code;
- official SPRFMO technical documentation;
- formal stock-assessment review;
- institutional assessment procedures;
- approved management advice.

Users are responsible for verifying the model version, input files, convergence, diagnostics, and interpretation before applying results.

## Maintainers

This repository is developed and maintained by the Dirección de Investigaciones del Subsistema Pelágico, Instituto del Mar del Perú — DIPEL-IMARPE.

Repository responsibilities and review roles should be defined in:

```text
.github/CODEOWNERS
```

## Institutional use

The protocol, source files, figures, scripts, and derived documents are subject to the institutional software, authorship, data, confidentiality, and publication policies of IMARPE.
