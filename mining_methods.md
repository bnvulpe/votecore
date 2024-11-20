Description of Techniques Used: Detailed explanation of each data mining technique used.
Justification of Technique Selection: Why these techniques were chosen based on the objectives of the project and the nature of the data.
Algorithm Configuration: Parameters used, tools, and libraries applied.
# Mining techniques.

## Description

### Dynamic Topic Modeling

First of all, this technique is applied to our raw text data. Since the posts/comments are not evenly distributed on each day, and to avoid havin topics such variants, we have decide to group the posts/comments in two weeks period.\
The amount of data we have is huge and unbalanced, having weeks with more than 30K posts/comments and weeks with few hundreds. Furthermore, this technique is pretty slow, so in order to reduce the computation time (and to even the data) we have truncated the amount of posts/comments to 327, being this truncation completely random to preserve the variaty of such messages.
Afterwards, we processed the raw text substracting the stop words and applying lemmatization.

### Time Series Analysis

blblb

## Why these techniques?

### Dynamic Topic Modeling

Given the importance of a change in the presidential run, is quite relevant for our study to analyze the evolution of the topics during these months.

### Time Series Analysis

blblb

## Final configuration

### Dynamic Topic Modeling

Our final parameters were:
- Number of topics to look (num_topics) = 5
- Controlled variance over time (chain_variance) = 0.100

### Time Series Analysis

blblb