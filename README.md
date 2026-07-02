# Retail Demand Signal Forecasting

This project tests whether public digital signals can help retailers anticipate category demand before changes appear in conventional sales reporting.

The original coursework asked whether Google Trends search interest and news sentiment could serve as leading indicators for food and beverage retail demand. This staged portfolio version frames the project around state-level food and beverage retail sales from FRED / US Census data, combined with Google Trends and VADER-scored news sentiment.

## Problem

Convenience retailers often make inventory and assortment decisions from lagging point-of-sale data. That can miss early shifts in trend-sensitive categories such as cold brew, energy drinks, protein drinks, electrolyte drinks, and viral snack flavors.

This project asks:

- Can Google Trends search activity lead food and beverage retail sales?
- Can sentiment help separate genuine demand from controversy-driven search spikes?
- Which categories and regions show the strongest early-warning signals?

## Data Sources

- FRED / US Census Bureau: state-level food and beverage store sales series.
- Google Trends: weekly search interest by state, collected with `pytrends`.
- NewsAPI: keyword-related headlines/descriptions scored with VADER sentiment.

Raw data and API pulls are not included in this repository. See `data/README_DATA.md` for reproduction notes.

## Methods

- Monthly alignment of weekly Google Trends data with FRED sales series.
- Min-max normalization of trends within state/keyword.
- VADER sentiment scoring for news headlines and descriptions.
- TF-IDF and cosine similarity across keyword news corpora.
- Composite signal: average normalized trend interest multiplied by sentiment adjustment.
- Cross-correlation to test whether search interest leads sales by 1-3 months.
- 36-month momentum scoring by keyword/state.
- Regional divergence analysis to identify early rollout markets.

## Results

The project found that 133 out of 490 keyword-state pairs, or 27.1%, showed Google Trends search activity leading food and beverage retail sales by up to three months.

The strongest composite demand signals in the submitted report were:

| Rank | Keyword | Composite Score | Portfolio Interpretation |
|---:|---|---:|---|
| 1 | Cold brew coffee | 0.5772 | Highest combined trend and sentiment signal |
| 2 | Energy drink | 0.5161 | Strong incumbent category signal |
| 3 | Protein drink | 0.4983 | Strong functional beverage signal |
| 4 | Gluten-free snack | 0.4830 | Health-oriented snack opportunity |
| 5 | Electrolyte drink | 0.4733 | Regionally strong hydration signal |

The report also found meaningful regional signals: electrolyte drinks indexed strongly in the Southeast, protein products performed well on the West Coast, and specific keyword/state pairs showed positive momentum over the final 36 months.

## How To Reproduce

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Add API keys as environment variables:

```bash
FRED_API_KEY=your_fred_key
NEWS_API_KEY=your_newsapi_key
```

3. Run the notebook scaffold:

```text
notebooks/retail_demand_signal_forecasting.ipynb
```

The notebook is staged as a clean public scaffold. The original submitted notebook did not contain the full analysis pipeline, so the report currently serves as the verified source of results.

## Limitations

- FRED sales data is monthly, so shorter 2-3 week demand leads cannot be measured.
- Google Trends is relative, not absolute search volume.
- NewsAPI coverage depends on API plan, query windows, and article availability.
- The analysis identifies leading associations, not causal proof.
- Retail sales are category-level proxies, not item-level POS data.

## Portfolio Framing

This is best presented as a public-signal demand sensing project: a lightweight analytics framework that combines search behavior, text sentiment, and official retail sales data to identify early category demand signals.
