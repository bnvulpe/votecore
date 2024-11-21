# Description of Techniques Used

### 1. **Dynamic Topic Modeling (LdaSeqModel)**
   - **Objective**: To extract key themes and topics from Reddit comments related to candidates over time.
   - **Approach**: We used the **LdaSeqModel** from Gensim to model the topics in Reddit comments over biweekly periods (June-November), ensuring a uniform amount of data per period (approx. 400 comments per period). Each period's corpus was represented in a **Bag-of-Words (BoW)** format.
   - **Parameters**: 
     - `um_topics = 5`: This sets the number of topics for the model to uncover.
     - `chain_variance = 0.100`: Defines the sensitivity to topic evolution across periods.
   - **Outcome**: The model generated 5 topics per period, which were visualized to track how their relevance changed over time. The intensity of cells represents the prominence of each topic during specific time slices, allowing for the visualization of how topics evolve over time. The visualization highlights shifts in focus and can show time-dependent changes. By analyzing the key words associated with each topic, we gain context about its theme and how it changes in response to external factors, such as events or trends.
   - **Why Chosen**: This method was selected to capture latent themes in Reddit comments over time. As political events unfold, the public discourse on platforms like Reddit shifts accordingly. The **LdaSeqModel** is well-suited to model the evolution of topics over time, helping us track changes in public sentiment and interest.

### 2. **Time Series-Support Score Analysis**
   - **Objective**: To analyze the temporal trends in candidate support scores (Trump, Biden, Harris) based on sentiment. In the previous release, we analyzed time series of support scores for Trump, Biden, and Harris. For **Trump vs. Biden**, we tested stationarity with the Dickey-Fuller test, analyzed ACF/PACF, and used **pmdarima** to find the best ARMA model for forecasting. We performed similar steps for **Trump vs. Harris**, detecting seasonality in Harris's support, which led to seasonal decomposition. We also analyzed the **differences** in support (Trump-Biden, Trump-Harris) using the same methods to understand how their relative support evolved over time.
   - **Outcome**: We assessed the predictability of the time series mentioned.
   - **Why Chosen**: Time series analysis allows us to track the evolution of candidate support over time and assess whether these trends can be predicted based on historical data. **ARMA** models are particularly suited for analyzing stationary time series data, making them ideal for examining the predictability of candidate support scores.

### 3. **Correlation with Polls, Google Trends and Sentiemt**
   - **Objective**: To explore the correlation between sentiment trends on Reddit and public opinion through polling data and Google search interest.
   - **Approach**:
     - **Poll averages** and **Google Trends** data were collected for the Trump-Biden and Trump-Harris timeframes.
     - The data is currently under analysis, with plans to assess temporal correlations between sentiment shifts and external indicators.
   - **Expected Outcome**: We aim to identify patterns where shifts in Reddit sentiment correlate with changes in public opinion (polls) and search interest, further validating our hypotheses about online discourse predicting political trends.
   - **Why Chosen**: Polling data and Google Trends are widely used proxies for public opinion and interest. Correlating sentiment on Reddit with these external datasets allows us to assess whether online discussions reflect broader trends and public perception.

# Use of techiques for questions proposed

### 1. **Correlation between Reddit support values and polling results**
   - **What’s Done**: Sentiment analysis and the **time series analysis** of support scores for each candidate (Trump, Biden, Harris) has been performed.
   - **Remaining Work**: The correlation with polling data needs to be completed. Then the statistical significance of these correlations will be used to confirm whether changes in Reddit sentiment align with polling results.

### 2. **Do changes in Reddit support values precede or follow changes in poll results?**
   - **What’s Done**: Time series analysis (ARMA models) has been conducted on support scores, which will help detect trends and potential seasonality.
   - **Remaining Work**: **Granger causality testing** is needed to determine if Reddit sentiment precedes polling data.

### 3. **Support for a candidate in Reddit posts/comments and relation to campaign events and Google search activity**
   - **What’s Done**: Dynamic topic modeling (LdaSeqModel) has been performed to track Reddit discussions over time. Topic evolution analysis and the correlation with Google Trends are being explored.
   - **Remaining Work**: You need to explicitly correlate key **campaign events** (e.g., debates, major announcements) with the Reddit support scores and Google Trends data. You will also need to quantify how sentiment and search volumes change around those events.

### 4. **Impact of specific incidents (e.g., Biden’s retirement, Harris’s entry) on support and poll results**
   - **What’s Done**: Dynamic topic modeling can reveal shifts in Reddit discussions around key events. Time series analysis has been done on the support scores, which will capture any significant changes in sentiment.
   - **Remaining Work**: Analyzing the direct impact of specific events on **support scores** and **poll results** is still pending. This will involve linking major events with noticeable changes in sentiment and testing if these correspond to shifts in polling data.
