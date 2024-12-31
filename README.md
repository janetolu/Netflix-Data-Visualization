
# **Netflix Data Visualization Project**

## **Overview**
This project focuses on analyzing and visualizing Netflix data using Python and R. The goal is to perform data cleaning, exploration, and visualization to uncover insights about the dataset. The project also demonstrates the integration of Python and R for creating visualizations.

---

## **Contents of the Project**
- **Dataset**: The dataset used in this project contains information about Netflix shows and movies, such as genres, ratings, release year, and more.
- **Python Scripts**:
  - **Data Cleaning**: Handles missing values and prepares the dataset for analysis.
  - **Data Exploration**: Generates descriptive statistics and performs initial analysis.
  - **Data Visualization**: Creates charts and graphs to represent insights (e.g., genre popularity and ratings distribution).
- **R Script**: Integrates one Python-generated visualization into R using the `ggplot2` library.
- **Cleaned Dataset**: A cleaned version of the dataset is saved for use in both Python and R.
- **README**: Comprehensive instructions for accessing and understanding the code.

---

## **Instructions for Running the Project**

### **1. Prerequisites**
Ensure you have the following software installed:
- **Python** (3.8 or above) with the following libraries:
  - `pandas`
  - `matplotlib`
  - `seaborn`
- **R** with the `ggplot2` package installed.

### **2. Setting Up the Project**
1. Download or clone the project from the GitHub repository or extract the provided zipped file.
2. Ensure the dataset file (`Netflix_shows_movies.csv`) is in the project directory.

### **3. Data Cleaning and Preparation (Python)**
#### **Step 1: Load the Dataset**
- The dataset is loaded using `pandas`. Missing values are handled by filling or dropping rows based on relevance.

```python
import pandas as pd

data = pd.read_csv('Netflix_shows_movies.csv')
```

#### **Step 2: Handle Missing Values**
- Fill missing values for columns such as `director` and `cast` with "Unknown".
- Drop rows with missing `date_added`.

```python
data['director'].fillna('Unknown', inplace=True)
data['cast'].fillna('Unknown', inplace=True)
data.dropna(subset=['date_added'], inplace=True)
```

#### **Step 3: Save the Cleaned Dataset**
- The cleaned dataset is saved as `Netflix_shows_movies_cleaned.csv`.

```python
data.to_csv('Netflix_shows_movies_cleaned.csv', index=False)
print("Cleaned dataset saved successfully!")
```

---

### **4. Data Exploration (Python)**
#### **Step 1: Describe the Data**
Generate summary statistics for numerical and categorical columns.

```python
print(data.describe())
print(data['rating'].value_counts())
```

#### **Step 2: Statistical Analysis**
Explore trends in the dataset (e.g., count of TV shows vs. movies, most common genres).

---

### **5. Data Visualization (Python)**
#### **Step 1: Most Watched Genres**
- Use `matplotlib` and `seaborn` to plot the most popular genres.

```python
import matplotlib.pyplot as plt
import seaborn as sns

data['listed_in'].value_counts().head(10).plot(kind='bar')
plt.title('Top 10 Most Watched Genres')
plt.show()
```

#### **Step 2: Ratings Distribution**
- Create a histogram to show the distribution of ratings.

```python
sns.histplot(data=data, x='rating', kde=True, bins=10)
plt.title('Ratings Distribution')
plt.show()
```

---

### **6. Visual Integration in R**
#### **Step 1: Load Cleaned Dataset**
- Import the cleaned dataset into R using `read.csv`.

```R
data <- read.csv("Netflix_shows_movies_cleaned.csv")
```

#### **Step 2: Create a Chart with `ggplot2`**
- Install and load `ggplot2` if not already installed:

```R
install.packages("ggplot2")
library(ggplot2)
```

- Create a bar chart for most watched genres:

```R
ggplot(data, aes(x = listed_in)) +
  geom_bar(fill = "blue") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1)) +
  ggtitle("Most Watched Genres in Netflix Data")
```

---

## **File Structure**
```plaintext
Netflix_Data_Visualization/
│
├── Netflix_shows_movies.csv               # Original dataset
├── Netflix_shows_movies_cleaned.csv       # Cleaned dataset
├── data_cleaning_exploration.py           # Python script for cleaning and exploration
├── data_visualization.py                  # Python script for visualization
├── netflix_visualization.R                # R script for visualizing data
├── README.md                              # Detailed instructions
```

---

## **Running the Code**
1. **Python**:
   - Run the Python scripts (`data_cleaning_exploration.py` and `data_visualization.py`) sequentially.
   - Ensure the cleaned dataset is generated before moving to the R script.

   ```bash
   python data_cleaning_exploration.py
   python data_visualization.py
   ```

2. **R**:
   - Open `netflix_visualization.R` in an R environment (e.g., RStudio).
   - Execute the script to generate the visualization.

---

## **Tips for Submission**
1. Ensure all scripts are well-commented.
2. Save the project as a zipped file or upload it to a GitHub repository.
3. Include this README in the project.

---
