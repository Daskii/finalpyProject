# COVID-19 Global Data Analysis Report

## Introduction

This report presents an analysis of the global COVID-19 pandemic, utilizing data from Our World in Data. The analysis covers trends in cases, deaths, and vaccinations, with a focus on comparing metrics across different countries, specifically Kenya, the United States, and India, while also providing a global overview where appropriate. The primary goal is to explore the dataset, visualize key trends, and derive meaningful insights from the data.

## 1. Data Collection and Loading

The dataset used for this analysis is the `owid-covid-data.csv` file, sourced محبوب Our World in Data, a reputable and frequently updated repository for COVID-19 statistics. The data was downloaded on May 15, 2025. 

Upon loading the data using the pandas library in Python, an initial exploration was conducted. This involved examining the column structure, previewing the initial rows of data, and identifying the extent of missing values across various fields. Key columns identified for the analysis included `date`, `location`, `total_cases`, `total_deaths`, `new_cases`, `new_deaths`, `total_vaccinations`, `people_vaccinated_per_hundred`, `people_fully_vaccinated_per_hundred`, and `iso_code`.

## 2. Data Cleaning

To prepare the data for analysis, several cleaning steps were performed. First, the dataset was filtered to retain records only for the countries of primary interest: Kenya, the United States, and India. Rows with missing critical values, such as the date or location, were dropped to ensure data integrity, although these were found to be minimal for the selected columns. The `date` column was converted to a datetime object format to facilitate time-series analysis. Missing numeric values in other columns, which could affect calculations and visualizations, were handled by filling them with zero. This approach was chosen for simplicity in this initial analysis, though more sophisticated imputation methods like interpolation could be considered for specific variables in a more in-depth study. The cleaned dataset was then saved to a new CSV file, `owid-covid-data-cleaned.csv`, for subsequent analysis phases.

## 3. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was conducted to uncover initial patterns and trends in the COVID-19 data for the selected countries and globally.

### Total Cases and Deaths Over Time

Line charts were generated to visualize the progression of total confirmed COVID-19 cases and total deaths over time for Kenya, the United States, and India. Due to the significant differences in the magnitude of cases and deaths between these countries and over time, a logarithmic scale was used for the y-axis to better illustrate the trends in all selected nations on a single plot.

**Total Cases Over Time:**

![Total Cases Over Time](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvZWRhX3Bsb3RzL3RvdGFsX2Nhc2VzX292ZXJfdGltZQ.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZaV1JoWDNCc2IzUnpMM1J2ZEdGc1gyTmhjMlZ6WDI5MlpYSmZkR2x0WlEucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzY3MjI1NjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=OHm~PRHuU6dCZ3jz7fXQK4BW1keb~92zXvgjI6FFBn0Ac739yOF2-vISm9dRAqbaEIJYu~JRs~AvXUrVr8YfIa9Y3EKP7IrBBlfL2EVcteJUc4XfmyU4PuCu6zTFoVOpwJ52ndPamfP9WdrwrCDpYMGa77b2qyX3WcTKk01uwUk0JH9jeAnCRvfAeyW4uU9x~0RlLiF4VZBiWx78Tfr-slre-1W7zoahFUgbRQXELKYMa6afwQfL2zHfgJgkXlrpErsj6ss6lDQeK51NAsCbEnZgbhbW9-56k1q7yu9zlwhe2piyqf0GuCd060lxpiIGo2odNMG-fqvcJracr5aXsQ__)

**Total Deaths Over Time:**

![Total Deaths Over Time](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvZWRhX3Bsb3RzL3RvdGFsX2RlYXRoc19vdmVyX3RpbWU.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZaV1JoWDNCc2IzUnpMM1J2ZEdGc1gyUmxZWFJvYzE5dmRtVnlYM1JwYldVLnBuZyIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTc2NzIyNTYwMH19fV19&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=KeEdUMOk1QqCO~eXCvrmAFmPKrqQhN3nEsxg8IP3IJpf0q-lPWaZyUXNecHN3gLg3q~zwCXaRDbtxZg90zlFXLy0XFLDpPYERS3K2nIBlDTzLY5AQm5iw047Ve8YtsbjCxL8YRJ5VbliRj1LyID4l-mlO3Z377t7aX9a0ma8-9c56Q7UgvZaumi9ysT4e9NVFXoN9p5SKLWqlh7PbiXGPjnJlY2KvtjZf4PSVqa6pDXOLqaph4sv17jzNpQyddp8L9IqTEbaI6wTAXDkdROouq90MwFXAKUgVXjj5hmsKPjDRy222kP2yuzBaQJr23sfTcjhej~20TRrU-x-QWlrtw__)

These plots illustrate the different waves and overall impact of the pandemic in each country.

### Daily New Cases

To compare the daily incidence of new cases, a line chart visualizing smoothed daily new cases was created. Smoothing helps to identify underlying trends by reducing the noise from daily reporting fluctuations.

**Daily New Cases (Smoothed) Over Time:**

![Daily New Cases (Smoothed) Over Time](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvZWRhX3Bsb3RzL2RhaWx5X25ld19jYXNlc19jb21wYXJpc29u.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZaV1JoWDNCc2IzUnpMMlJoYVd4NVgyNWxkMTlqWVhObGMxOWpiMjF3WVhKcGMyOXUucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzY3MjI1NjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=B~okYYzk1XsYN-WXhelqXiBpMCIiLmZpOOW2sQOQYr2omU4tzWvH4ImzqfLgzuzR83mlsP3WIBvoeGZjX7rK1KU8qRMyRkjUERyGDHpeGR398lI7HAUP6pGNIJsfof3r84c12QaI-9hevEJHSaGdDabElRE3P-HScRsM9Sq7R~muHDBVkoNytUZBIA6ef6aSlouymRDstYXgHQfyo3k~TsTzGAO20cgTqDXQQcH-B-~-VFwS~3GDl0CBxjR7zN58l-4Z9ZmJ~V9d~3tL8HzsoXGgvyBAyRjh0WSQq~be8t6b5T8oAoHXUkHnGLv0r0Ls~pNe8yDuB7h8w4r1f6Q2~Q__)

This visualization highlights the timing and severity of various waves of infection in Kenya, the United States, and India.

### Death Rate Calculation

The death rate, calculated as `total_deaths / total_cases`, was computed for the latest available date for the selected countries. The results were saved to `death_rates.txt`. This metric provides an insight into the lethality of the virus in these locations at a specific point in time, though it is influenced by many factors including testing rates and healthcare capacity.

### Top Countries by Total Cases

A bar chart was generated to show the top 20 countries by total confirmed COVID-19 cases based on the latest available data. This provides a global perspective on the most affected nations.

**Top 20 Countries by Total Cases (Latest Data):**

![Top 20 Countries by Total Cases](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvZWRhX3Bsb3RzL3RvcF9jb3VudHJpZXNfYnlfdG90YWxfY2FzZXM.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZaV1JoWDNCc2IzUnpMM1J2Y0Y5amIzVnVkSEpwWlhOZllubGZkRzkwWVd4ZlkyRnpaWE0ucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzY3MjI1NjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=rboZ0KgCCP0c18otetI8ucyaYi4wNHDa5hd--xtquiCkgtdpp6~hVeE1n~XvFZfAn~NvEojPInS3rRrKmsGMbdcGzkbKVrFzjUqX0sY4J2HF0q02HsqrJYAZgelnZ7E4K6wSQQ1JbAyFeoay9DcOrJcDucgXkvWXvAva0QUXsozv-s7nfAqi3E-N662zARoIVUA5LrmCSvu9MJTp9JZY8NSDgp7E9sJ2Z07JEL2fCUp0wEvmmQ5QvyjifNwlvpu8lnF9ZylhIojuIKGnbb8rxrg1FyCP0zLpNOo4Ulb7XeaRSOCI88Etj~1rfyedtmqlEZ3ZNySX8zg3mKphEyqCWQ__)

## 4. Visualizing Vaccination Progress

The rollout and progress of COVID-19 vaccination campaigns were analyzed for Kenya, the United States, and India.

### Cumulative Vaccinations Over Time

A line chart depicts the growth of cumulative total vaccinations administered in the selected countries. A logarithmic scale was considered for the y-axis if the numbers varied greatly, to allow for comparison.

**Cumulative Total Vaccinations Over Time:**

![Cumulative Total Vaccinations Over Time](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvdmFjY2luYXRpb25fcGxvdHMvdG90YWxfdmFjY2luYXRpb25zX292ZXJfdGltZQ.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZkbUZqWTJsdVlYUnBiMjVmY0d4dmRITXZkRzkwWVd4ZmRtRmpZMmx1WVhScGIyNXpYMjkyWlhKZmRHbHRaUS5wbmciLCJDb25kaXRpb24iOnsiRGF0ZUxlc3NUaGFuIjp7IkFXUzpFcG9jaFRpbWUiOjE3NjcyMjU2MDB9fX1dfQ__&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=Bin1SOCKSPxYtUSQdq8DEqBUEdM-PGV4V2rhO-Nckw74cn7L2lRNIXVbTTzrBbfCvtQSHuEF~euld7Q8EZDEam4HCf2kbjZoTq0kC2cqPwc-pewqLg-md2r2-8oUh3l4B0SVMlzHkhPqZMm7gAwSIREp98-RwP80a4Vh-CurocrDYuq3f2g6ZuXwXfTQ4t46l3lFNQIcexB1nPBD3Np-YG5rFBpAw67DDXRYyoqsRYZynpPzbK9nfIjp4t3L47HQrQty9d4mQv44d7Nw-iqbCB2Zfidd7gW1TUNVDgDZJYjMkRfTeRln2IjeXzxUmfMDzFMXSxBJzR-J6YdowXCCng__)

### Percentage of Population Vaccinated

To understand vaccination coverage, line charts were created to show the percentage of the population that had received at least one dose of a COVID-19 vaccine and the percentage that was fully vaccinated over time.

**Percentage of Population Vaccinated (At Least One Dose):**

![Percentage of Population Vaccinated (At Least One Dose)](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvdmFjY2luYXRpb25fcGxvdHMvcGVvcGxlX3ZhY2NpbmF0ZWRfcGVyX2h1bmRyZWQ.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZkbUZqWTJsdVlYUnBiMjVmY0d4dmRITXZjR1Z2Y0d4bFgzWmhZMk5wYm1GMFpXUmZjR1Z5WDJoMWJtUnlaV1EucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzY3MjI1NjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=g-5QLlj~-4pzgCAyR5~KKuivN2hTNz8~ZmzsGsjwyxyqpK9zdtVfTekfrV4UlEMFLXeyZHvu8mF6GbIJuj4xP4Q1dOieOvz21yFzoBv5s2bY5Aovu0SWAKkJubBpSsmYOI~6cDriiU1ZaQdGZ1MlOSWLpVHnTlCmPaZrX29olE6ARNJxWuwp8ENwvlLDAAgO7mhy7QnjyZezwGdjv4Nfl2MxHtjqyZS5th2oTnJXIgRI1zeAiSY6RNmjCIQxkI17PBm5hrqCA~Ot0JL9uYSbgQDMqrwraX6tcudXZCtJPhH65jdBO2t~ETh9fLDD~jaMTzJkNg41LZNkfaEkTsmjQg__)

**Percentage of Population Fully Vaccinated:**

![Percentage of Population Fully Vaccinated](https://private-us-east-1.manuscdn.com/sessionFile/0lg3DBsLjsg5Onf7ruu7xm/sandbox/DOlvuYeiyFK6u4frvGel1q-images_1747338864557_na1fn_L2hvbWUvdWJ1bnR1L2NvdmlkX2RhdGFfYW5hbHlzaXMvdmFjY2luYXRpb25fcGxvdHMvcGVvcGxlX2Z1bGx5X3ZhY2NpbmF0ZWRfcGVyX2h1bmRyZWQ.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvMGxnM0RCc0xqc2c1T25mN3J1dTd4bS9zYW5kYm94L0RPbHZ1WWVpeUZLNnU0ZnJ2R2VsMXEtaW1hZ2VzXzE3NDczMzg4NjQ1NTdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyTnZkbWxrWDJSaGRHRmZZVzVoYkhsemFYTXZkbUZqWTJsdVlYUnBiMjVmY0d4dmRITXZjR1Z2Y0d4bFgyWjFiR3g1WDNaaFkyTnBibUYwWldSZmNHVnlYMmgxYm1SeVpXUS5wbmciLCJDb25kaXRpb24iOnsiRGF0ZUxlc3NUaGFuIjp7IkFXUzpFcG9jaFRpbWUiOjE3NjcyMjU2MDB9fX1dfQ__&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=hXGNcgz~w51lK5aKwnkSCNulVR2vzAdP-Ik1krfCOBbGwwKx~DeGLxmZab9IQ4fsU5mC93pZdxXx5HoAP-7XCpRNdIA84gzTjkRJIiZAhampVQj4Y30iklCodsiZ4Bf1veN22ZiA7AoTtS13F1-y1B2ge29~KSfFMtY2J~raoFo57g07e53DGyuW6snvTACJqF1u5FKZbqCHxEYL8Jg9EgAabQ6QQYQSCRM9bXPbt7VvRGw5ONt7Qrf3HDwPndIzaeRjyGxx2NI30ohkpFlfiXieMWidnzGLt7-uQHTFpU0hE~lnbZshu7~J0-Tat3Kg7uBO89-BDV1XWUhC0bFivA__)

These charts illustrate the pace and extent of vaccination efforts in the selected countries, highlighting disparities in vaccine access and uptake.

## 5. Choropleth Maps (Optional Analysis)

To visualize the geographical distribution of COVID-19 impact and vaccination efforts, choropleth maps were generated. These maps provide a global overview based on the latest available data.

**COVID-19 Total Cases per Million by Country:**

An interactive choropleth map showing the total cases per million people by country was created and saved as `choropleth_total_cases_per_million.html` in the `/home/ubuntu/covid_data_analysis/maps/` directory. This map helps to visualize the relative case burden across different nations.

**COVID-19 People Fully Vaccinated per Hundred by Country:**

Similarly, an interactive choropleth map illustrating the percentage of people fully vaccinated per hundred by country was generated and saved as `choropleth_fully_vaccinated_per_hundred.html` in the `/home/ubuntu/covid_data_analysis/maps/` directory. This map highlights global disparities in vaccination coverage.

(These HTML files can be opened in a web browser to view the interactive maps.)

## 6. Key Insights and Conclusion

This analysis of the Our World in Data COVID-19 dataset has yielded several key insights into the pandemic's progression and the global response, with a particular focus on Kenya, the United States, and India.

1.  **Varied Pandemic Trajectories:** The selected countries (Kenya, USA, India) exhibited distinct trajectories in terms of total cases, deaths, and the timing of infection waves. The United States and India, with their larger populations, reported significantly higher absolute numbers of cases and deaths compared to Kenya. The smoothed daily new cases plots clearly showed multiple waves of infection, often at different times and with varying intensity in each nation, reflecting differences in public health interventions, population density, and other socio-economic factors.

2.  **Disparities in Vaccination Rollout and Coverage:** Vaccination progress, measured by total vaccinations administered and the percentage of the population vaccinated, varied substantially. The United States generally showed a faster initial rollout and achieved higher vaccination coverage (both partial and full) earlier compared to India and Kenya. These differences likely reflect disparities in vaccine procurement, healthcare infrastructure, and public acceptance or access.

3.  **Global Impact Concentration:** The bar chart of top countries by total cases underscored that the pandemic, while global, had a concentrated impact in certain populous nations. The choropleth map of total cases per million further nuanced this by showing that some smaller countries also experienced high relative case burdens.

4.  **Ongoing Nature of Data Collection and Reporting:** The dataset is dynamic, with new data continually being added. The analysis performed reflects the state of the pandemic as of the last data update included in the downloaded file. Trends and rates, such as death rates, can change over time due to new variants, treatment improvements, and vaccination levels.

5.  **Importance of Contextual Factors:** While the data provides valuable quantitative insights, it is crucial to interpret these findings within the context of each country's specific circumstances, including testing strategies (which affect case detection), demographic profiles, healthcare system capacities, and implemented public health measures. For instance, the calculated death rates are influenced by the accuracy of both case and death reporting.

In conclusion, this data-driven exploration has provided a quantitative overview of the COVID-19 pandemic's impact and the global vaccination response. The visualizations and analyses highlight significant variations across countries and underscore the complex, multifaceted nature of this global health crisis. Further research could delve into correlating these trends with specific policy interventions or socio-economic indicators to gain deeper understanding.

## References

*   Hannah Ritchie, Edouard Mathieu, Lucas Rodés-Guirao, Cameron Appel, Charlie Giattino, Esteban Ortiz-Ospina, Joe Hasell, Bobbie Macdonald, Diana Beltekian, Saloni Dattani, and Max Roser (2020-2024) - "Coronavirus Pandemic (COVID-19)". Published online at OurWorldInData.org. Retrieved from: 'https://ourworldindata.org/coronavirus' [Online Resource]

