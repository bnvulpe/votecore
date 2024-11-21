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
   - **Objective**: To analyze the temporal trends in candidate support scores (Trump, Biden, Harris) based on sentiment. For **Trump vs. Biden**, we tested stationarity with the Dickey-Fuller test, analyzed ACF/PACF, and used **pmdarima** to find the best ARMA model for forecasting. We performed similar steps for **Trump vs. Harris**, detecting seasonality in Harris's support, which led to seasonal decomposition. We also analyzed the **differences** in support (Trump-Biden, Trump-Harris) using the same methods to understand how their relative support evolved over time.
   - **Outcome**: We assessed the predictability of the time series mentioned.
   - **Why Chosen**: Time series analysis allows us to track the evolution of candidate support over time and assess whether these trends can be predicted based on historical data. 

### 3. **Correlation with Polls, Google Trends and Sentiment**
   - **Objective**: To explore the correlation between Reddit sentiment trends and public opinion, using polling data and Google search interest as proxies.  
   - **Approach**: Utilizing the poll averages, sentiment scores, and Google Trends data that were gathered for the Trump-Biden and Trump-Harris timeframes, the following was done:
      - **Correlation Analysis**: Sentiment scores were treated as exogenous variables for both polling data and Google search interest. Using **pmdarima**, the best parameters for ARIMA models were identified, and the coefficients were calculated. Every possible combination of polling data or search interest with sentiment was analyzed:
         - **Trump-Biden Period**: 
            - Polls (Trump) with sentiment for Trump and Biden individually, and combined.
            - Polls (Biden) with sentiment for Trump, Biden, and their combination.
         - **Trump-Harris Period**: 
            - Polls (Trump) with sentiment for Trump and Harris individually, and combined.
            - Polls (Harris) with sentiment for Trump, Harris, and their combination.  
         - The same combinations were repeated for Google search interest data.  

   - **Outcome**: The analysis is aimed to identify patterns where changes in Reddit sentiment align with shifts in public opinion (polls) and search interest, validating or not the hypothesis that online discourse can predict broader political trends.  
   - **Why Chosen**: Polling data and Google Trends are well-established indicators of public opinion and interest. Correlating these with Reddit sentiment allows us to determine whether online discussions reflect or even anticipate public perception shifts. This strengthens the link between sentiment analysis and real-world trends, providing a richer understanding of the political discourse landscape.

