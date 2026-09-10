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

Error codes from HVAC equipment sold in the United States, United Kingdom, and Europe, as published by HVAC Bench. Each record gives the manufacturer, the code, the product family the definition applies to, a plain-language meaning, the checks an owner can safely make, the point at which a technician is needed, and the date the definition was last checked against manufacturer documentation. Codes are specific to a product family and are not interchangeable between brands.

- **Publisher:** [HVAC Bench](https://hvac-bench.com)
- **Creator:** Mukarram Haroon, HVAC Bench
- **Dataset page:** https://hvac-bench.com/data/hvac-error-codes/
- **Version:** 1.0.0 (updated 2026-09-11)
- **Licence:** [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
- **Records:** 87 codes across 38 manufacturers and 9 equipment types

## Read this before using a code

An HVAC error code is defined by the manufacturer for a specific product family. The same code can mean different things on two brands, and on two generations of the same brand. Every record states the product family its definition was documented for in `product_family` and `scope_note`. Do not apply a record outside that scope, and do not merge records from different brands into one universal list.

The `owner_safe_checks` column lists only checks that need no tools and no access to live electrical parts, refrigerant, or combustion components. Everything else belongs in `call_a_technician_when`.

## Files

| File | Format |
| --- | --- |
| `hvac-error-codes.csv` | CSV, UTF-8, RFC 4180, header row |
| `hvac-error-codes.json` | JSON with dataset metadata and a `records` array |

The same data is served live at `https://hvac-bench.com/api/v1/error-codes/` with cross-origin access allowed.

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
| Daikin | 5 |
| Goodman | 5 |
| Gree | 4 |
| Mitsubishi Electric | 4 |
| MRCOOL | 4 |
| York | 4 |
| Carrier | 3 |
| Ideal Heating | 3 |
| Lennox | 3 |
| LG | 3 |
| Panasonic | 3 |
| Pioneer | 3 |
| Rheem | 3 |
| Senville | 3 |
| Vaillant | 3 |
| Ariston | 2 |
| Baxi | 2 |
| Bosch | 2 |
| Della | 2 |
| Google Nest | 2 |
| Haier | 2 |
| Hitachi | 2 |
| Klimaire | 2 |
| Midea | 2 |
| tado | 2 |
| Worcester Bosch | 2 |
| Amana | 1 |
| American Standard | 1 |
| Blueridge | 1 |
| Cooper & Hunter | 1 |
| Daikin Altherma | 1 |
| Hisense | 1 |
| NIBE | 1 |
| Ruud | 1 |
| Samsung | 1 |
| Toshiba | 1 |
| Trane | 1 |
| Viessmann | 1 |

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

> HVAC Bench Error Code Dataset by HVAC Bench (https://hvac-bench.com), CC-BY-4.0

## Citation

```bibtex
@misc{hvacbench_error_codes,
  title     = {HVAC Bench Error Code Dataset},
  author    = {Haroon, Mukarram},
  publisher = {HVAC Bench},
  year      = {2026},
  version   = {1.0.0},
  url       = {https://hvac-bench.com/data/hvac-error-codes/}
}
```

## Corrections

Report an error through https://hvac-bench.com/contact/. Corrections that change a definition are logged at https://hvac-bench.com/corrections/.
