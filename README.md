# A-share Listed Companies Audit Risk Analysis

## 1. Project & Objective
This project connects WRDS financial database with Python, extracts 2024 annual financial statements of China A-share listed firms.
It builds a multi-dimensional financial audit risk assessment system, calculates core financial ratios, classifies enterprise risk levels, and uses statistical visualization to show financial risk distribution and correlation characteristics.

## 2. Data
- **Source**: WRDS CSMAR Financial Database (`csmar_financial.fs_combas`, `csmar_financial.fs_comins`)
- **Access Date**: April 23, 2026
- **Query**: SQL LEFT JOIN matches 2023 & 2024 annual report data of listed companies
- **Key Fields**: Stock code, Total assets, Total liabilities, Accounts receivable, Owner equity, Operating revenue, Net profit, Year-on-year revenue growth

## 3. Methods
### 3.1 Data Acquisition
Use Python `wrds` library to establish secure connection with WRDS cloud PostgreSQL database, execute structured SQL query to pull panel financial data.

### 3.2 Data Cleaning
- Delete invalid samples: firms with total assets ≤ 0, net assets ≤ 0
- Replace infinite abnormal values, drop rows with missing key indicators
- Standardize financial statement period & report type filtering

### 3.3 Financial Indicator Calculation
- Debt-to-Asset Ratio = Total Liabilities / Total Assets
- Accounts Receivable Ratio = Accounts Receivable / Total Assets
- ROE (Return on Equity) = Net Profit / Total Owner Equity
- Operating Revenue YoY Growth Rate

### 3.4 Risk Rating & Scoring
- Divide enterprises into 4 risk levels: Low Risk, Medium Risk, High Risk, Extreme Risk
- Build weighted comprehensive audit risk score (0-100 full score)

### 3.5 Statistical Visualization
1. Asset-liability ratio distribution histogram
2. Enterprise risk level proportion pie chart
3. Correlation scatter plot between receivable ratio and leverage ratio
4. ROE profitability distribution box plot
5. 2×2 integrated financial risk dashboard

## 4. Results
- Export full original dataset & simplified analysis CSV files locally
- Generate 300DPI high-definition risk analysis charts
- Complete hierarchical audit risk classification and comprehensive risk ranking of samples

## 5. Environment & Dependencies

Install all packages with command:

```bash
pip install -r requirements.txt
Package	Purpose	
pandas	Data frame cleaning & analysis	
numpy	Numerical operation & abnormal value processing	
matplotlib & seaborn	Statistical chart drawing	
wrds==3.4.0	WRDS database interface	
psycopg2-binary	PostgreSQL database driver	

```markdown


## 6. Operation Steps
1. Finish `.pgpass` password file configuration to realise WRDS auto-login
2. Run code cells in `notebook.ipynb` in order
3. Automatically complete data query, cleaning and indicator calculation
4. Export visualization pictures and structured result tables
5. Support offline analysis by reading local CSV files directly

## 7. Notes
- Valid WRDS academic account and stable overseas network are required for original data acquisition
- Matplotlib has been configured to support normal Chinese display
- You can freely adjust SQL screening conditions, risk grouping standards and indicator weight rules
- All file paths adopt relative paths, which are compatible with Windows and Mac systems
- Python 3.10-3.11 version is recommended to avoid wrds library compatibility errors