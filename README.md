# Welcome to our DS 306 Project!

### How to run
Download the .qmd file + CSV and place them into one folder. *Make sure you have all the files in a single folder only.*

You can run the file in R Studio, it is all one chunk so there should be no issue. There should only be one Quarto Markdown file titled "306project.qmd".

https://1zv46g-michael-cui.shinyapps.io/Dataset/

### Context
#### Dataset Description
We are using data from the US Census Bureau’s American Community Survey (ACS), titled “Poverty Status in the Last 12 Months”. The dataset covers Michigan poverty trends among residents from 2005 through 2024, except 2020 as a 1-year estimate for 2020 is not provided by ACS. It contains several variables, however we will specifically be looking at the following:
- Percent below the federal poverty line (which we will now be referring to as “poverty rate” moving forward)
- Sex: male and female
- Race: White, Black, Hispanic (any race), American Indian/Alaska Native, Asian, Some other race, Two or more races
- Educational attainment: high school graduates, some college or Associate’s, Bachelor’s or higher

#### Motivation/Interest
Our project aims to explore the progression of poverty throughout time within Michigan. Specifically, we aim to explore whether overall conditions are improving and whether economic disparities between gender, education attainment, and racial groups are narrowing. By analyzing this data over time, we aim to determine if society is making measurable progress in reducing poverty and promoting equity. This is valuable because it shows trends in poverty rate gaps across socioeconomic groups and can provide a good understanding of overall economic well-being and systemic disparities.

#### Statistical/Computational Question
Ultimately,  we ask how do poverty rates vary across educational attainment, sex, and racial groups in Michigan, and are economic disparities widening or narrowing over time?

#### Approach/Methods
Data was preprocessed, with each CSV file representing a year’s ACS 1‑year estimate; the files are named “ACSST1Y2010….csv”, with each file named with its respective year. We did not include the 5-year estimates within this project. 

Each file was read, cleaned, and merged into a long-form single dataset with “year” as an additional column. Relevant columns were renamed for clarity (ex: “Michigan!!Below poverty level!!Estimate” was renamed “belowpoverty_pop”). Group labels were converted to uppercase and whitespace was removed. Poverty rates were originally stored as percentages but needed to be converted to numeric values to function correctly; they are still represented as percentages in the analysis. Subsets of the data were then created for specific analyses: gender data included only “Male” and “Female” rows, race data combined similar categories and removed ambiguous entries, and mean poverty rates were computed by year for each group. The resulting cleaned datasets (df_gender, df_race, and df_education) were used for interactive visualizations using Shiny.

#### Interactivity
The Shiny app contains three main tabs:
- By Gender: bar graph that plots poverty rates for males and females over a specified year.
- By Race: line graph that plots poverty rates for races over time (NH/PI was not included within this project as it did not have enough data)
- By Education: bar graph that plots poverty rates by educational attainment over a specified year.

The Shiny app provides a customized method of exploration as users are able to choose what specific variables they would like to explore. In the gender tab, users select a year to view a bar graph comparing male and female poverty rates, along with a regression summary showing each group’s long-term trend. In the race tab, users can choose two racial groups to compare directly in a line graph, along with regression summaries describing the long-term trajectory of each group. In the education tab, users select a year to view a bar graph of poverty rates across educational attainment levels, with linear trend summaries included beneath the plot. The interactivity allows users to tailor the analysis to the groups and time periods that interest them, making the patterns easier to explore and interpret.

#### Findings
The first tab shows poverty rates for males and females over time. Both groups experienced a decline from ~2013 to ~2019, suggesting some overall improvement in economic conditions. However, females consistently have higher poverty rates than males, and the gap has remained fairly stable, indicating persistent gender-based disparities. 

The second graph shows poverty rates for racial groups over time. Black and American Indian/Alaska Native residents consistently experience the highest poverty rates, followed by Hispanic and multiracial populations. White and Asian populations have the lowest poverty rates. While some groups show slight declines over time, disparities between the highest- and lowest-poverty groups continue to persist (Black and White), illustrating continuous socioeconomic inequalities. 

The third graph shows poverty rates for educational attainment over time. Residents with less than a high school diploma consistently experience the highest poverty rates, followed by high school graduates, some college or associate’s degree holders, and then bachelor’s degree or higher. 

These visualizations confirm that while overall poverty in Michigan has seen modest improvement, economic gaps by gender and race remain significant. Moreover, our visualizations also demonstrate a common trend: poverty rates start off high, increase slightly until ~2013, decline from ~2013 to ~2019, and then increase slightly or plateau. This pattern reflects Michigan’s economic state: the early 2010s reflect the lingering effects of the Great Recession, when many households were still facing financial strain. The decline after 2013 reflects economic recovery and job growth after the recession. The small increase or plateau after 2019 reflects the COVID-19 recession.

#### Related Work
The [Women in the Michigan Workforce](https://www.michigan.gov/mcda/-/media/Project/Websites/mcda/reports/2024/Women-in-the-Michigan-Workforce-2024-Report.pdf) report by the Michigan Center for Data and Analytics examines a wide range of economic indicators for women vs. men in Michigan, including labor force participation, income, and occupation. Specifically, we are looking at the “Poverty” section (page 19). The section explores poverty rates in Michigan across the following variables: Race and Ethnicity, Employment Status, and Educational Attainment. While the report provides insights into several variables, it is limited to a single recent period. It also groups American Indian/Alaska Native, NH/PI, and Some Other Race Alone into “All Other Races.” Our project differs from this report as it is more expansive, looking into multiple demographic groups, examines multiple years, and visualizing how poverty gaps evolve over time. This allows us to explore long-term patterns and compare trends across gender, race, and education in a way that complements but goes beyond the findings within this report.
