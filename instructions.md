Exercise 2: Exploratory Data Analysis with Visualization Techniques
Aim

To perform Exploratory Data Analysis (EDA) on a dataset using visualization techniques to identify patterns, trends, and relationships between variables.

Description

Exploratory Data Analysis (EDA) is an important step in data science used to understand the structure and characteristics of a dataset before applying machine learning models.

In this experiment, a social media dataset is analyzed. The dataset contains information about different platforms, number of users, daily active users (DAU), and engagement rates.

Using statistical summaries and visualization techniques, insights are derived regarding:

Distribution of users
Relationship between DAU and engagement
Correlation between variables
Comparison of engagement rates across platforms
Dataset

The dataset includes the following attributes:

Platform
Users (in millions)
Daily Active Users (in millions)
Engagement Rate (%)
Program
# Step 1: Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Step 2: Create dataset
data = {
    "Platform": ["Facebook","Instagram","Twitter","LinkedIn","Youtube"],
    "Users (in millions)": [2555,2600,1005,1500,700],
    "Daily Active Users (in millions)": [3000,450,650,668,654],
    "Enagagement Rate (%)":[35,42,34,65,34]
}

df = pd.DataFrame(data)

# Step 3: Display basic statistics
print(df.describe())

# Step 4: Histogram
plt.figure(figsize=(8,6))
plt.hist(df["Users (in millions)"], bins=5, edgecolor='black')
plt.title("Distribution of Users on Social Media Platforms")
plt.xlabel("Users (in millions)")
plt.ylabel("Frequency")
plt.show()

# Step 5: Scatter Plot
plt.figure(figsize=(8,6))
sns.scatterplot(
    x="Daily Active Users (in millions)",
    y="Enagagement Rate (%)",
    hue="Platform",
    data=df,
    s=100
)
plt.title("Daily Active Users vs Engagement Rate")
plt.xlabel("Daily Active Users (in millions)")
plt.ylabel("Engagement Rate (%)")
plt.show()

# Step 6: Correlation Heatmap
plt.figure(figsize=(8,6))
corr = df[["Users (in millions)", "Daily Active Users (in millions)", "Enagagement Rate (%)"]].corr()
sns.heatmap(corr, annot=True)
plt.title("Correlation Heatmap")
plt.show()

# Step 7: Box Plot
plt.figure(figsize=(8,6))
sns.boxplot(
    x="Platform",
    y="Enagagement Rate (%)",
    data=df
)
plt.title("Engagement Rate by Platform")
plt.xlabel("Platform")
plt.ylabel("Engagement Rate (%)")
plt.xticks(rotation=45)
plt.show()
Output Explanation
Histogram shows how user counts are distributed across platforms.
Scatter Plot shows relationship between daily active users and engagement rate.
Heatmap shows correlation between Users, DAU, and Engagement Rate.
Box Plot compares engagement rate distribution among platforms.
Result

Exploratory Data Analysis was successfully performed using various visualization techniques. The analysis helped in understanding:

Distribution of users across platforms
Relationship between daily active users and engagement
Correlations among variables
Differences in engagement rates across platforms
