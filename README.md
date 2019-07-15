# Reddit Natural Language Processing
--------------
### Problem Statement
> 1. Is it possible to determine where a reddit post comes from based on the title and the post text? 
2. How much does the language of climate denial/skepticism differ from the language used by those who believe in climate change? 

### Data Dictionary 
| Column        | Data-Type | Description                                              |
|---------------|-----------|----------------------------------------------------------|
| post_text     | object    | the text contained within a specific subreddit post      |
| post_title    | object    | the title of a specific subreddit post                   |
| combined_text | object    | the combined text and title of a specific subreddit post |

### Executive Summary
In short, this project sought to create a classification model using natural language processing that could look at the text from a subreddit posts title and identify whether it came from /r/climatechange or /r/climateskeptics with as close to 100% accuracy as possible. I was able to create a logistical regression model that is able to predict subreddits with pretty good accuracy but it suffers from high variance. Here is a brief rundown of the steps I took to do this.
> 1. Using the Python requests library and the reddit API, I pulled and organized post data from the r/climatechange and r/climateskeptics.
2. After cleaning the data, I used natural language processing to tokenize and organize my textual data into computer readable results. I then used logistic regression to create a model. The resulting model had high accuracy also high variance.
3. I created a few more models using GridSearchCV and Pipelines to set up optimal hyperparameters and tokenize our texual data. The resulting models had low variance but were also less accurate. 

### Analysis
- My best model was actually one that I didn't use Hyper-Parameters on. I think I know why this happened though: in that model I used an edited stop list where I added in some key words that were widely used in both subreddits like 'climate and 'change'. Because those words were used so much, removing them likely allowed for the model to choose more impactful features. I also used a lemmatizer for my strings in model one, which also seems to have helped the model detect scores.
- A few more key takeaways: Hyperparameters matter. Despite my pipeline-gridsearch models being outperformed by my first model, they did have one advantage over it: They suffered from far less variance. In the future I'd like to figure out some ways to potentially add lemmatization and more customized stopwords sets as gridsearch hyperparameters. That would potentially allow for higher scoring models with low variance.
- If I could keep working on this in the future, I'd want to collect more data. With more text I believe I could further increase the model's accuracy. It would also be immensely helpful if I had more post text to work with rather then just titles. Alternatively, if I could set up an image recognition neural network, I think that could be another interesting way to use this data in the future (a lot of posts gathered had images instead of text).

