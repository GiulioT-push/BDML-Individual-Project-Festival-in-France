# Festivals in France: Cultural Offer Decision Dashboard

BDML Individual Project: Data Visualization, Data Storytelling & Business Intelligence
Author: [YOUR NAME], student ID [20000]

## 1. Problem & Context

Festivals are a major driver of cultural life, tourism and local economies, but their distribution across France is uneven. This dashboard helps a decision-maker see **where festivals are concentrated, which disciplines dominate, when they take place, and which territories are under-served**.

## 2. Target User (Decision-Maker)

**A regional cultural / tourism development officer** (e.g. a regional cultural affairs department or a tourism board).

Decisions supported:
- Where to allocate cultural funding or support new festivals.
- Which disciplines are under-represented in a territory.
- How to spread the festival offer across the year (seasonality).
- How a department compares with the national average.

## 3. Business Questions

1. Which regions and departments concentrate the most festivals, and which are under-served relative to their population?
2. Which disciplines dominate, and how does the mix differ between territories?
3. When do festivals take place during the year (seasonality)?

*(Adapt these to the final columns of the dataset.)*

## 4. Dataset

| Item | Detail |
|---|---|
| Name | Liste des festivals en France |
| Publisher | Ministère de la Culture (Deps-doc / France festivals / Cepel, 2022) |
| Source | https://www.data.gouv.fr/datasets/liste-des-festivals-en-france |
| Licence | Licence Ouverte / Open Licence 2.0 |
| Format | CSV |
| Reference year | 2019 (festivals held in 2019 with at least 2 editions, more than one day, at least 5 shows) |
| Geolocation | Commune centroid (no postal address) |

Optional second dataset for benchmarking (population by department, INSEE): [ADD LINK IF USED]

The CSV is stored in `data/dataset.csv`. If it is missing, download it from the link above and place it in `data/`.

## 5. KPIs

| KPI | Definition | Management question |
|---|---|---|
| Total festivals | Count of festivals after filters | How large is the offer? |
| Festivals per 100,000 inhabitants | Festivals / population x 100,000 | Which territories are under-served? |
| Top region | Region with the most festivals | Where is the offer concentrated? |
| Top discipline share | % of festivals in the main discipline | Is the offer diverse? |
| Peak month | Month with the most festivals | When is the offer concentrated? |

*(Adjust to what the data allows and keep at least 5.)*

## 6. Dashboard Structure

1. **Executive Overview**: KPIs and headline numbers.
2. **Map & Territories**: map of festivals, ranking of regions/departments (Top N / Bottom N).
3. **Disciplines & Seasonality**: discipline mix, monthly distribution.
4. **Benchmark**: department vs national average (actual value, benchmark, difference, % difference).
5. **Data Explorer**: interactive table with CSV export.
6. **Decision Support / Recommendations**: 3 key insights, 2 recommendations, 1 limitation.

Filters: region, department, discipline, period/month.

## 7. Data Cleaning & Quality

Documented in `src/data_prep.py` (or in the app):
- Column names normalised, types converted.
- Missing values counted per column and handled explicitly.
- Duplicates checked and removed.
- Department code derived from the commune/postal code when needed.
- Outliers and inconsistent values reviewed.

Assumptions:
- Each row is one festival.
- The data is a 2019 snapshot, so no year-over-year comparison is possible.

## 8. Limitations

- Snapshot of 2019 only: **no evolution over time**, and the post-pandemic situation is not covered.
- Selection criteria exclude small or one-day events: the dataset is **not exhaustive**.
- Festivals are located at the commune centroid, so maps are approximate.
- Festival counts do not measure attendance, budget or quality.

## 9. Project Structure

```
.
├── app.py
├── requirements.txt
├── README.md
├── Videofile.mp4
├── data/
│   └── dataset.csv
└── src/
    └── data_prep.py
```

## 10. How to Run

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

`requirements.txt` (minimum):

```
streamlit
pandas
numpy
plotly
```

Data loading and cleaning use `st.cache_data` for performance.

## 11. Demo Video

`Videofile.mp4`: 2 to 4 minutes covering context, target user, dataset, KPIs, key interactions, main insight and recommendation.

## 12. Deployment

[Add Streamlit Community Cloud link if deployed]
