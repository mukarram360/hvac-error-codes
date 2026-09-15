---
license: cc-by-4.0
language:
  - en
pretty_name: HVAC Bench Error Code Dataset
size_categories:
  - n<1K
task_categories:
  - question-answering
  - text-classification
tags:
  - hvac
  - error-codes
  - heat-pump
  - mini-split
  - boiler
  - diagnostics
configs:
  - config_name: default
    data_files: hvac-error-codes.csv
---

# HVAC Bench Error Code Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22698961.svg)](https://doi.org/10.5281/zenodo.22698961)

Error codes from HVAC equipment sold in the United States, United Kingdom, and Europe, as published by HVAC Bench. Each record gives the manufacturer, the code, the product family the definition applies to, a plain-language meaning, the checks an owner can safely make, the point at which a technician is needed, and the date the definition was last checked against manufacturer documentation. Codes are specific to a product family and are not interchangeable between brands.

- **Publisher:** [HVAC Bench](https://hvac-bench.com/)
- **Creator:** Mukarram Haroon, HVAC Bench
- **Dataset page:** [HVAC Bench Error Code Dataset](https://hvac-bench.com/data/hvac-error-codes/)
- **Error code library:** [HVAC Error Codes by Manufacturer](https://hvac-bench.com/error-codes/)
- **DOI:** [10.5281/zenodo.22698961](https://doi.org/10.5281/zenodo.22698961), the concept DOI for all versions, which always resolves to the latest deposited version. Version 1.1.0 is [10.5281/zenodo.22763965](https://doi.org/10.5281/zenodo.22763965); version 1.0.0 is archived as [10.5281/zenodo.22698962](https://doi.org/10.5281/zenodo.22698962).
- **Version:** 1.1.0 (updated 2026-09-15)
- **Licence:** [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
- **Records:** 161 codes across 50 manufacturers and 9 equipment types

## Read this before using a code

An HVAC error code is defined by the manufacturer for a specific product family. The same code can mean different things on two brands, and on two generations of the same brand. Every record states the product family its definition was documented for in `product_family` and `scope_note`. Do not apply a record outside that scope, and do not merge records from different brands into one universal list.

The `owner_safe_checks` column lists only checks that need no tools and no access to live electrical parts, refrigerant, or combustion components. Everything else belongs in `call_a_technician_when`.

## Files

| File | Format |
| --- | --- |
| `hvac-error-codes.csv` | CSV, UTF-8, RFC 4180, header row |
| `hvac-error-codes.json` | JSON with dataset metadata and a `records` array |

The same data is served live at `https://hvac-bench.com/api/v1/error-codes/` with cross-origin access allowed.

The canonical copy is the [dataset page on HVAC Bench](https://hvac-bench.com/data/hvac-error-codes/). Identical copies are published on:

- [GitHub](https://github.com/mukarram360/hvac-error-codes)
- [Zenodo](https://doi.org/10.5281/zenodo.22698961)
- [Kaggle](https://www.kaggle.com/datasets/mukarramharoon/hvac-error-codes-by-hvac-bench)
- [Hugging Face](https://huggingface.co/datasets/mukarram360/hvac-error-codes)

## Columns

| Column | Description |
| --- | --- |
| `id` | Stable record identifier, taken from the reference page address. |
| `brand` | Manufacturer name as it appears on the equipment. |
| `brand_slug` | Lowercase manufacturer key, stable across versions. |
| `error_code` | The code as the display or controller shows it. |
| `equipment_type` | Equipment category, such as ductless-mini-split or boiler. |
| `product_family` | The product family the definition was documented for. A code is only valid inside this scope. |
| `models` | Models or series named in the documentation, separated by semicolons. |
| `fault_category` | What kind of fault the code reports, such as communication-fault. |
| `title` | Headline of the HVAC Bench reference page. |
| `meaning` | Plain-language definition of what the control detected. |
| `scope_note` | Limits on where the definition applies, when the documentation states them. |
| `owner_safe_checks` | Checks an owner can make without opening the equipment, separated by a vertical bar. |
| `call_a_technician_when` | Conditions and work that need a qualified technician, separated by a vertical bar. |
| `reset_guidance` | What the documentation permits for a reset, when it says. |
| `evidence_class` | Class of primary documentation behind the definition. |
| `evidence_publishers` | Publishers of that documentation, separated by semicolons. |
| `last_reviewed` | Date the definition was last checked against its source (ISO 8601). |
| `reference_url` | The full HVAC Bench reference page for this code. |

## Coverage by manufacturer

| Manufacturer | Records |
| --- | --- |
| Daikin | 11 |
| Mitsubishi Electric | 9 |
| Carrier | 8 |
| Goodman | 8 |
| Gree | 6 |
| LG | 6 |
| York | 6 |
| MRCOOL | 5 |
| Vaillant | 5 |
| Baxi | 4 |
| Ideal Heating | 4 |
| Lennox | 4 |
| Midea | 4 |
| Panasonic | 4 |
| Pioneer | 4 |
| Rheem | 4 |
| Senville | 4 |
| Ariston | 3 |
| Bosch | 3 |
| Della | 3 |
| Google Nest | 3 |
| Haier | 3 |
| Hitachi | 3 |
| Klimaire | 3 |
| Samsung | 3 |
| tado | 3 |
| Trane | 3 |
| Worcester Bosch | 3 |
| Amana | 2 |
| American Standard | 2 |
| Blueridge | 2 |
| Cooper & Hunter | 2 |
| Daikin Altherma | 2 |
| Hisense | 2 |
| NIBE | 2 |
| Ruud | 2 |
| Toshiba | 2 |
| Viessmann | 2 |
| Bryant | 1 |
| Drayton | 1 |
| ecobee | 1 |
| Friedrich | 1 |
| Fujitsu General | 1 |
| GE Appliances | 1 |
| Grant | 1 |
| Hive | 1 |
| Honeywell Home | 1 |
| Mitsubishi Heavy Industries | 1 |
| Stiebel Eltron | 1 |
| TCL | 1 |

## How the records are made

Each record is taken from a published HVAC Bench reference page that has been checked against the manufacturer's own documentation: a service manual, an installation or operation manual, or an official support article. Definitions are paraphrased rather than copied, and the class and publisher of the documentation are recorded in `evidence_class` and `evidence_publishers`. The full reasoning, diagnostic branches, and safety limits for each code are on the page in `reference_url`.

## Embeddable lookup

A free lookup widget reads this dataset:

```html
<div data-hvac-bench-lookup>
  <a href="https://hvac-bench.com/error-codes/">HVAC error codes from HVAC Bench</a>
</div>
<script src="https://hvac-bench.com/embed/error-code-lookup.js" async></script>
```

## Attribution

Under CC BY 4.0 you may share and adapt the data for any purpose, including commercially, provided you give credit. Please attribute as:

> HVAC Bench Error Code Dataset by HVAC Bench (<https://hvac-bench.com/>), CC BY 4.0

## Citation

```bibtex
@misc{hvacbench_error_codes,
  title     = {HVAC Bench Error Code Dataset},
  author    = {Haroon, Mukarram},
  publisher = {HVAC Bench},
  year      = {2026},
  version   = {1.1.0},
  doi       = {10.5281/zenodo.22698961},
  url       = {https://hvac-bench.com/data/hvac-error-codes/}
}
```

## Corrections

Report an error through https://hvac-bench.com/contact/. Corrections that change a definition are logged at https://hvac-bench.com/corrections/.
