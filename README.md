# Predicting Myers-Briggs Personality Types from Social Media Posts

Capstone project I completed as a student in the Data Science Immersive program at General Assembly

This project uses natural language processing techniques to analyze text postings on a social forum, and predict the writers' Myers-Briggs personality type using a classification model. It also compares personality types based on other factors such as the length, polarity, and subjectivity of these posts.

#### Techniques/Models used:
- Natural Language Processing (NLP)
- Stopwords, PorterStemmer, TextBlob, CountVectorizer
- RandomForestClassifier, KNeighborsClassifier, OneVsRestClassifier, GridSearchCV, Tukey range test, t-test
- numpy, pandas, matplotlib, seaborn

#### Background:
Personality refers to individual differences in characteristic patterns of thinking, feeling and behaving. Personality typologies classify different types of individuals to reveal and enhance the understanding of their behaviors.

The *_Myers-Briggs Type Indicator (MBTI)_* is a psychological assessment tool to classify people into one of 16 different personality types. The classification system consists of a four-letter code based on four axes, where each letter in the code refers to the predominant trait in each axis. The four axes are:

- *_Introversion (I) – Extroversion (E)_*: Describes the different attitudes people use to direct their energy (i.e. the "inner world" vs. one's "outer world")
- *_Intuition (N) – Sensing (S)_*: Describes people's method of processing informaton (i.e. paying more attention to the patterns and possibilities seen in the information received vs. information that comes in through the five senses)
- *_Thinking (T) – Feeling (F)_*: Describes people's method for making decisions (i.e. putting more weight on objective principles and impersonal facts vs. personal concerns and the people involved)
- *_Judging (J) – Perceiving (P)_*: Describes people's orientation to the outside world and the behaviors one exhibits (i.e. preferring a structured and decided lifestyle vs. a more flexible and adaptive lifestyle)

For example, a person scoring higher on Introversion, Sensing, Thinking, and Judging would be classified with an ISTJ personality type.

#### Data source

The dataset was obtained on Kaggle (https://www.kaggle.com/datasnaek/mbti-type), and contains data from 8,675 subjects.

The original dataset consists of 2 columns:

- *_type_*: subjects’ known MBTI code (16 codes in total)
- *_posts_*: subjects’ 50 most recent posts on PersonalityCafe, an online forum focusing on personality types (http://personalitycafe.com/forum/). The site is geared toward the general public (not psychology professionals) with an interest in the topic of personality types

The dataset is skewed toward subjects from the Introverted-Intuitive personality types (INFJ, INFP, INTJ, and INTP). Also, personality types are self-reported by the users of this forum, and it is assumed that they are reported accurately.

#### Key findings

##### Multiclass classification
Three different classification models were tested: K-Neighbors Classifier, Random Forest Classifier, and One-Vs-The-Rest Classifier. The One-Vs-The-Rest Classifier, although having only the second-highest accuracy score of the three (0.265), cleared the 0.211 baseline and also predicted classes across the entire 16-class range -- unlike the top-scoring Random Forest Classifier.

##### Binary classification
A Random Forest Classifier was used to classify each of the four axis pairs. This model was chosen because it had the highest accuracy rate of the three models used in the multiclass exercise (although it had faltered in the predictions of the lower-prevalence classes). The model topped the baseline on only the Thinking-Feeling axis, with an accuracy of 0.697 (vs. a baseline of 0.541), but the models for the other three axes did not fall that far behind their respective baselines.

##### Sentiment Analysis and Word Count
On average, subjects used 26.4 words per post, with a neutral polarity (0.133) and moderate subjectivity (0.540). Those with one of the Intuitive-Feeling personality types tended to have higher post lengths than many of their counterparts, while the Extroversion-Intuitive-Feeling types tended to show significantly higher (but still relatively neutral) polarity and higher (but still relatively moderate) subjectivity than the other personality types.
