# Website technology batch audit for n8n

A manual workflow for the [Data Lantern Website Technology Detector](https://apify.com/datalantern/tech-stack-detector). It turns a small URL batch and saved results into a report and downloadable CSV.

Disclosure: Data Lantern maintains the linked paid Actor.

## Start with the fictional demo

1. Download `workflow.json` from this directory.
2. Import it into an n8n instance you control.
3. Run **Manual start** with the defaults unchanged.
4. Open **Download audit CSV** to download the file.

The default demo uses fictional `.example` addresses. It makes no HTTP requests and requires no credential. The workflow is inactive, with no schedule or webhook.

## Live use is optional and paid

Read the Actor's [current pricing](https://apify.com/datalantern/tech-stack-detector/pricing) first. In your own n8n instance, create an HTTP Header Auth credential: `Authorization: Bearer <your own Apify token>`. Select it on the three HTTP Request nodes. Never put a token in the workflow JSON.

Edit the values in **Configure batch**: use 1–20 public canonical HTTP(S) hostname URLs, set `mode` to `live`, and set `allowPaidRun` to `true` only when approving a new run. The default per-run Actor charge cap is $0.05. n8n hosting and other platform usage are separate.

If a start response is lost or the run is still active, inspect Apify Runs. To retrieve later, keep the original URLs, set `existingRunId`, and leave `allowPaidRun: false`. This uses GET requests, without a new Actor start.

## Limits and verification

The report separates successful, temporary-failure, needs-review and unobserved targets. Retry suggestions never execute automatically. There is no automatic polling, restart or persistent monitoring.

URLs with query strings, fragments, credentials, IP literals or nonstandard ports are rejected. No JavaScript browser execution or reverse technology-to-domain search is provided. Review diagnostics and incomplete results.

The original workflow passed five synthetic scenarios in native n8n 2.43.8 on 20 October 2026. The 30 October export refresh passed 11 offline tests, including literal-comma URL preservation. The refreshed file has not been rerun in native n8n or against the live paid Actor. No compatibility with every n8n version is promised.
