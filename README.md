# Financial Metrics with SQL

**TripleTen Data Analyst Bootcamp project (2026)**

Analysis of 2017 revenue, costs, gross profit, profit margin and marketing campaign ROI across six key markets, using SQL on a relational sales database.

## 🎯 Business question

Which countries and product categories generate the most profit, and how efficiently does marketing spend turn into returns in each territory?

## 🗂️ Data

Relational database (PostgreSQL) with these tables:

| Table | Content |
| --- | --- |
| `ventas_2017` | Orders: order number, product, quantity and territory |
| `productos` | Products: name, subcategory, price and cost |
| `productos_categorias` | Product subcategories and categories |
| `territorios` | Territories: country and continent |
| `pais_ingreso_costo` | Revenue and costs aggregated by country |
| `pais_campanas` | Marketing campaign cost by territory |

## 🛠️ Process

1. **Data validation** ([01_data_validation.sql](sql/01_data_validation.sql)): checked nulls in key columns, quantities less than or equal to zero, and negative prices before running the analysis.
2. **Sales detail** ([02_sales_detail.sql](sql/02_sales_detail.sql)): joined sales with products, categories and territories, and calculated revenue and cost per order line. Used `COALESCE` to handle missing values.
3. **Country metrics** ([03_country_metrics.sql](sql/03_country_metrics.sql)): aggregated revenue, costs and campaign cost by country, and calculated gross profit, profit margin and campaign ROI. Used `NULLIF` to avoid division by zero.

## 📐 Metric definitions

- **Gross profit** = revenue − costs
- **Profit margin (%)** = gross profit / revenue × 100
- **Campaign ROI (%)** = gross profit / campaign cost × 100

## 📊 Results

| Country | Revenue | Costs | Campaign cost | Gross profit | Margin | ROI |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| United States | $3,353,940 | $1,899,471 | $1,920,000 | $1,454,469 | 43.4 % | 75.8 % |
| Australia | $2,532,003 | $1,474,958 | $2,150,400 | $1,057,045 | 41.8 % | 49.2 % |
| United Kingdom | $1,189,637 | $681,509 | $2,304,000 | $508,128 | 42.7 % | 22.1 % |
| Germany | $1,071,460 | $611,295 | $2,265,600 | $460,165 | 43.0 % | 20.3 % |
| France | $924,317 | $527,797 | $2,208,000 | $396,520 | 42.9 % | 18.0 % |
| Canada | $710,205 | $392,326 | $1,824,000 | $317,879 | 44.8 % | 17.4 % |

## 💡 Key findings

1. **The United States leads in volume and efficiency:** it generates the highest gross profit ($1.45M) and the highest campaign ROI (75.8 %), with a lower campaign cost than the UK, Germany or France.
2. **Margins are stable across markets:** profit margin stays between 41.8 % (Australia) and 44.8 % (Canada), so the differences in profitability come from sales volume and marketing spend, not from pricing or product costs.
3. **Low advertising efficiency in Europe and Canada:** despite spending more than $1.8M per market on campaigns, the UK, Germany, France and Canada return between 17.4 % and 22.1 %.

## ✅ Recommendations

- Reallocate marketing budget toward the United States and Australia, the markets with ROI above 49 %.
- Audit and restructure campaigns in the UK, Germany, France and Canada, adjusting targeting or reducing spend.

The full executive summary, including the Context → Finding → Implication analysis, is available in [executive_summary.xlsx](executive_summary.xlsx).

## 🧰 Skills demonstrated

SQL · PostgreSQL · `INNER JOIN` / `LEFT JOIN` · aggregations with `GROUP BY` · `CASE WHEN` · `COALESCE` · `NULLIF` · data validation · financial KPIs
