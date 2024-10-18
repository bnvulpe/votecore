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
  
In the end, we have a **JSON file** where each dictionary corresponds to a comment or post made on a specific day, and contains not only the information relevant to that comment/post, but also the corresponding poll data and Google interest scores for each candidate on the same day.

Initially, we planned to preserve the relationship between comments, parent comments, and posts, thinking it might be useful for text modeling (e.g., analyzing the context in which a comment appears). However, as we are now focusing on sentiment extraction towards each candidate from the **bodies + titles**, this relationship is no longer relevant. Consequently, we removed the columns **name, datetime, post_id, id**, and **parent** from the final dataset. This helps streamline the data for sentiment analysis and ensures we’re not carrying unnecessary information moving forward.