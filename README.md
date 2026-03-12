# CompliGUARD Knowledge Base

**Purpose:** Regulatory knowledge base for CompliGUARD AI compliance review system  
**Usage:** Fetched by n8n workflow nodes to provide grounded regulatory context to Claude compliance assessments  
**Maintained by:** CompliGUARD / ClickFlow Digital Marketing  
**Last updated:** March 2026

---

## Repository Structure

```
compliguard-knowledge-base/
├── README.md                          ← This file — index and routing guide
│
├── tga/
│   ├── tga_part1_preliminary_definitions.md
│   ├── tga_part3_general_requirements.md
│   ├── tga_part4_mandatory_statements.md
│   ├── tga_part5_particular_goods.md
│   ├── tga_part6_testimonials_part7_samples.md
│   ├── tga_part8_restricted_representations.md
│   └── tga_part9_price_information.md
│
├── ahpra/
│   ├── ahpra_part1_overview_false_misleading.md
│   └── ahpra_part2_gifts_testimonials_expectations.md
│
├── accc/
│   ├── accc_part1_misleading_health_reviews.md
│   └── accc_part2_pricing_comparative_credence.md
│
├── fsanz/
│   └── fsanz_standard_1_2_7_health_claims.md
│
└── fmi/
    └── fmi_food_medicine_interface_guidance_tool.md
```

---

## Routing Guide for n8n Code Node

Use this table to determine which files to fetch based on submission characteristics:

| Trigger Condition | Files to Fetch |
|---|---|
| **Always** (all reviews) | `tga/tga_part3_general_requirements.md` |
| **Always** (all reviews) | `accc/accc_part1_misleading_health_reviews.md` |
| Product has health claims | `tga/tga_part4_mandatory_statements.md` |
| Testimonials present | `tga/tga_part6_testimonials_part7_samples.md` |
| Complementary medicine / traditional use claims | `tga/tga_part5_particular_goods.md` |
| Analgesics | `tga/tga_part5_particular_goods.md` |
| Weight management claims | `tga/tga_part5_particular_goods.md` |
| Sunscreen claims | `tga/tga_part5_particular_goods.md` |
| Therapeutic claims (treat/cure/prevent disease) | `tga/tga_part8_restricted_representations.md` |
| Food or supplement product (not TGA registered) | `fsanz/fsanz_standard_1_2_7_health_claims.md` |
| Uncertain food vs medicine classification | `fmi/fmi_food_medicine_interface_guidance_tool.md` |
| Registered health practitioner involved | `ahpra/ahpra_part1_overview_false_misleading.md` |
| Practitioner advertising health service | `ahpra/ahpra_part2_gifts_testimonials_expectations.md` |
| Price comparisons in ad | `accc/accc_part2_pricing_comparative_credence.md` |
| "Before and after" imagery | `ahpra/ahpra_part2_gifts_testimonials_expectations.md` |
| Organic / natural / environmental claims | `accc/accc_part2_pricing_comparative_credence.md` |
| Price information list (pharmacy) | `tga/tga_part9_price_information.md` |

---

## Source Documents

| Chunk | Source | Version |
|---|---|---|
| TGA all parts | Therapeutic Goods (Therapeutic Goods Advertising Code) Instrument 2021 | Compilation No. 1, 20 December 2022 |
| AHPRA all parts | Guidelines for Advertising a Regulated Health Service | December 2020 |
| ACCC all parts | ACCC Advertising and Selling Guide | July 2021 |
| FSANZ | Australia New Zealand Food Standards Code — Standard 1.2.7 | Current as at March 2026 |
| FMI | TGA Food-Medicine Interface Guidance Tool | July 2014 (current) |

---

## Update Policy

When regulatory guidance is updated:
1. Update the relevant markdown file(s)
2. Commit with a message referencing the amendment (e.g., `TGA Code amendment F2022L01650`)
3. Git commit history provides the audit trail of which version was current at any point in time

This version control history supports CompliGUARD's audit trail obligations under the TGA's "reasonable steps" framework.

---

## n8n Fetch URL Pattern

```
https://raw.githubusercontent.com/[YOUR-ORG]/compliguard-knowledge-base/main/[FILE_PATH]
```

Example:
```
https://raw.githubusercontent.com/compliguard/knowledge-base/main/tga/tga_part3_general_requirements.md
```

For private repos, include `Authorization: Bearer [GITHUB_PAT]` header in the HTTP Request node.
