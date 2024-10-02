# Dataset Information

## -> Presidential General Averages

### **Data Source**
The data was extracted from the [FiveThirtyEight 2024 Presidential General Polls Project](https://projects.fivethirtyeight.com/polls/president-general/2024/national/).

The most recent version can be downloaded in the "More on the polls - Download the data" section under the **Presidential general election polling averages**.

### **Collection Date**
The data was collected on **September 27, 2024**.

### **Data Format**
The data is in **CSV** format (`presidential_general_averages.csv`).

### **Usage License**
The data is provided under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**, allowing for reuse with proper attribution to the source.

## Description of Variables or Attributes

| Variable/Attribute   | Description |
| -------------------- | ----------- |
| `candidate`          | Name of the presidential candidate. |
| `date`               | Date on which the polling data was recorded. |
| `pct_trend_adjusted` | Percentage of support for the candidate, adjusted to account for polling trends and other biases. |
| `state`              | U.S. state for which the polling data is relevant to.|
| `cycle`              | Election cycle year (e.g., 2024). |
| `party`              | The political party presumably associated with the candidate (Nan values given). |
| `pct_estimate`       | Estimated percentage of support for the candidate based on the poll. |
| `hi`                 | Upper bound of the estimated percentage. |
| `lo`                 | Lower bound of the estimated percentage. |


## -> Google Trends Data (Last 90 Days)

### **Data Source**
There are 2 files with content on this topic. The data was downloaded from [Google Trends](https://trends.google.es/trends/) with corresponding comparison searches on the names that appear in the variables of each file.

### **Collection Date**
The data was collected on **September 27, 2024**.

### **Data Format**
The data is in **CSV** format (`google_trends_last_90_days_full_names.csv`, `google_trends_last_90_days_surnames.csv` ).

### **Usage License**
Please refer to the [Google Trends Terms of Service](https://policies.google.com/terms) for specific usage rights and restrictions regarding the data.

## Description of Variables or Attributes

`google_trends_last_90_days_full_names.csv` file:

| Variable/Attribute                   | Description |
| ------------------------------------ | ----------- |
| `Día`                                | Date of data collection (YYYY-MM-DD format). |
| `Kamala Harris: (Estados Unidos)`    | Google Trends interest score for "Kamala Harris" in the United States on the given date. |
| `Joe Biden: (Estados Unidos)`        | Google Trends interest score for "Joe Biden" in the United States on the given date. |
| `Donald Trump: (Estados Unidos)`     | Google Trends interest score for "Donald Trump" in the United States on the given date. |

`google_trends_last_90_days_surnames.csv` file:

| Variable/Attribute                   | Description |
| ------------------------------------ | ----------- |
| `Día`                                | Date of data collection (YYYY-MM-DD format). |
| `Harris: (Estados Unidos)`    | Google Trends interest score for "Harris" in the United States on the given date. |
| `Biden: (Estados Unidos)`        | Google Trends interest score for "Biden" in the United States on the given date. |
| `Trump: (Estados Unidos)`     | Google Trends interest score for "Trump" in the United States on the given date. |


The values represent interest over time, with higher values indicating more search interest relative to the other data points. A value of `<1` indicates very low interest, less than 1 on the normalized scale.

