🎯 Aim

To analyze and apply various data visualization techniques for qualitative (categorical) data in order to represent category-wise distributions and relationships effectively.

⚙️ Procedure

Import the required Python libraries such as Pandas, Matplotlib, Seaborn, and WordCloud.
Create a dataset containing categorical data related to social media platforms.
Convert the dataset into a Pandas DataFrame.
Generate a Bar Chart to visualize the frequency of platforms.
Create a Pie Chart to represent the proportion of user types.
Draw a Stacked Bar Chart to show engagement levels across platforms.
Generate a Word Cloud to visualize frequently occurring platform names.
Analyze and interpret the results obtained from the visualizations.

List of Tasks
1. Import required Python libraries (Pandas, Matplotlib, Seaborn, WordCloud).

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from wordcloud import WordCloud

2. Create a DataFrame containing qualitative social media data.

data = {
    "Platform": [
        "Facebook", "Instagram", "Twitter", "LinkedIn",
        "YouTube", "Instagram", "Facebook", "Twitter"
    ],
    "User Type": [
        "Personal", "Personal", "Business", "Business",
        "Personal", "Business", "Business", "Personal"
    ],
    "Engagement Level": [
        "High", "High", "Medium", "Medium",
        "High", "Low", "Medium", "Low"
    ]
}
df = pd.DataFrame(data)
df

3. Generate a Bar Chart to show the frequency of platforms.

plt.figure(figsize=(5, 5))
sns.countplot(data=df, x="Platform", palette="Set2")
plt.title("Frequency of Social Media Platforms")
plt.show()

4. Create a Pie Chart to represent the proportion of user types.

user_type_counts = df["User Type"].value_counts()
plt.figure(figsize=(6, 6))
plt.pie(user_type_counts,
        labels=user_type_counts.index,
        autopct="%1.1f%%")
plt.title("User Type Distribution")
plt.show()

5.Draw a Stacked Bar Chart to visualize engagement levels by platform.

engagement = pd.crosstab(df["Platform"], df["Engagement Level"])
engagement.plot(kind="bar", stacked=True)
plt.title("Engagement Levels by Platform")
plt.show()

6. Generate a Word Cloud to visualize frequently occurring platform names.

text = " ".join(df["Platform"])
wordcloud = WordCloud(background_color="white").generate(text)

plt.imshow(wordcloud)
plt.axis("off")
plt.show()

RESULT:
based on visualization technique for qualitative data the programs have been executed and
outputs are executed successfully.
