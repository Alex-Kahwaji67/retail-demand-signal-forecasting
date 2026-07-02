# Data Notes

Raw API exports and intermediate data are intentionally not committed.

The project uses:

- FRED / US Census Bureau state-level food and beverage store sales data.
- Google Trends weekly search interest by state, collected through `pytrends`.
- NewsAPI headlines and descriptions for selected retail keywords.

To reproduce the project, generate local files such as:

```text
data/raw/fred_sales.csv
data/raw/google_trends_raw.csv
data/raw/news_sentiment_raw.csv
data/processed/google_trends_monthly.csv
data/processed/merged_trends_sales.csv
data/processed/sentiment_summary.csv
```

These files should remain local unless API terms and redistribution permissions are reviewed.

No API keys should ever be committed. Use environment variables such as `FRED_API_KEY` and `NEWS_API_KEY`.
