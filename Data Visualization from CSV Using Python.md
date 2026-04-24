# DVLAB
Aim

To create a Python script that reads data from a CSV file containing social media post metrics
and generates basic visualizations (bar chart, line chart, and pie chart) to analyze engagement
across platforms and post types effectively.

Description

This exercise demonstrates how to visualize data from a CSV file using Python. The dataset
contains information about social media posts, including platforms, post types, and engagement
metrics (likes, shares, comments, views). The script:
 Loads and cleans the data (handles missing values and invalid entries).
 Aggregates metrics (e.g., average likes and views by platform).
 Generates three visualizations:
o Bar chart: Compares average likes across platforms.
o Line chart: Shows trends in average views across platforms.
o Pie chart: Displays the percentage distribution of post types. These visualizations
help analyze engagement patterns and distribution in the dataset.

List of Tasks

1. Import necessary libraries (Pandas and Matplotlib).

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

2. Load the CSV file into a DataFrame.

df = pd.read_csv("social_media_data.csv")
df.head()

3. Preview the data to verify loading.

print("Dataset:(7097)")
print(df)

4. Clean the data by filling missing values (NaN) with 0.

df.fillna(0, inplace=True)

5. Filter out invalid platforms (keep only Twitter, Instagram, Facebook).
valid_platforms = ["Twitter", "Instagram", "Facebook"]
data = df[df["platform"].isin(valid_platforms)]

6. Aggregate average metrics (likes, shares, comments, views) by platform.

agg_data = data.groupby("platform").agg({
    "likes": "mean",
    "shares": "mean",
    "comments": "mean",
    "views": "mean"
}).reset_index()

print("\nAggregated Data:(7097)")
print(agg_data)

7. Create a bar chart for average likes by platform.

plt.figure(figsize=(10, 6))
plt.bar(
    agg_data['platform'],
    agg_data['likes'],
    color='black',
    edgecolor='red'
)

plt.title('Average Likes by Platform - 7097', fontsize=12, pad=15)
plt.xlabel('Platform', fontsize=12)
plt.ylabel('Average Likes', fontsize=12)
plt.xticks(rotation=45, ha='right')

plt.tight_layout()
plt.savefig("bar_chart_avg_likes.png", dpi=300)
plt.show()

8. Create a line chart for average views by platform.

plt.figure(figsize=(10, 6))
plt.plot(
    agg_data['platform'],
    agg_data['views'],
    marker='o',
    linestyle='--',
    linewidth=2
)

plt.title('Average Views by Platform - 7097', fontsize=14, pad=15)
plt.xlabel('Platform', fontsize=12)
plt.ylabel('Average Views', fontsize=12)
plt.xticks(rotation=45, ha='right')
plt.grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig('line_chart_avg_views.png', dpi=300)
plt.show()

9. Create a pie chart for the distribution of post types.

post_type_counts = data['post_type'].value_counts()

plt.figure(figsize=(6, 6))
plt.pie(
    post_type_counts,
    labels=post_type_counts.index,
    autopct='%1.1f%%',
    startangle=120,
    colors=plt.cm.Set2.colors,
    textprops={'fontsize': 12}
)

plt.title('Distribution of Post Types - 7097', fontsize=14, pad=20)
plt.tight_layout()
plt.savefig('pie_chart_post_type.png', dpi=300)
plt.show()

Result:

The Python script successfully analyzed social media data from a CSV file and generated bar, line,
and pie charts that clearly illustrated engagement patterns across platforms and post types.

