# 🦠 COVID-19 Tracker & Data Analysis

This project analyzes global COVID-19 data to understand trends in cases, deaths, and vaccination rollouts across various countries. It uses Python and data visualization libraries to explore and communicate insights effectively.

---

## 📁 Project Structure

covid19-analysis/
├── data/
│ └── owid-covid-data.csv
├── notebook/
│ └── covid_analysis.ipynb
├── images/
│ └── [generated charts and maps]
├── output/
│ └── report.pdf (optional)
├── README.md
└── requirements.txt

yaml
Copy
Edit

---

## 📊 Project Features

- 📥 Import and clean COVID-19 data from [Our World in Data](https://ourworldindata.org/covid-deaths)
- 📈 Analyze time trends: total cases, deaths, and vaccinations
- 🌍 Compare COVID metrics across countries (e.g., Kenya, USA, India)
- 📉 Visualize with line charts, bar graphs, and optional choropleth maps
- 📄 Summarize insights in a report-style Jupyter Notebook

---

## 📦 Setup & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/covid19-analysis.git
cd covid19-analysis
2. Install Required Libraries
Use a virtual environment or install globally:

bash
Copy
Edit
pip install -r requirements.txt
3. Run the Notebook
Launch Jupyter in VS Code or browser:

bash
Copy
Edit
jupyter notebook notebook/covid_analysis.ipynb
🧰 Technologies Used
Python 3.x

pandas – data manipulation

matplotlib / seaborn – data visualization

plotly.express (optional) – for choropleth map

Jupyter Notebook – code + narrative + visuals

🌍 Data Source
Our World in Data – COVID-19 Dataset

File used: owid-covid-data.csv

📸 Sample Visualizations
(Add screenshots here or link to saved images in /images/)

📌 Key Insights
India experienced a sharp spike in mid-2021.

The US had a fast but uneven vaccination rollout.

Kenya had relatively low case numbers but also limited vaccine coverage early on.

📄 License
This project is for educational use only. Data © Our World in Data, released under a permissive license.

🙋‍♀️ Contributions
Pull requests are welcome. For major changes, please open an issue first to discuss.
