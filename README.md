# Netflix Data Analysis

A beginner-friendly Exploratory Data Analysis (EDA) project that uses Python to understand Netflix's movie and TV show catalog.

The project starts with a raw CSV file and uses Pandas, NumPy, Matplotlib, and Seaborn to inspect the data, clean useful columns, create visualizations, and discover patterns in Netflix content.

> **Note:** The dataset contains titles released between 1925 and 2021. The results describe this dataset and should not be treated as Netflix's current catalog.

## Project Objective

The main goal of this project is to practice the complete beginner-level data analysis workflow:

1. Load a real-world dataset.
2. Understand its rows, columns, and data types.
3. Check missing and duplicate values.
4. Prepare columns for analysis.
5. Ask useful questions about the data.
6. Create clear charts.
7. Explain the patterns found in the results.

## Questions Explored

The notebook investigates questions such as:

- Does Netflix contain more movies or TV shows?
- Which content ratings appear most often?
- How are titles distributed by release year?
- Which countries contribute the most content?
- Which genre combinations are most common?
- What is the distribution of movie durations?
- How did the amount of content added to Netflix change over time?
- How did the growth of movies compare with the growth of TV shows?

## Dataset

The dataset is stored at `data/netflix_titles.csv` and contains **8,807 rows** and **12 columns**.

| Column | Description |
| --- | --- |
| `show_id` | Unique ID for each title |
| `type` | Movie or TV Show |
| `title` | Name of the title |
| `director` | Director name(s) |
| `cast` | Main cast members |
| `country` | Country or countries of production |
| `date_added` | Date the title was added to Netflix |
| `release_year` | Original release year |
| `rating` | Audience/content rating |
| `duration` | Runtime in minutes or number of seasons |
| `listed_in` | Genre/category labels |
| `description` | Short summary of the title |

Some columns contain missing values. Finding these values is part of the analysis rather than something to hide. For example, `director`, `cast`, and `country` have noticeable amounts of missing data.

## Project Structure

```text
Netflix-Data-Analysis/
├── data/
│   └── netflix_titles.csv
├── notebooks/
│   └── analysis.ipynb
├── README.md
└── requirements.txt
```

## Tools and Libraries

- **Python** — programming language used for the analysis
- **Jupyter Notebook** — interactive environment for code, notes, and charts
- **Pandas** — data loading, filtering, cleaning, and aggregation
- **NumPy** — numerical operations
- **Matplotlib** — chart creation and customization
- **Seaborn** — statistical data visualizations

## Getting Started

### 1. Open the project folder

```bash
cd Netflix-Data-Analysis
```

### 2. Create a virtual environment

```bash
python3 -m venv .venv
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

Activate it on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install the required packages

The current `requirements.txt` is empty, so install the libraries directly:

```bash
python -m pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Open `notebooks/analysis.ipynb`, then run the cells from top to bottom.

## Analysis Workflow

### 1. Import the libraries

The notebook begins by importing Pandas, NumPy, Matplotlib, and Seaborn. This teaches how different Python libraries work together in a data project.

### 2. Load and preview the data

The CSV file is loaded into a Pandas DataFrame with `pd.read_csv()`. `df.head()` is then used to check that the file loaded correctly and to preview the first five rows.

### 3. Understand data quality

The notebook checks:

- the number of rows and columns;
- column names and data types;
- missing values;
- duplicate rows;
- the frequency of values in important columns.

These checks are essential because charts and conclusions are only reliable when the structure and quality of the data are understood.

### 4. Filter and transform columns

The analysis filters movie rows into a separate DataFrame, removes the `min` text from movie durations, trims extra spaces from `date_added`, converts that column to a date, and extracts a new `year_added` feature.

This is a simple example of **feature engineering**: creating a useful new column from existing data.

### 5. Visualize the results

Count plots and histograms are used to compare categories and show distributions. Titles, axis labels, figure sizes, and rotated tick labels make the charts easier to read.

## Key Findings

- The dataset contains **6,131 movies** and **2,676 TV shows**, so movies form about 70% of the catalog represented in the data.
- `TV-MA` and `TV-14` are the two most frequent content ratings.
- The United States is the most common single-country value, followed by India and the United Kingdom.
- `Dramas, International Movies` is one of the most common genre combinations.
- Much of the catalog growth happened after 2015.
- Most movies are concentrated around standard feature-film runtimes, approximately 90–120 minutes.
- International titles make up an important part of the catalog, showing Netflix's global content strategy.

These findings are observations from this dataset, not claims about Netflix's live catalog today.

## What I Learned From This Project

As a beginner, this project helped me learn how to:

- read a CSV file into a Pandas DataFrame;
- use `head()`, `shape`, `columns`, `info()`, and `describe()` to understand a dataset;
- detect missing values with `isnull().sum()`;
- detect duplicate rows with `duplicated().sum()`;
- count and rank categories with `value_counts()`;
- filter rows using conditions such as `df[df['type'] == 'Movie']`;
- clean text values with Pandas string methods;
- convert text into dates with `pd.to_datetime()`;
- extract a year from a date column;
- create a new feature for further analysis;
- build count plots and histograms with Seaborn;
- improve chart readability with titles, labels, sizing, and tick rotation;
- compare movies and TV shows using the `hue` parameter;
- turn raw values and charts into simple, meaningful conclusions;
- recognize that missing or combined values can affect the accuracy of an analysis.

Most importantly, I learned that data analysis is not only about writing code. It is a process of asking a question, preparing the data, selecting a suitable visualization, checking whether the result makes sense, and clearly communicating the answer.

## Beginner Notes and Common Improvements

The notebook is a learning project, so it also reveals useful areas for improvement:

- Methods must include parentheses: use `df.info()` and `df.describe()`, not `df.info` and `df.describe`.
- Use `plt.figure(...)` with a lowercase `f` when setting the active plot size.
- Convert cleaned movie durations to numeric values before plotting them.
- Use `.copy()` when creating `movies_df` to avoid Pandas `SettingWithCopyWarning`.
- Parse `date_added` carefully because it contains missing values.
- A row can contain multiple countries or genres separated by commas. Splitting and exploding these values gives a more accurate country or genre analysis than counting full combinations.
- Conclusions should be linked to a visible calculation or chart and should mention the limits of the dataset.

## Possible Next Steps

- Fill or label missing values using a clear strategy.
- Split multi-country and multi-genre entries before counting them.
- Compare movie duration by genre, country, or release decade.
- Analyze directors and cast members with the most titles.
- Create a correlation heatmap for suitable numerical features.
- Add chart images to this README.
- Convert the notebook into a reusable Python script.
- Build an interactive dashboard with Streamlit or Plotly.
- Add tested package versions to `requirements.txt` for reproducibility.

## Conclusion

This project turns a raw Netflix titles dataset into an understandable story through data inspection, cleaning, transformation, and visualization. It provides practical experience with the core tools used in Exploratory Data Analysis and creates a strong foundation for future data science and machine learning projects.

For a first data analysis project, the biggest achievement is not producing complex models. It is learning to explore data carefully, notice problems, ask better questions, and support conclusions with evidence.
