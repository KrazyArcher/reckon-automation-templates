# Zapier 3-Step Recipe: Google Sheets -> Reckon All-in-One Suite -> Gmail Draft
1. Trigger: `Google Sheets -> New Spreadsheet Row` (`Website`).
2. Action 1: `Apify -> Run Actor` -> Select `krazyarcher/reckon-all-in-one-suite` (Run Synchronously).
   Input: `{"urls":["{{Website}}"],"brandName":"Your Agency","onlyQualified":true,"generateReports":true,"generateGeoKit":true}`
3. Action 2: `Gmail -> Create Draft` -> To `{{email}}`, Subject `{{outreach_pitch.subject}}`, Body `{{outreach_pitch.body}}` + `Audit PDF: {{report_pdf_url}}` + `GEO llms.txt: {{geo_kit.llms_txt_url}}`.