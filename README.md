This is a dataset of Stack Overflow data related to the tag 'design'. My goal for this was to create a design training dataset for identifying design issues in software discussions.

- `sotorrent_design_answers.csv` contains tags (1-4) plus 26,989 text answers with those tags, one of which will be `design`.
- `sotorrent_design_questions.csv` contains tags (1-4) plus 9436 text questions with those tags, one of which will be `design`.
- `sotorrent_qa_design` is the join of SO answers, and their associated questions. Thus the questions are repeated for each answer in the data. Other fields include the SO Ids (links) for each, tags, type of response (q/a), question Title, accepted answer ID, and scores for each. 

This dataset was created from the SOTorrent dump from Google Bigquery, of Dec 2018. In total there are 26,989 entries (answers and associated questions). The only selection/filtering on BigQuery was "tag = design". Once I obtained those records (around 36k), I endeavoured to remove entries whose tags indicated they focused on graphical design:

"winforms"          "css"               "wpf"               "cocoa"             "cocoa-touch"       "xaml"              "animation"        "qt"  "twitter-bootstrap" "material" "html" "image" "user-interface" "layout" "wpf" "qt" "xaml"

There are likely still more answers about graphical design present, but css etc seemed to remove about 1/6 of the total questions.  

My Bigquery query is available if interested.

Thanks to Sebastian Baltes and his colleagues for the original dataset:

> Sebastian Baltes, Lorik Dumani, Christoph Treude, and Stephan Diehl. 2018. "SOTorrent: Reconstructing and Analyzing the Evolution of Stack Overflow" Posts. Proceedings of the 15th International Conference on Mining Software Repositories (MSR 2018).