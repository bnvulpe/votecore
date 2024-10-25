# Dataset Information

## **Usage License**
Please refer to the [LICENSE](/LICENSE) file in the repository for more information.
## **Data Sources**

- **Presidential General Averages**  
  The data was sourced from the [FiveThirtyEight 2024 Presidential General Polls Project](https://projects.fivethirtyeight.com/polls/president-general/2024/national/). The most recent version is available for download in the “More on the polls - Download the data” section, under **Presidential general election polling averages**.

- **Google Trends Data (Last 90 Days)**  
  There are two files covering this topic. The data was obtained from [Google Trends](https://trends.google.es/trends/), with corresponding comparison searches based on the names appearing as variables in each file.

- **Reddit Posts and Comments**  
  The data was extracted using the tool [Arctic Shift](https://github.com/ArthurHeitmann/arctic_shift), as Reddit’s official API no longer supports time-specific searches since last year. We have data from the communities r/politics, r/progressive, r/conservative.

## **Collection Date**
The data was collected on **September 27, 2024**.

## **Dataset for Biden’s Presidential Candidacy**  

This dataset covers the period when Joe Biden was actively campaigning for the presidency. It includes polling averages, Google Trends data, and Reddit activity specifically filtered for this timeframe to capture public sentiment, interest trends, and online discussions relevant to the time frame and candidates.

| Variable/Attribute   | Description |
| -------------------- | ----------- |
| `date_day`           | Date on which the data reffers to. |
| `polls_Biden`        | Estimated percentage of voters in favor of Biden (average, normalized) based on the poll on the given date. |
| `polls_Trump`        | Estimated percentage of voters in favor of Trump (average, normalized) based on the poll on the given date. |
| `google_Trump`       | Google Trends interest (average, normalized) score for "Donald Trump" and "Trump" in the United States on the given date. |
| `google_Biden`       | Google Trends interest (average, normalized) score for "Joe Biden" and "Biden" in the United States on the given date. |
| `donald_trump_love`   | Model's love classification score average for Trump on the given date. |
| `donald_trump_hate`   | Model's hate classification score average for Trump on the given date. |
| `joe_biden_love`   | Model's love classification score average for Biden on the given date. |
| `joe_biden_hate`   | Model's hate classification score average for Biden on the given date. |

## **Dataset for Biden's Exit and Harris's Candidacy**  

This dataset encompasses the period following Joe Biden’s withdrawal from the presidential race and Kamala Harris’s subsequent candidacy. It includes updated polling averages, Google Trends data, and Reddit activity, capturing shifts in public sentiment, search trends, and online discussions.

| Variable/Attribute   | Description |
| -------------------- | ----------- |
| `date_day`           | Date on which the data reffers to. |
| `polls_Harris`       | Estimated percentage of voters in favor of Harris (average, normalized) based on the poll on the given date. |
| `polls_Trump`        | Estimated percentage of voters in favor of Trump (average, normalized) based on the poll on the given date. |
| `google_Trump`       | Google Trends interest (average, normalized) score for "Donald Trump" and "Trump" in the United States on the given date. |
| `google_Harris`      | Google Trends interest (average, normalized) score for "Kamala Harris" and "Harris" in the United States on the given date. |
| `donald_trump_love`   | Model's love classification score average for Trump on the given date. |
| `donald_trump_hate`   | Model's hate classification score average for Trump on the given date. |
| `kamala_harris_love`  | Model's love classification score average for Harris on the given date. |
| `kamala_harris_hate`  | Model's hate classification score average for Harris on the given date. |
