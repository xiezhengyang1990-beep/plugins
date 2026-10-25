# Data Lantern: Apify API examples

Small input examples for two existing Data Lantern Actors. These files contain public API inputs and usage notes. They do not contain the Actors' implementation code, API keys or customer data.

## 1. Inventory the technologies used by a list of websites

[Website Technology Detector](https://apify.com/datalantern/tech-stack-detector) returns website-level technology signals such as CMS, ecommerce platform, CDN, frameworks and analytics.

Use [tech-stack-input.json](./tech-stack-input.json) as a small starting input. It lists three public websites and caps successful website results at three. The example disables linked-script content scanning for a lighter first run. This can miss technologies found only inside those scripts.

- [Public API documentation](https://documenter.getpostman.com/view/59106431/2sBYHUSfLx)
- [Existing Apify example](https://apify.com/datalantern/tech-stack-detector/examples/compare-website-tech-stacks)

The Actor reads public HTML, headers and other exposed signals. It does not run a full JavaScript browser. Empty detections do not prove a technology is absent. Keep the original URL, error/status fields and analysis warnings when importing results into an inventory.

## 2. Extract traceable text from public PDF URLs

[PDF Text Extractor](https://apify.com/datalantern/pdf-text-extractor) reads the text layer from publicly accessible PDFs that you have the right to process.

Use [pdf-input.json](./pdf-input.json) as a starting input. It requests one record per document, the first 20 pages at most, and a 10 MB file-size limit. The complete file still has to fit the size limit.

- [Public API documentation](https://documenter.getpostman.com/view/59106431/2sBYHUSfLz)
- [Existing Apify example](https://apify.com/datalantern/pdf-text-extractor/examples/extract-public-pdf-text-for-rag)

This Actor does not perform OCR, create embeddings, answer questions or reliably reconstruct tables. A scanned document needs another tool. Preserve the source URL and extraction status before sending text to a separate search or RAG system.

## Before you start a run

Both Actors use paid, usage-based Apify pricing. Read the current prices on their Store pages and set a maximum charge in the run options before starting. Viewing these files or the documentation does not start an Actor run.

Paste an input JSON into the Actor's JSON input editor, review it, then choose whether to start it in your own Apify account. For programmatic execution, use the linked API documentation and your own securely stored Apify token. Never paste a real token into a public file, issue, screenshot or chat.

For a larger batch, use an asynchronous run and save its run ID. If an HTTP connection times out, inspect the existing run before issuing another start request. A lost response does not prove the original run stopped. Download the complete dataset and review failures before retrying selected items.

## Scope and feedback

Published by Data Lantern, the maker of the linked Actors. These are starting inputs, not a promise that every target website or PDF can be read. Source restrictions and document layout can affect results.

Use each Actor's existing Issues tab for product-specific feedback. This example folder does not provide customer support for unrelated plugins in the parent repository.
