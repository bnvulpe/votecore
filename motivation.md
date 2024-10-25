### Motivation Overview

- **General Objective of the Project:**  
  The primary goal of this project is to analyze the sentiment towards political candidates by combining various datasets, including social media interactions, polling data, and Google Trends. By integrating these data sources, we aim to better understand public opinion and trends over a specific period leading up to an election. The analysis will focus on uncovering sentiment patterns, fluctuations in candidate support, and possible correlations between public discourse and polling/interest data.

- **Research Questions or Hypotheses:**  

  The hypothesis of this study is twofold: First, the support values extracted from Reddit comments and posts for each candidate are expected to show a statistically positive correlation (correlation > 0) with the corresponding poll results from the same timeframe. This suggests that as public sentiment on Reddit improves or worsens for a candidate, their polling numbers will follow a similar trend. Second, the frequency of mentions of each candidate in political discussions on Reddit is hypothesized to positively correlate with Google Trends search volume for the same candidate. This indicates that as candidates receive more attention and mentions in Reddit forums, public interest, as reflected by Google search activity, will increase proportionally. These hypotheses aim to demonstrate how online discourse and sentiment can provide insights into broader public opinion and interest. 

  The study is limited to the U.S. public, focusing specifically on the behaviors of predominantly U.S.-based users on Reddit and Google Trends.

  Here are some research questions that we intend on answering to support the project's objectives and validate the hypothesis:

  1. **What is the correlation between support values from Reddit posts/comments and polling results for each candidate over the same time period?**
    - This question helps directly address the first part of the hypothesis, measuring how closely online support reflects polling trends.

  2. **Do changes in Reddit support values for each candidate precede or follow changes in poll results?**
    - This explores the temporal dynamics of the correlation, determining whether online support predicts poll outcomes or reflects them after they happen.

  3. **How does the frequency of mentions of each candidate on Reddit political forums correlate with the Google Trends search volume over the same time period?**
    - This would test the second part of the hypothesis, focusing on whether public discussions align with search trends.

  4. **How does the number of mentions of a candidate in Reddit posts/comments vary in relation to key campaign events, and how does this compare to spikes in Google search activity?**
    - This examines whether certain events lead to parallel increases in mentions and searches, suggesting synchronized spikes in public interest.

  5. **Do incidents like the assassination attempt, Biden's retirement from politics and arrival of Kamala Harris to the presidential race directly affect support and poll results?**
    - This question assesses whether these significant events lead to noticeable improvements or declines in support and polling trends, highlighting their immediate impact on public opinion.

- **Justification of the Selected Data:**  

  The datasets selected for this project—social media comments and posts, polling data, and Google Trends—are ideal for addressing the research questions because they provide a multi-faceted view of public sentiment. Social media data offers real-time reactions and discussions from the general public, while polling data gives insight into formalized public opinion at regular intervals. Google Trends data reflects spontaneous interest in candidates, which might be linked to specific events or moments of heightened attention. Together, these sources offer complementary perspectives on public opinion.

- **Potential Challenges with the Cleaned Data:**  

  1. **Data Bias:** Social media data, especially from platforms like Reddit, may not be representative of the broader population, as it often reflects the opinions of more vocal or politically active users.

  2. **Insufficient Coverage:** Certain time periods or candidates may have limited data available, particularly in less-discussed regions or during quieter periods of the campaign, leading to incomplete coverage.

  3. **Data Gaps:** There may be missing or incomplete data points for some days in both polling and Google Trends datasets, which could affect the accuracy of longitudinal analyses.

  4. **Support Analysis Accuracy:** The complexity of political discourse and the presence of sarcasm or ambiguous language may present challenges in accurately capturing supportive or critical sentiment from social media posts.