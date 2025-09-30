# omnichat-data-cleaner
Python/Colab pipeline for cleaning Omnichat contact data: normalize headers, standardize phones to E.164, parse BRL currency, coalesce heterogeneous column names, deduplicate by phone (keep latest), apply configurable low-potential filters, and export full audit XLSX + contacts CSV without losing original columns.
