# Data 101: advertising data API

Fictional monthly advertising spend for 6 stores (Store A to Store F), January to December 2025. Made for the Data Analytics Club Data 101 workshop. These are not real companies or figures.

## Endpoints

| Data | URL |
|---|---|
| All stores (JSON) | `https://raw.githubusercontent.com/franciellessantos/data101-advertising-api/main/advertising.json` |
| All stores (CSV) | `https://raw.githubusercontent.com/franciellessantos/data101-advertising-api/main/advertising.csv` |
| One store (JSON) | `https://raw.githubusercontent.com/franciellessantos/data101-advertising-api/main/stores/Store_A.json` (Store_A to Store_F) |

Each record: `store`, `month` (YYYY-MM), `ad_spend_usd`.

## Python

```python
import requests
import pandas as pd

url = "https://raw.githubusercontent.com/franciellessantos/data101-advertising-api/main/advertising.json"
response = requests.get(url, timeout=10)
response.raise_for_status()

ads = pd.DataFrame(response.json())
print(ads.groupby("store")["ad_spend_usd"].sum())
```

Or read the CSV directly:

```python
import pandas as pd
ads = pd.read_csv("https://raw.githubusercontent.com/franciellessantos/data101-advertising-api/main/advertising.csv")
```
