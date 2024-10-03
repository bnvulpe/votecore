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

## -> Reddit posts

### **Data Source**
The data was extracted using the tool [Artic Shift](https://github.com/ArthurHeitmann/arctic_shift) as since last year, reddit's official API doesn't support searching on concrete time intervals.

### **Collection Date**
The data was collected on **September 27, 2024**, so data ranges from 2024-06-01 to 2024-09-27.

### **Data Format**
The data is in **JSON** format (`r_(subreddit)_posts.json`).

### **Usage License**
Not relevant.

## Description of Variables or Attributes

| Variable/Attribute   | Description |
| -------------------- | ----------- |
| `subreddit`          | Name of the subreddit. |
| `subreddit_id`       | Id of the subreddit. |
| `id`                 | Id of the post. |
| `name`               | Id of the posts used to link with comments. |
| `author`             | Username of the author. |
| `created`            | Originally named `created_utc`, represents the timestamp of creation. |
| `datetime`           | Datetime (YYYY-MM-DD hh:mm:ss) of the creation of the comment. |
| `score`              | Upvotes minus downvotes of the comment. |
| `ratio`              | Originally named `upvote_ratio`, represents the ratio between upvotes and downvotes of the posts, a value of 1.0 means no downvotes. |
| `title`              | Title of the post. |
| `body`               | Originally named `selftext`, represents the text content of the post. |
| `url`                | Url of the post. |

## Discarded Attributes from Original Data

Some fields found in the raw documents generated by Artic Shift were discarded, as they can be confusing and are not relevant to this task. Here's a list of all of them:

`banned_at_utc`, `archived`, `hide_score`, `ups`, `media_embed`, `distinguished`, `link_flair_text_color`, `no_follow`, `awarders`, `whitelist_status`, `can_mod_post`, `contest_mode`, `author_cakeday`, `secure_media`, `hidden`, `num_comments`, `content_categories`, `_meta`, `pwls`, `author_flair_text`, `subreddit_subscribers`, `removed_by`, `author_patreon_flair`, `link_flair_richtext`, `thumbnail_height`, `downs`, `top_awarded_type`, `link_flair_template_id`, `wls`, `category`, `view_count`, `author_fullname`, `removed_by_category`, `crosspost_parent`, `preview`, `quarantine`, `num_reports`, `send_replies`, `author_flair_css_class`, `num_crossposts`, `crosspost_parent_list`, `removal_reason`, `discussion_type`, `all_awardings`, `visited`, `author_flair_template_id`, `domain`, `user_reports`, `link_flair_type`, `approved_at_utc`, `is_video`, `pinned`, `treatment_tags`, `subreddit_type`, `total_awards_received`, `created`, `author_flair_background_color`, `gildings`, `thumbnail`, `banned_by`, `author_premium`, `gilded`, `author_flair_text_color`, `mod_reports`, `mod_reason_title`, `url_overridden_by_dest`, `is_self`, `media`, `author_flair_type`, `mod_reason_by`, `permalink`, `is_reddit_media_domain`, `suggested_sort`, `saved`, `allow_live_comments`, `stickied`, `is_created_from_ads_ui`, `retrieved_on`, `likes`, `is_meta`, `subreddit_name_prefixed`, `thumbnail_width`, `secure_media_embed`, `is_original_content`, `author_flair_richtext`, `link_flair_text`, `over_18`, `mod_note`, `link_flair_css_class`, `link_flair_background_color`, `can_gild`, `post_hint`, `media_only`, `spoiler`, `edited`, `clicked`, `approved_by`, `is_crosspostable`, `report_reasons`, `parent_whitelist_status`, `is_robot_indexable`, `locked`, `author_is_blocked`.

## -> Reddit comments

### **Data Source**
The data was extracted using the tool [Artic Shift](https://github.com/ArthurHeitmann/arctic_shift) as since last year, reddit's official API doesn't support searching on concrete time intervals.

### **Collection Date**
The data was collected on **September 27, 2024**, so data ranges from 2024-06-01 to 2024-09-27.

### **Data Format**
The data is in **JSON** format (`r_(subreddit)_comments(_month?).json`).

### **Usage License**
Not relevant.

## Description of Variables or Attributes

| Variable/Attribute   | Description |
| -------------------- | ----------- |
| `subreddit`          | Name of the subreddit. |
| `id`                 | Originally named `name`, represents the id of the comment. |
| `post_id`            | Originally named `link_id`, represents the id of the post. |
| `parent`             | Originally named `parent_id`, represents the id of the parent comment if the comment is a response. |
| `author`             | Username of the author. |
| `created`            | Originally named `created_utc`, represents the timestamp of creation. |
| `datetime`           | Datetime (YYYY-MM-DD hh:mm:ss) of the creation of the comment. |
| `score`              | Upvotes minus downvotes of the comment. |
| `upvotes`            | Originally named `ups`, represents the upvotes of the comment. |
| `body`               | Content of the comment. |

## Discarded Attributes from Original Data

Some fields found in the raw documents generated by Artic Shift were discarded, as they can be confusing and are not relevant to this task. Here's a list of all of them:

`subreddit_type`, `collapsed_reason_code`, `subreddit_name_prefixed`, `banned_at_utc`, `author_fullname`, `total_awards_received`, `collapsed_reason`, `archived`, `associated_award`, `is_submitter`, `treatment_tags`, `created`, `author_flair_background_color`, `author_flair_richtext`, `distinguished`, `gildings`, `replies`, `banned_by`, `no_follow`, `author_premium`, `awarders`, `collapsed`, `can_mod_post`, `num_reports`, `author_cakeday`, `gilded`, `send_replies`, `author_flair_css_class`, `mod_note`, `author_flair_text_color`, `collapsed_because_crowd_control`, `mod_reports`, `removal_reason`, `_meta`, `media_metadata`, `mod_reason_title`, `all_awardings`, `controversiality`, `subreddit_id`, `author_flair_type`, `author_flair_text`, `mod_reason_by`, `can_gild`, `author_flair_template_id`, `permalink`, `unrepliable_reason`, `user_reports`, `expression_asset_data`, `comment_type`, `edited`, `approved_by`, `author_patreon_flair`, `score_hidden`, `saved`, `report_reasons`, `downs`, `stickied`, `approved_at_utc`, `top_awarded_type`, `editable`, `retrieved_on`, `locked`, `likes`, `id`, `author_is_blocked`.

