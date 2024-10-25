# Data Cleaning Process

## Steps for Cleaning:

### 1. **Google Trends Data**

- **Merging Files**: Both `.csv` files from Google Trends (containing interest scores of candidates by full name and surname) were merged based on the date to consolidate the information.
- **Replacing Minimal Interest Scores**: Interest values below 1 were replaced with 0 to ensure consistency in the dataset. This allows us to work exclusively with numerical data that can be easily visualized and processed as numerical values, avoiding complications that could arise from handling non-numeric or very low values.

- **Combining Mentions**: For each candidate, data from both name variations (full name and surname) were averaged to create a single interest score per day.

**Justification**: 
- The minimal data provided by Google Trends required merging and consolidation to avoid redundancy.
- Averaging the values from different mentions of candidates provided a more comprehensive interest score, while low values (<1) were not considered impactful enough to include.

---

### 2. **Polling Data**

- **Time Filter**: Data before the study period (01-06-2024 to 27-09-2024) was removed to ensure relevance.
- **Candidate Filtering**: Only the three main candidates were retained, excluding others like Kennedy.
- **State-Level Poll Averages**: Poll estimates across different states were averaged, providing a single percentage per candidate each day. With this final step we are left with 3 single columns `date`, `candidate` and `pct_estimate`.

**Justification**: 
- Focusing on the main candidates allowed us to align the data with the research hypothesis. 
- Averaging the state-level poll data helped create a more manageable dataset and prevented certain regions from being overrepresented. This step was important because other data sources used in the study, such as Reddit interactions, are not representative of individual states but instead capture a broader, highly concentrated view of opinions from politically engaged users across the country. By balancing the polling data, we ensure a fair comparison with these online interactions, which tend to reflect the perspectives of political enthusiasts rather than a geographically diverse sample.
---

### 3. **Reddit Comments and Posts**

- **Filtering by Candidate Mention**: Only comments or posts mentioning the main candidates were kept, as others are irrelevant for this analysis.
- **Removing Unnecessary Columns**: Columns like `author`, `is_valid`, `created`, `subreddit_id`, `id` and `url` were dropped, as they don't contribute to the sentiment or content analysis.
- **Datetime Conversion**: `created` was converted to just the date (day), to align with the time indexing used in other datasets.
- **Cleaning Text**: Links and URLs were removed from the `body` of posts and comments, as they add no value to the analysis.

**Justification**:
- Focusing only on content mentioning the main candidates ensures relevance.
- Text and datetime cleaning standardizes the format and prevents noise (e.g., unnecessary links), facilitating downstream text processing.

---

### 4. **Joining All Data into a Final File**

After cleaning the individual datasets, the next step is to consolidate all the information into a single dataset. Here’s how the process unfolds:

- We added a new column, named **"type"**, to both the posts and comments DataFrames, assigning the value "post" for posts and "comment" for comments. This differentiation will help later in distinguishing between the two types of data.
- Both DataFrames were then converted into lists of dictionaries using the `to_dict(orient="records")` method. These lists were merged into a single list, called **json_data**.
- From the **polls** DataFrame, we extracted the unique candidate names, while from the **Google** DataFrame, we focused on specific column names related to candidate interest.
- The next step involved iterating over each document in **json_data** and matching the **date_day** field with the **date** field in both the polls and Google DataFrames. For each candidate, we retrieved the corresponding poll and Google values and added them to the document. If no matching data was found for that day, we assigned the value **None** to the field.
- Once all the data was added to the documents, decided to convert the **json_data** list into a DataFrame. For this task, we decided to remove the columns **type**, **upvotes**, **score** and **ratio** from the final dataset, as they were not relevant for the support analysis.

**Justification**:
- The final dataset combines all relevant information for the making it ready for the next steps of analysis. The removal of all score collumns is justified by the fact that we are focusing on the support values extraction from the bodies and titles of the comments and posts.

---

### 5. **Support Analysis**

Once the data is cleaned and consolidated, the next step is to perform support analysis. This involves extracting sentiment towards each candidate from the bodies and titles of the comments and posts. The sentiment analysis will be conducted using a zero-shot classifier to determine the most appropiate slogan for each candidate on each post or comment.

- **Zero-Shot Classification**: A zero-shot classifier, [facebook/bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli), will be used to determine the support values towards each candidate in the comments and posts. This approach allows us to classify the sentiment without the need for pre-defined categories and , making it more flexible and adaptable to the nuances of political discourse.

- **Category Assignment**: Given we are focusing on candidates, for each comment or post, the classifier will assign if the text refers to a suppotive or critical sentiment towards each candidate. This will be done for the both the body and the title of the comment or post. The use of slogans instead of pure sentiment is justified by the fact that the model was not explicitly trained for sentiment analysis, so classifiation by slogans is a more robust approach.

- **No mention case**: In the case where a comment or post does not mention any candidate, the support value will be assigned as **None**, indicating that no sentiment towards any candidate was expressed.
  
**Justification**:
- Give the lack of Entity Level Sentiment Analysis models, the zero-shot classification approach is the best option to determine the sentiment towards each candidate in the comments and posts.
- The assignment of **None** for the case where no candidate is mentioned is important to avoid false positives in the support analysis.

---

### 6. **Normalization and Aggregation**

After extracting the support values, the next step is to normalize and aggregate the data to facilitate the analysis. This involves:

- **Aggregating Support Values**: The support values for each candidate will be aggregated daily to provide a comprehensive view of the sentiment trends over time. For each day, the mean support value for each candidate will be calculated based on the comments and posts mentioning them, hereby creating a daily support score for each candidate. Note that **None** values will be excluded from the aggregation automatically by pandas.

- **Normalization**: The google trends data will be normalized to ensure that all datasets are on the same scale. This will involve scaling the interest scores to a range of 0-1, allowing for direct comparison with the support values. Also, the poll data will be normalized to the same range to ensure consistency across all datasets.

- **Aggregating Poll and Google Data**: The poll and Google data will be aggregated daily to align with the support values. This will involve averaging the poll estimates and interest scores for each candidate to create a single value per day.

**Justification**:
- Aggregating the support values and normalizing the data will provide a consistent basis for comparison and analysis. This step is crucial for identifying trends and correlations between different datasets.