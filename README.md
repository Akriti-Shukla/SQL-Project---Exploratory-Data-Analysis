# 📊 Exploratory Data Analysis (EDA) with SQL – Project

This project focuses on performing **Exploratory Data Analysis (EDA)** to derive meaningful insights from a dataset. 
The key tasks involve leveraging SQL techniques to gain a deeper understanding of the data.

## Key Tasks:
- 🔢 **Window Functions**: Rank countries based on specific metrics, providing valuable insights into the data.
- 🧩 **Common Table Expressions (CTEs)**: Simplify complex queries for improved readability and maintainability.
  
## Resources:
- Detailed EDA processes
- SQL queries for real-world analysis scenarios

  ## Sample of a SQL Query used in the project

  - Analyzing companies in order of maximum layoffs per year

```sql
WITH Company_Year (company, years, total_laid_off) AS
(
SELECT company, YEAR(`date`), SUM(total_laid_off)
FROM layoffs_staging2
GROUP BY company, YEAR(`date`)
), Company_Year_Rank AS
 (SELECT *, 
DENSE_RANK() OVER(PARTITION BY years ORDER BY total_laid_off DESC) AS Ranking
FROM Company_Year
WHERE years IS NOT NULL
)
SELECT *
FROM Company_Year_Rank
WHERE Ranking <=5;
```


This project serves as an example of using advanced SQL functions to clean, analyze, and interpret data effectively for business decision-making.
