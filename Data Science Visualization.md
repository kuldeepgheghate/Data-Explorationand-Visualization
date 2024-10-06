from google.colab import drive
drive.mount('/content/drive')
import pandas as pd
df = pd.read_csv('/content/healthcare2.csv')
import matplotlib.pyplot as plt
import seaborn as sns
# Load the dataset

df.head()
df.info()
# Cleaning the data: Remove rows with missing values in important columns like Price, Year, and Kilometer
df_clean = df.dropna()
# Extract the year from 'Date of Admission' using string slicing
df['Year'] = df['Date of Admission'].str[-4:].astype(int)

# Create a line plot for Billing Amount over Year
plt.figure(figsize=(10, 6))
sns.lineplot(data=df, x='Year', y='Billing Amount', marker='o', ci=None)
plt.title('Line Chart: Billing Amount Over the Years')
plt.xlabel('Year')
plt.ylabel('Billing Amount (INR)')
plt.show()
# Create a bar plot for Billing Amount over Year
plt.figure(figsize=(10, 6))
sns.barplot(data=df, x='Year', y='Billing Amount', ci=None, color='pink')
plt.title('Bar Chart: Billing Amount Over the Years')
plt.xlabel('Year')
plt.ylabel('Billing Amount (INR)')
plt.show()
# Create a histogram for Billing Amount
plt.figure(figsize=(10, 6))
sns.histplot(data=df, x='Billing Amount', bins=10, kde=False,color='yellow')
plt.title('Histogram: Distribution of Billing Amount')
plt.xlabel('Billing Amount (INR)')
plt.ylabel('Frequency')
plt.show()
df.hist()
plt.show()
