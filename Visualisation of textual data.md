👇

📊 Experiment: Text Preprocessing & Visualization Analysis
🎯 Aim

To use textual data to perform preprocessing techniques and analyze the processed data through appropriate visualization methods in order to gain meaningful insights.

⚙️ Procedure

Import required libraries (Pandas, NLTK, Matplotlib, WordCloud, TextBlob, Sklearn).
Load the dataset into a Pandas DataFrame.
Perform tokenization using NLTK.
Convert text into lowercase for uniformity.
Remove stopwords from the text.
Remove punctuation to clean the data.
Generate a Word Cloud to visualize frequent words.
Compute word frequencies and plot a bar chart.
Perform sentiment analysis and visualize using a pie chart.
Apply Topic Modeling (LDA) to extract hidden topics.
Interpret the results to identify key insights.

# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import nltk

# Load dataset
df = pd.read_csv("amazon_review.csv")

# Download tokenizer
nltk.download('punkt')
from nltk.tokenize import word_tokenize

# Tokenization
df['reviewText'] = df['reviewText'].fillna("")
df['tokens'] = df['reviewText'].apply(word_tokenize)

# Convert to lowercase
df['summary'] = df['summary'].astype(str).str.lower()
df['reviewText'] = df['reviewText'].astype(str).str.lower()

# Remove stopwords
from nltk.corpus import stopwords
stop_words = set(stopwords.words('english'))

def remove_stopwords(text):
    tokens = word_tokenize(str(text))
    filtered = [word for word in tokens if word not in stop_words]
    return " ".join(filtered)

df['reviewText_no_stop'] = df['reviewText'].apply(remove_stopwords)

# Remove punctuation
import string
punctuations = set(string.punctuation)

def remove_punctuation(text):
    tokens = word_tokenize(str(text))
    filtered = [word for word in tokens if word not in punctuations]
    return " ".join(filtered)

df['summary_clean'] = df['summary'].apply(remove_punctuation)

# WordCloud
from wordcloud import WordCloud
text = " ".join(df['summary'])
wordcloud = WordCloud(width=800, height=400, background_color='black').generate(text)

plt.imshow(wordcloud)
plt.axis("off")
plt.show()

# Word Frequency Bar Chart
from collections import Counter
words = " ".join(df['summary']).split()
word_freq = Counter(words)
top_words = dict(word_freq.most_common(20))

plt.bar(top_words.keys(), top_words.values())
plt.xticks(rotation=90)
plt.show()

# Sentiment Analysis
from textblob import TextBlob

def get_sentiment(text):
    polarity = TextBlob(text).sentiment.polarity
    if polarity > 0:
        return "Positive"
    elif polarity == 0:
        return "Neutral"
    else:
        return "Negative"

df['sentiment'] = df['summary'].apply(get_sentiment)

sentiment_counts = df['sentiment'].value_counts()
plt.pie(sentiment_counts, labels=sentiment_counts.index, autopct='%1.1f%%')
plt.show()

# Topic Modeling (LDA)
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.decomposition import LatentDirichletAllocation

vectorizer = CountVectorizer(max_df=0.9, min_df=5, stop_words='english')
doc_term_matrix = vectorizer.fit_transform(df['summary'])

lda = LatentDirichletAllocation(n_components=5, random_state=42)
lda.fit(doc_term_matrix)

words = vectorizer.get_feature_names_out()

for i, topic in enumerate(lda.components_):
    print(f"Topic {i+1}:")
    print([words[j] for j in topic.argsort()[-10:]])

✅ Result

The experiment was successfully executed by applying text preprocessing techniques and visualization methods on textual data.    
