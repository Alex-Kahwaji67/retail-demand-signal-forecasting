# Retail Demand Signal Forecasting

## Summary

This project examines whether public digital signals can act as early indicators of food and beverage retail demand. It combines Google Trends search interest, VADER-scored news sentiment, and FRED / US Census Bureau state-level food and beverage store sales to test whether search activity precedes changes in sales.

The central result from the submitted report is that 133 out of 490 keyword-state pairs, or 27.1%, showed Google Trends search activity leading retail sales by up to three months.

## Data

The analysis used three public or API-accessible sources:

- FRED / US Census Bureau state-level food and beverage store sales.
- Google Trends weekly search interest for retail product keywords across U.S. states.
- NewsAPI headlines and descriptions for selected keywords.

The project covered 49 states after filtering to states with sufficient FRED data. Google Trends data was collected weekly and aggregated to monthly frequency to align with the FRED series.

## Methods

Google Trends data was cleaned with forward filling, normalized within state and keyword, and aggregated from weekly to monthly observations. Sales and trends data were merged by month and state.

News headlines and descriptions were scored with VADER sentiment. These scores were used both as a text analytics output and as an adjustment to search interest:

```text
Composite Demand Signal = Average Normalized Trend Interest * (1 + Sentiment Score)
```

The project also used TF-IDF and cosine similarity to compare keyword media coverage, co-occurrence lift analysis to search for keyword associations, cross-correlation to identify lead-lag relationships, and 36-month regression slopes to estimate keyword momentum by state.

## Results

The report found that 27.1% of keyword-state pairs showed search interest leading retail sales by up to three months. This supports the idea that digital search behavior can act as an early-warning signal in selected product categories and regions, while also showing that the relationship is not universal.

Composite demand signal rankings from the report:

| Rank | Keyword | Trend Score | Sentiment | Composite |
|---:|---|---:|---:|---:|
| 1 | Cold brew coffee | 0.366 | 0.577 | 0.5772 |
| 2 | Energy drink | 0.364 | 0.417 | 0.5161 |
| 3 | Protein drink | 0.338 | 0.368 | 0.4983 |
| 4 | Gluten-free snack |  |  | 0.4830 |
| 5 | Electrolyte drink |  |  | 0.4733 |

The strongest business insight is regional: a national inventory strategy can miss local demand shifts. The report identifies electrolyte drinks as particularly strong in the Southeast, protein products as strong on the West Coast, and selected keyword-state combinations as promising early signals.

## Business Use

Retail category managers could use this framework as an early-warning layer alongside POS forecasting. A weekly dashboard could flag keyword-state pairs whose search momentum and sentiment cross a threshold, helping teams decide where to pilot stock increases, plan regional assortment changes, or monitor emerging product categories.

## Limitations

The analysis identifies leading associations, not proof of causality. FRED sales data is monthly and category-level, so it may miss shorter trend cycles or item-level demand changes. Google Trends is a relative index, and NewsAPI coverage may vary by query and date range. The framework should be treated as a demand-sensing signal, not a standalone forecasting system.
