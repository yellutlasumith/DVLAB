Exercise 2: Exploratory Data Analysis with Visualization Techniques

Aim
To perform exploratory data analysis (EDA) on a given dataset by applying various visualization
methods to uncover insights, patterns, and relationships between variables.

Description
Exploratory Data Analysis (EDA) is a crucial step in data science. It helps in understanding the
dataset’s structure, distribution, and relationships between variables before applying predictive
models.
In this experiment, we analyze a social media dataset containing user counts, daily active users,
and engagement rates. Using statistical summaries and visualizations, we uncover trends and
correlations that highlight platform performance and user behavior.
The following visualization methods are applied:
 Histogram – to study the distribution of user counts.
 Scatter Plot – to examine the relationship between daily active users and engagement
rate.
 Correlation Heatmap – to visualize correlations between Users, DAU, and Engagement
Rate.
 Box Plot – to compare engagement rate distributions across platforms.
These methods collectively provide insights into platform performance, user engagement, and
variable relationships.

List of Tasks
1. Load the dataset into a Pandas DataFrame.

import pandas as pd 
data = { 
    "Platform": ["Facebook","Instagram","Twitter","LinkedIn","Youtube"], 
    "Users (in millions)": [2555,2600,1005,1500,700], 
    "Daily Active Users (in millions)": [3000,450,650,668,654], 
    "Enagagement Rate (%)":[35,42,34,65,34]     
} 
df=pd.DataFrame(data)

2. Generate basic statistics using describe().
df.describe()

3. Plot a Histogram to show distribution of users.
import matplotlib.pyplot as plt 
plt.figure(figsize=(8,6))
plt.hist(df["Users (in millions)"], bins = 5,color="skyblue",edgecolor='black')
plt.title("Distribution of users on Social Media Platform - 7097")
plt.xlabel("Users (in millions)")
plt.ylabel("Frequency")
plt.show()

4. Create a Scatter Plot to visualize Daily Active Users vs Engagement Rate.
import matplotlib.pyplot as plt 
import seaborn as sns 
 
plt.figure(figsize=(8, 6)) 
sns.scatterplot( 
    x="Daily Active Users (in millions)", 
    y="Enagagement Rate (%)", 
    hue='Platform', 
    data=df, 
    s=100 
) 
 
plt.title('Daily Active Users vs Engagement Rate - 7097') 
plt.xlabel('Daily Active Users (in millions)') 
plt.ylabel('Engagement Rate (%)') 
plt.legend(title='Platform') 
plt.show()

5. Generate a Correlation Heatmap to analyze
plt.figure(figsize=(8,6)) 
corr=df[["Users (in millions)","Daily Active Users (in millions)","Enagagement Rate (%)"]].corr() 
sns.heatmap(corr, annot=True,cmap='coolwarm') 
plt.title('Correlatiom Heatmap - 7097') 
plt.show()

6. Draw a Box Plot to compare engagement rates across platforms.
plt.figure(figsize=(8,6))
sns.boxplot(
    x="Platform",
    y="Enagagement Rate (%)",
    data=df,
    hue="Platform",
    palette="Set2",
    legend=False
)
plt.title('Engagement Rate by Platform - 7097')
plt.xlabel('Platform')
plt.ylabel('Enagagement Rate (%)')
plt.xticks(rotation=45)
plt.show()

Result:
Exploratory data analysis was successfully performed using multiple visualizations, revealing key
patterns, relationships, and insights among the variables in the dataset.
