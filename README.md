# Stack Overflow Developer Survey 2025 — Python EDA

**Tools:** Python · Pandas · Google Colab  
**Dataset:** Stack Overflow Developer Survey 2025

## Overview

This project explores responses to the 2025 Stack Overflow Developer Survey using Python and Pandas. It examines professional experience, working arrangements, adoption of Python, learning methods, and reported annual compensation. The analysis consists of ten questions, including two additional investigations into Python adoption by age and the industries represented among higher-paid remote respondents.

The project demonstrates dataset exploration, filtering, descriptive statistics, grouping, aggregation, missing-value handling, and analysis of multi-select survey responses.

## Questions explored

1. How many respondents participated in the survey?
2. How many survey records have no missing values across the available questionnaire fields?
3. What are the mean, median, and mode of professional work experience?
4. How many respondents reported remote work?
5. What share of all respondents reported using Python?
6. How many respondents reported learning through online courses?
7. How do mean and median annual compensation for Python users vary by country?
8. What education levels were reported by the five highest-compensated respondents?
9. How does reported Python use vary across age groups?
10. Which industries are most common among remote respondents earning at or above the 75th compensation percentile?

## Selected results

| Measure | Result |
|---|---:|
| Survey respondents | 49,191 |
| Mean professional experience | 13.37 years |
| Median professional experience | 10 years |
| Mode of professional experience | 10 years |
| Respondents reporting remote work | 10,931 |
| Respondents reporting Python use | 37.5% |
| Respondents reporting online courses | 10,973 |

**Selected observations:**

- The 18–24 age group reported the highest Python-use rate in the displayed age breakdown (**40.0%**). The 65+ group reported **31.63%**.
- **Software Development (1,186 respondents)** was the most frequent industry among remote respondents with reported annual compensation at or above the dataset's 75th percentile.
- The mean work experience (**13.37 years**) is higher than the median (**10 years**), consistent with a distribution influenced by respondents with longer experience.

These figures come from the saved outputs of the notebook. Counts and proportions are survey-response statistics, not population estimates. For the Python percentage, the denominator is all 49,191 survey records, including records with missing language responses.

## Visualisations

### Python use by age group

![Python adoption by age group](images/python_by_age.png)

### Industries among higher-paid remote respondents

![Industries of high-paid remote professionals](images/industries_high_paid_remote.png)

### Remote work and online learning

![Remote work and online-course learning counts](images/work_and_learning.png)

### Professional experience

![Mean, median and mode of work experience](images/work_experience.png)

The charts were prepared separately from the notebook's saved outputs; the original analysis code was not modified to generate them.

## Explore the analysis

- [View the Jupyter Notebook](developer_survey_eda.ipynb)
- [Open the original notebook in Google Colab](https://colab.research.google.com/drive/1wNeXrSRjq4b_Ja6ulMITpMRkeLxNQYb8?usp=sharing)
- [Stack Overflow Developer Survey — official source](https://survey.stackoverflow.co/)

## Run the notebook

The notebook was developed in **Google Colab**, using the Google Drive mount to load the two source files. It currently expects these files at the following paths:

```text
MyDrive/
└── stack-overflow-developer-survey-2025/
    ├── survey_results_public.csv
    └── survey_results_schema.csv
```

1. Download the **2025** public survey dataset and schema from the official Stack Overflow survey downloads.
2. Upload both CSV files into `MyDrive/stack-overflow-developer-survey-2025/` in your own Google Drive.
3. Open [`developer_survey_eda.ipynb`](developer_survey_eda.ipynb) in Google Colab.
4. Run the cells in order and authorize access to your own Google Drive when prompted.

The code imports `pandas` and uses Google Colab's built-in Drive integration. The complete source CSV is not included in this repository.

## Methodology and limitations

- Python-language use is identified from the multi-select `LanguageHaveWorkedWith` field.
- Annual compensation comparisons are calculated only for rows with non-missing `ConvertedCompYearly` values.
- Mean and median compensation are grouped by `Country`; small country samples and extreme values can make comparisons unstable.
- Higher-paid remote respondents are defined as those whose `ConvertedCompYearly` is at least the **75th percentile** of all available compensation values and whose `RemoteWork` response contains `Remote`.
- The notebook checks fully complete responses across all available schema question fields. A result of **zero** under this strict definition does not imply that the dataset is unusable: many survey questions are optional or conditional.
- The survey is observational and self-reported. Its findings should not be interpreted as causal effects or representative estimates of all developers.

## Files

```text
stack-overflow-2025-python-eda/
├── README.md
├── developer_survey_eda.ipynb
├── requirements.txt
└── images/
    ├── python_by_age.png
    ├── industries_high_paid_remote.png
    ├── work_and_learning.png
    └── work_experience.png
```

**Source:** Stack Overflow Developer Survey 2025. This is an independent educational analysis of the publicly available survey results.
