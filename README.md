# Japan-Football-Data-Project
## Step 1: Asking question - What is the purpose of this project

- **Deliverable**: A summary of the analysis task and the key stakeholders and audience
- **The analysis task**: is to find data that can explain the success of Japanese football(soccer) over the last 3 decades, so that to better advice the decision-makers of countries that want to develop their football.
- **Driven question**. How did Japan become the Asian soccer powerhouse in just about 30 years?
- **Key Metrics:**
    - number of registered players over years.
    - soccer popularity. soccer population (measured in soccer participants over total population) over year (to determine the cultural support)
    - number of soccer participants among students
    - number of soccer participants among the whole population
    
- Who is my audience
    - Sport and Culture Institution that hope to improve football performance
    - Sport Analytics Entities.
    - My football friends and community
- How can my insights help client make decisions
    - My insight might help the football association of other country to copy the right path into becoming better in football without wasting resources

## **Step 2: Data Preparation**

**Deliverable**: A description of all data sources used and the purpose of each data source

**Dataset 1: Number of registered players, teams, coaches, and instructors per year from Japan Football Association website page**

- This dataset was used to explore the change of number of registered players at Japan Football Association, one of the main indicators of a nation's football environment.
    - https://www.jfa.jp/eng/about_jfa/organization/databox/player.html
    - I copied the data into Excel sheet
    - NOTE: Records in this data might overlap with the Japan national team as one player could possibly register for more than one team. But the overall trend should not be significantly affected
    - **To see the detailed Classification of Attributes, please refer to the bottom part of the website**
 
**Dataset 2: Historical FIFA ranking dataset**

- **This dataset was used to explore the change of Japan’s performance over time**
    - https://www.kaggle.com/datasets/cashncarry/fifaworldranking/data (FIFA RANKING)
    - Data from Alex on Kaggle, which contains FIFA ranking from 1992 to 2024
- The dataset was pre-cleaned, so I directly imported it into Tableau for visualization

 **Datasets of participants by kinds of sports and education level in Japan**

- https://www.stat.go.jp/data/shakai/2011/index2.html#kekka
- I found datasets for the year 2006,2011,2016, and 2021, respectively

 **Datasets of participants by kinds of sports and region in Japan - geographical display of soccer popularity**

- https://www.e-stat.go.jp/stat-search/files?page=1&layout=datalist&toukei=00200533&tstat=000001050585&cycle=0&tclass1=000001050588&tclass2=000001050589&tclass3=000001050597&tclass4=000001050599&tclass5val=0
- I found datasets for the year 2006,2011,2016, and 2021, respectively
- All datasets above was collected by the Japanese government. Though credibility-ensured, the datasets still contains messy and mismatching data that needs to be cleaned and transformed
- I used these datasets to try to find the insight of soccer popularity among students and the overall population in Japan
- In the next step, I had to clean the data and calculate the metrics in a new sheet, simply because there was a lot of error or misinformation in the original dataset. Notably, some subsets don’t add up to total in the original data set, possibly due to the nature of survey. I transformed the datasets into more readable and goal-oriented datasets.

## **Step 3: Data Processing**

**Deliverable**: a detailed records of how each dataset was processed to be analyzed

**Registered Players Dataset**

- For the dataset of registered players from the JPA website, I copied them into Excel table since they are not massive data and can be easily manipulated in Excel.
- With this dataset I created two visualization. One simple line chart in Excel and the other more visually appealing chart in Tableau, both depicting the change of the number of registered players in Japan over time.

**FIFA Ranking Dataset**

- I directly import this dataset from Kaggle into Tableau to create visualization since it is a pre-cleaned dataset.

**Japan National Survey on Sport Activity by Region Dataset**

- I first loaded the four csv files into Excel (surveys of year 2006,2011,2016, and 2021 respectively). Then I cleaned the dataset to include only the total population of each prefecture (rather than keeping the two sub categorical records of employed and unemployed population).
- Then I integrate the data of all four sheets into one new sheet in order to transport them into Tableau and compare them longitudinally. In the new sheet I had only the fields of prefecture name, soccer participants, sample size, year (newly created field), and soccer participants to sample size - soccer percentage(newly created field, this is the metric I was interested in)
- I truncated the columns to keep only the more competitive sports as it is more in line with the focus of our analysis
- Next I changed the Prefecture names from Japanese into English in order to integrate with Tableau Map. I also checked for null values and any duplicated values

**Japan National Survey on Time Use and Leisure Activity - Participants in activities by kind of sport, sex, education**

- I load the four csv files into Excel (surveys of year 2006,2011,2016, and 2021 respectively). Then I cleaned the dataset to include only the total participants number of each educational level, rather than keeping the two sub categorical records of employed and unemployed population.
- Then I integrate the data of all four sheets into one new sheet in order to transport them into Tableau and compare them longitudinally.
- In the students dataset, I delete yoga, ground golf, and Gateball, because these attributes were not consistent over years.
- I then removed the records of technical college and graduate schools, since those educational level do not have a significantly big enough sample size to draw conclusions.
- Then, I checked for the null values. I found no participants records for elementary school, possibly due to Covid. But I decided to just leave it blank and transport into Tableau mostly because I didn’t want to alter the fact.
- I then deleted the sports that are both non-team based and not constantly physically demanding, such as walking and bowling, since these sports were not my focuses.
- Next, for the most challenging part, I transposed the dataset in Excel in order to compare the participants of different sports among students, as sports names made up fields in the original dataset. Doing so, I made each educational level one column and all the sports under the same column.

**In tableau**

- In the worksheet, I will display the sum of participants by sports in 小学，中学，高校，大学 （These four have to be in measures and to filter out, so that we can compare soccer with other sports in different education level)
- In the Rows, I will display different “Sports” - therefore, sports have to be in the dimension
- Luckily, I had already changed the data format in Excel by using transpose function.

I wanted to be able to filter both the educational level and the year in one sheet so that I didn’t have to make four separate sheets for each educational level.

- To do that I created a parameter
- I created a calculated field to link the parameter
    - use CASE statement, WHEN ‘parameter 1’ THEN calculated field 1
    - By doing this, I made a parameter for me to filter and display the specific number of students in each educational level, while still being able to filter year. Thus, I was able to manipulate two variables at the same time to see the change of participants longitudinally in different educational levels


In my Tableau dashboard, I created a total of six sheets:

1. FIFA Ranking Line Chart: Displays the dynamic ranking of any selected country, allowing for a comparison of Japan's historical ranking against other nations.
2. Bar Graph: Illustrates participant numbers by sport, year, and education level, enabling a comparison of soccer's popularity among Japanese students across different years.
3. Multi-Layered Area Graph: Shows longitudinal data on the number of registered players across various classes in Japan.
4. Map of Japan: Visualizes the percentage of soccer participants in all 47 prefectures, with color depth indicating the proportion of the soccer population.
5. Circles Graph: Highlights the top 15 prefectures based on soccer population, where larger circles represent a greater number of participants, and deeper colors indicate higher soccer populations.

## **Step 4: Analysis & Sharing data insight**
- Deliverable: a complete dashboard and an article to show the insight visually and verbally
- Please refer to my Medium story for the analysis part and important insights.
- Link to my Medium to view the data story I put together from the charts: https://medium.com/@siyuc_27512/how-to-rise-like-a-blue-samurai-c7912cf6ebd3
