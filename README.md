# Catalog cleanup and Shopify CSV pilot — work sample

An independently checked delivery demonstration for a small, fixed-scope catalog cleanup service. All products and source URLs here are synthetic. This is not customer work, a sale, or evidence of a live Shopify import.

## What the pilot delivers

Given an authorized buyer CSV and agreed field mapping:

- Preserve exact SKU text, including leading zeroes.
- Produce a master table with one row per accepted SKU/model fitment.
- Produce one draft/unpublished Shopify CSV candidate per accepted SKU.
- Quarantine conflicting or invalid records rather than guessing or silently merging them.
- Report duplicates, missing data and image-rights declarations.
- Withhold image URLs without an allowed rights declaration.
- Reconcile every input record and include file-integrity hashes.

A pilot covers up to 100 distinct SKUs from one agreed CSV format. Fitment volume, mapping, price, schedule and acceptance are agreed before work begins. Scraping, paid data, image licensing, live-store access, production imports and ongoing refreshes are not included. Repeat processing can be scoped separately.

## Inspect the actual sample

- [Synthetic input](sample/input.csv) — deliberately contains invalid and formula-shaped test values. Do not open as a trusted spreadsheet.
- [Master output](sample/master.csv)
- [Draft Shopify candidate](sample/shopify.csv)
- [Issues ledger](sample/issues.csv)
- [Reconciliation and hashes](sample/summary.json)
- [Verification result](sample/verification.json)

The sample contains 100 distinct synthetic SKUs across 120 input records. Actual output: 105 accepted fitment rows, 94 draft products and 15 rejected records. Six SKUs were intentionally quarantined. There are 150 issue entries, including warnings; issue entries are not rejected-record counts.

The implementation passed 31 offline tests. A separate verifier performed 2,506 checks, including exact identifier preservation, hand-labelled expected rejections, output/source comparisons, rights flags and content hashes. The coordinator reran the tests, converter and verifier before publishing this sample. These checks are code/data verification, not a security certification or a guarantee of Shopify acceptance.

## Important limitations

Shopify output is a candidate format, not import-ready certification. A separately approved test import and buyer review are required. Images and source pages were not downloaded; rights are input declarations, not independent verification. Input observation timestamps are synthetic and carried through, not claimed collection dates.

CSV has no cell-type metadata: import SKU columns as text to preserve leading zeroes. Descriptive formula-shaped values are escaped and reported. The issues ledger encodes rejected SKU strings as JSON to preserve them without activating spreadsheet formulas. Draft data should not be blindly imported into a real store.

## Request a quote

Open a GitHub issue with the desired output, approximate SKU/fitment count and a description of your input format. Do not post private catalog data, credentials or customer information in a public issue. A private authorized sample, data handling terms, scope, quote and schedule must be agreed before a paid engagement starts.

This repository contains demonstration artifacts only; it does not grant a software license to the private converter. No prior-client experience or earned revenue is claimed.
