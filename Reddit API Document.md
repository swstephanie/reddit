# Documentation on Reddit API
## _PRAW_

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://praw.readthedocs.io/en/stable/getting_started/quick_start.html)
PRAW, the Python Reddit API Wrapper. This document only covers the methods and attributes related to our web scrapping. (There are some functions and methods in PRAW that are related to submit comments and interact with the users on Reddit. They are not included.)


### Subreddit
- Methods
`top(limit)` : top submissions  
`hot(limit)` : hot submissions  
`new(limit)` : new submissions  
`comments(limit)` : return the most recent comments in the subreddit  
`emoji()` : discover all emoji for a subreddit  
`post_requirements()` : get the post requirements for a subreddit.  
`rules()` : Use this attribute for interacting with a subreddit’s rules. It can be used to list all the rules for a subreddit  
`search(query: str, sort: str = 'relevance', syntax: str = 'lucene', time_filter: str = 'all')` : time_filter can be one of all, day, hour, month, week, year (default: all).  



- Attributes
    ```sh
    subreddit = reddit.subreddit("redditdev")
    subreddit.description
    ```
For example, we can get all the following attributes of the "redditdev" subreddit.
| Attribute | Description |
| --- | --- |
| `can_assign_link_flair` | Whether users can assign their own link flair. |
| `can_assign_user_flair` | Whether users can assign their own user flair. |
| `created_utc` | Time the subreddit was created, represented in [Unix Time](https://en.wikipedia.org/wiki/Unix_time). |
| `description` | Subreddit description, in Markdown. |
| `description_html` | Subreddit description, in HTML. |
| `display_name` | Name of the subreddit. |
| `id` | ID of the subreddit. |
| `name` | Fullname of the subreddit. |
| `over18` | Whether the subreddit is NSFW. |
| `public_description` | Description of the subreddit, shown in searches and on the “You must be invited to visit this community” page (if applicable). |
| `spoilers_enabled` | Whether the spoiler tag feature is enabled. |
| `subscribers` | Count of subscribers. |
| `user_is_banned` | Whether the authenticated user is banned. |
| `user_is_moderator` | Whether the authenticated user is a moderator. |
| `user_is_subscriber` | Whether the authenticated user is subscribed. |
### Submission
Submission refers to each post in the subreddit
 - Attributes
    ```sh
    subreddit = reddit.subreddit("redditdev")
    subreddit.description
    ```
| Attribute | Description |
| --- | --- |
| `author` | Provides an instance of [`Redditor`](redditor.html#praw.models.Redditor "praw.models.Redditor"). |
| `clicked` | Whether or not the submission has been clicked by the client. |
| `comments` | Provides an instance of [`CommentForest`](../other/commentforest.html#praw.models.comment_forest.CommentForest "praw.models.comment_forest.CommentForest"). |
| `created_utc` | Time the submission was created, represented in [Unix Time](https://en.wikipedia.org/wiki/Unix_time). |
| `distinguished` | Whether or not the submission is distinguished. |
| `edited` | Whether or not the submission has been edited. |
| `id` | ID of the submission. |
| `is_original_content` | Whether or not the submission has been set as original content. |
| `is_self` | Whether or not the submission is a selfpost (text-only). |
| `link_flair_template_id` | The link flair’s ID. |
| `link_flair_text` | The link flair’s text content, or None if not flaired. |
| `locked` | Whether or not the submission has been locked. |
| `name` | Fullname of the submission. |
| `num_comments` | The number of comments on the submission. |
| `over_18` | Whether or not the submission has been marked as NSFW. |
| `permalink` | A permalink for the submission. |
| `poll_data` | A [`PollData`](../other/poll.html#praw.models.reddit.poll.PollData "praw.models.reddit.poll.PollData") object representing the data of this submission, if it is a poll submission. |
| `saved` | Whether or not the submission is saved. |
| `score` | The number of upvotes for the submission. |
| `selftext` | The submissions’ selftext - an empty string if a link post. |
| `spoiler` | Whether or not the submission has been marked as a spoiler. |
| `stickied` | Whether or not the submission is stickied. |
| `subreddit` | Provides an instance of [`Subreddit`](subreddit.html#praw.models.Subreddit "praw.models.Subreddit"). |
| `title` | The title of the submission. |
| `upvote_ratio` | The percentage of upvotes from all votes on the submission. |
| `url` | The URL the submission links to, or the permalink if a selfpost |

 - Methods & Property
 `comments`: Provide an instance of CommentForest. This attribute can be used to obtain a flat list of comments, with any MoreComments removed. Sort order and comment limit can be set with the comment_sort and comment_limit attributes before comments are fetched, including any call to replace_more():
    ```sh
    submission.comments.replace_more(limit=0)
    comments = submission.comments.list()
    submission.comment_sort = "new"
    comments = submission.comments.list()
    ```

### Comment

  
| Attribute | Description |
| --- | --- |
| `author` | Provides an instance of [`Redditor`](redditor.html#praw.models.Redditor "praw.models.Redditor"). |
| `body` | The body of the comment, as Markdown. |
| `body_html` | The body of the comment, as HTML. |
| `created_utc` | Time the comment was created, represented in [Unix Time](https://en.wikipedia.org/wiki/Unix_time). |
| `distinguished` | Whether or not the comment is distinguished. |
| `edited` | Whether or not the comment has been edited. |
| `id` | The ID of the comment. |
| `is_submitter` | Whether or not the comment author is also the author of the submission. |
| `link_id` | The submission ID that the comment belongs to. |
| `parent_id` | The ID of the parent comment (prefixed with `t1_`). If it is a top-level comment, this returns the submission ID instead (prefixed with `t3_`). |
| `permalink` | A permalink for the comment. Comment objects from the inbox have a `context` attribute instead. |
| `replies` | Provides an instance of [`CommentForest`](../other/commentforest.html#praw.models.comment_forest.CommentForest "praw.models.comment_forest.CommentForest"). |
| `saved` | Whether or not the comment is saved. |
| `score` | The number of upvotes for the comment. |
| `stickied` | Whether or not the comment is stickied. |
| `submission` | Provides an instance of [`Submission`](submission.html#praw.models.Submission "praw.models.Submission"). The submission that the comment belongs to. |
| `subreddit` | Provides an instance of [`Subreddit`](subreddit.html#praw.models.Subreddit "praw.models.Subreddit"). The subreddit that the comment belongs to. |
| `subreddit_id` | The subreddit ID that the comment belongs to. |

- Methods and Propeties
`replies`: return the replies of a comment 


### Others
We can unique IDs to fetch each submission and each comments
```sh
submission = reddit.submission(id="5or86n")
comment = reddit.comment("dkk4qjd")
```


## _PushShift_

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://reddit-api.readthedocs.io/en/latest/)
The `pushshift.io` Reddit API was designed and created by the /r/datasets mod team to help provide enhanced functionality and search capabilities for searching Reddit comments and submissions.   

### Comment Search
- Time based Parameters (before, after, comment volume of the week or day)
- Content search 
    get the comments that mention "xxxx"   
    restrict to a specific author  
    restrict to a specific subreddit
### Submission Search
Similar to the comment search



### List of Endpoints

| Endpoint | Description | Status | 
| ------ | ------ | ------- |
| /reddit/search/comment/ | Search Reddit Comments | Active |
| /reddit/search/submission/ | Search Reddit Submissions | Active |
| /reddit/submission/comment_ids/{base36-submission-id} | Retrieve comment ids for a submission object | Active |
| /reddit/analyze/user/{author-name} | Analyze a Reddit user's activity | In Development |
| /reddit/term/frequency/{term} | Analyze a term based on activity |  In Development |
| /reddit/search/all/ | Search Both Comment and Submissions | In Development |
| /reddit/trending/people | Find out who is trending on Reddit | In Development |
| /reddit/search/links | Find relevent links being shared on Reddit | In Development |


