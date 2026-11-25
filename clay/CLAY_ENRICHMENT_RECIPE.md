# Clay HTTP API Recipe (Reckon All-in-One Suite)
- Method: `POST`
- Endpoint: `https://api.apify.com/v2/acts/krazyarcher~reckon-all-in-one-suite/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN`
- Body: `{"urls":["{{Website}}"],"brandName":"Your Agency","onlyQualified":true,"generateReports":true,"generateGeoKit":true}`
- Map Columns: `0.leak_tier`, `0.priority_score`, `0.email`, `0.cms`, `0.report_pdf_url`, `0.geo_kit.llms_txt_url`, `0.outreach_pitch.subject`, `0.outreach_pitch.body`