This is a dataset of Stack Overflow data related to the tag 'design'. Our goal for this was to create a design training dataset for identifying design issues in software discussions. The fundamental assumption is that the act of tagging a question (and its associated answers) as 'design' reflects discussions about software design, i.e., it is similar to having this community labeling discussions as either related to design or not. 

- `sotorrent_design_answers.csv` contains tags (1-4) plus 26,989 text answers with those tags, one of which will be `design`.
- `sotorrent_design_questions.csv` contains tags (1-4) plus 9436 text questions with those tags, one of which will be `design`.
- `sotorrent_qa_design` is the join of SO answers, and their associated questions. Thus the questions are repeated for each answer in the data. Other fields include the SO Ids (links) for each, tags, type of response (q/a), question Title, accepted answer ID, and scores for each. 
- `questions-only.txt` is a newline separated, double-quote delimited list of design-tagged questions. This is good for loading text as a way of training embeddings. 
- `answers-only.txt` is as a newline separated, double-quote delimited list of design-tagged answers.
- `combined.txt` is questions-only.txt plus 25000 random stack overflow questions, not tagged design, rated over 0.

Note the body of the questions has newlines, commas, and other potential flaws for loading the CSV. 

This dataset was created from the SOTorrent dump from Google Bigquery, of Dec 2018. In total there are 26,989 entries (answers and associated questions). The only selection/filtering on BigQuery was "tag = design" and "score > 0" (i.e., no offtopic or poor questions, and most unanswered questions/unimportant questions are omitted). But see the paper "Promises and Perils of Mining StackOverflow" for more discussion of this topic. Wait, no one has written this paper yet? 

Once we obtained those records (around 36k), we endeavoured to remove entries whose tags indicated they focused on graphical design:

"winforms"          "css"               "wpf"               "cocoa"             "cocoa-touch"       "xaml"              "animation"        "qt"  "twitter-bootstrap" "material" "html" "image" "user-interface" "layout" "wpf" "qt" "xaml"

There are likely still more answers about graphical design present, but css etc seemed to remove about 1/6 of the total questions.  

The Bigquery query is available if interested.

Thanks to Sebastian Baltes and his colleagues for the original dataset:

> Sebastian Baltes, Lorik Dumani, Christoph Treude, and Stephan Diehl. 2018. "SOTorrent: Reconstructing and Analyzing the Evolution of Stack Overflow" Posts. Proceedings of the 15th International Conference on Mining Software Repositories (MSR 2018).
