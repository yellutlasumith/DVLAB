📊 Experiment: Student Social Media Usage & Addiction Analysis
🎯 Aim

To analyze student social media usage and addiction data using appropriate data visualization techniques in order to identify behavioral patterns, academic impact, and health-related trends.

⚙️ Procedure
Import required libraries (Pandas, Matplotlib, Seaborn).
Load the dataset into a Pandas DataFrame.
Visualize platform usage using a Bar Chart.
Represent academic level distribution using a Pie Chart.
Analyze sleep patterns using a Histogram.
Study the relationship between usage and sleep using a Line Chart.
Examine correlation between sleep and mental health using a Scatter Plot.
Identify distribution and outliers in addiction scores using a Box Plot.
Visualize academic impact using a Pie Chart.
Compare platform usage by gender using a Stacked Bar Chart.
Explore relationships among multiple variables using a Pair Plot.
Analyze correlations using a Heatmap.
Interpret the results to identify trends and insights.

# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv("Students Social Media Addiction.csv")

# 1. Bar Chart – Platform Usage
plt.figure(figsize=(8,5))
sns.countplot(data=df, x="Most_Used_Platform")
plt.title("Number of Students by Most Used Social Media Platform")
plt.xticks(rotation=45)
plt.show()

# 2. Pie Chart – Academic Level
academic_counts = df["Academic_Level"].value_counts()
plt.figure(figsize=(4,4))
plt.pie(academic_counts, labels=academic_counts.index, autopct="%1.1f%%")
plt.title("Academic Level Distribution")
plt.show()

# 3. Histogram – Sleep Hours
plt.figure(figsize=(8,5))
plt.hist(df["Sleep_Hours_Per_Night"], bins=5)
plt.title("Distribution of Sleep Hours")
plt.show()

# 4. Line Chart – Usage vs Sleep
usage_sleep = df.sort_values("Avg_Daily_Usage_Hours")
plt.plot(usage_sleep["Avg_Daily_Usage_Hours"],
         usage_sleep["Sleep_Hours_Per_Night"])
plt.title("Usage vs Sleep")
plt.show()

# 5. Scatter Plot – Sleep vs Mental Health
sns.scatterplot(data=df,
                x="Sleep_Hours_Per_Night",
                y="Mental_Health_Score")
plt.title("Sleep vs Mental Health")
plt.show()

# 6. Box Plot – Addiction Score
sns.boxplot(y=df["Addicted_Score"])
plt.title("Addiction Score Distribution")
plt.show()

# 7. Pie Chart – Academic Impact
impact_counts = df["Affects_Academic_Performance"].value_counts()
plt.figure(figsize=(4,4))
plt.pie(impact_counts, labels=impact_counts.index, autopct="%1.1f%%")
plt.title("Academic Impact")
plt.show()

# 8. Stacked Bar Chart – Platform vs Gender
platform_gender = pd.crosstab(df["Most_Used_Platform"], df["Gender"])
platform_gender.plot(kind="bar", stacked=True)
plt.title("Platform Usage by Gender")
plt.show()

# 9. Pair Plot
sns.pairplot(df[[
    "Age",
    "Avg_Daily_Usage_Hours",
    "Sleep_Hours_Per_Night",
    "Mental_Health_Score",
    "Conflicts_Over_Social_Media",
    "Addicted_Score"
]])
plt.show()

# 10. Heatmap
plt.figure(figsize=(5,6))
corr = df.select_dtypes(include="number").corr()
sns.heatmap(corr, annot=True, cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()

✅ Result
The experiment was successfully performed using multiple data visualization techniques to analyze student social media usage and addiction data.
