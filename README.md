# Behind Schedule: An Investigation into Pittsburgh Regional Transit Performance

# Introduction and Motivation

Pittsburgh Regional Transit (PRT), formerly known as Port Authority, has aimed to provide reliable Bus and Rail Transportation for the Greater Pittsburgh Community since its inception. In addition to being used by Pittsburgh residents for recurring transportation needs, many students of Pittsburgh-based universities such as Carnegie Mellon University, the University of Pittsburgh, and Dusquesne Univeristy rely exclusively on Pittsburgh Regional Transit to commute to and from class, work, and social gatherings.

PRT has set monthly average On-Time Performance (OTP) goals for its Bus and Rail services, clarifying that a bus is considered "On Time" if it is no more than one minute early or five minutes late to its scheduled timepoint. These goals are 73% and 80% OTP for Bus and Rail service respectively. This report aims to quantify the reliability of PRT's service and evaluate whether it has consistently met its OTP goals holistically and for routes commonly used by university students. Its results are meant to inform university students and the broader community and ensure that PRT is held accountable to their goals.

# Dataset
Monthly OTP Data is sourced from the Western Pennsylvania Regional Data Center, where PRT has catalogued various datasets related to performance and ridership. The dataset contains 22,258 entries (rows), 11 features (columns), and covers the time period from January 2017 to September 2024. In 2018, PRT switched from a more archaic data recording system to one called Clever, which uses more timepoints and fixes previous technical issues. 

This dataset’s columns are as follows: <br>
<br>
*<b>id<b>* : unique identifier key <br>
*<b>route<b>*: route code for joining with PAAC geospatial data <br>
*<b>ridership route code<b>*: route code for joining with ridership data <br>
*<b>full route name<b>*: full route name as it would appear on bus headsign <br>
*<b>current garage<b>*: garage that route operates out of <br>
*<b>mode<b>*: bus, light Rail <br>
*<b>month start<b>*: first day of the month in YYYY-MM-DD format <br>
*<b>year month<b>*: year-month key in YYYYMM format <br>
*<b>day type<b>*: weekday, saturday, or sunday <br>
*<b>on time percent<b>*: [0,1] fraction of timepoints that bus/rail departed on time from the stop/station <br>
*<b>data source<b>*: UTA, Clever <br>

Our variables of interest are: *month start*, *day type*, *on time percent*, *full route name*, and *current garage*.

# Methodology
Data was split into bus and rail service, then preprocessed accordingly to deal with on-time performance values of 0. Observations with an OTP of 0.0 were determined to be entry errors and are dropped from the dataset. Following preprocessing, the report explores the research questions and utilizes data manipulation libraries (pandas) and visualization libraries (altair) for analysis. Our research questions are as follows:

<b> Question 1: Has PRT met its OTP targets this year, and have they improved over time (since 2017 when the data collection began)? <b>

<b> Question 2: Do CMU-Centric routes see better OTP? Which routes have the best and worst OTP? <b>

<b> Question 3: Does Bus OTP Performance Differ by Type of Day, and How Does Time of Year Affect this Relationship? <b>

To address the first research question, line charts and bar charts are employed that quantify Bus OTP in 2024, compare that year's performance to previous years, and determine at a high-level whether PRT's Buses are meeting OTP targets. 

To address the second research question, descriptive statistics and bar charts are employed that quantify Bus OTP across different routes, classified as CMU-centric routes or non-CMU centric routes. 

To address the third research question, boxplots, line charts, and bar charts are employed that quantify Bus OTP across the type of day both across all years recorded and in 2024, and determine whether PRT's Buses are meeting OTP Targets on certain service days.

# Discussion of Results

In 2024, while Rail Service consistently exceeded the 80% On-Time Performance (OTP) target set by PRT, the same cannot be said for Bus Service, which fell short of its 73% target. Though PRT may have initially considered these goals ambitious, it is disappointing that, despite a five-minute allowance for delays, no month in 2024 recorded an average bus OTP meeting 73%. Furthermore, fewer than 45% of bus routes met the OTP target in any given month, meaning more than half of the routes consistently arrived late. Particularly concerning is the downward trend in bus performance throughout 2024, with the lowest monthly average OTP recorded in September—coinciding with the return of students to campus, a period when reliable bus service becomes especially critical.

Since 2017, when PRT began collecting performance data, bus service has been influenced by numerous internal and external factors. Notably, OTP peaked in early 2020 but was sharply impacted by the onset of the COVID-19 pandemic in March of that year. There was a recovery in subsequent months, and performance metrics stabilized at levels slightly below the pre-pandemic peak. In 2021, PRT recorded its most consistent bus performance, possibly attributed to increased investment in services. As such, the company decided to kick off its rebrand in 2022, but this event unfortunately coincided with another sharp decline in performance. The degree to which any fund mismanagement and rebrand-related structual changes caused declines in performance is unclear, but it is probable that these changes at least partially contributed to the negative change in performance metrics. Since 2022, performance has hovered below pre-pandemic levels, with added volatility and inconsistency.

The poor performance of bus routes servicing Carnegie Mellon University (CMU) is especially problematic. These routes not only fall short of the 73% OTP target but also lag behind the system-wide average. Given that they pass through CMU, the University of Pittsburgh, and other Pittsburgh-based universities, it is plausible that increased ridership and traffic congestion in these areas contribute to delays. To address this, PRT has undertaken a project to construct a hyper-transit corridor servicing these routes. This Bus Rapid Transit (BRT) is described as one to “improve the transit amenity and reliability experience for all users of the corridor between the three neighborhood areas in the City of Pittsburgh. Five bus routes, the 61A, 61B, 61C, 71B, and P3 will become “BRT” routes, and provide upgraded service from Oakland heading west to Downtown Pittsburgh. However, even users of the non-BRT routes, which include routes 61D, 71A, 71C and 71D with shortened service, will experience the benefits of the BRT amenities in Oakland. In this area, all bus riders will experience upgraded stations with amenities, dedicated bus lanes, and transit signal priority. East of the Oakland area, these routes will continue to have the benefit of more reliable service by providing reliability improvements in Oakland". The 61A-D are some of the worst-performing routes in the entire city, and hopefully the BRT project, which is currently in phase 1 of its construction, will be able to significiantly improve the service of these routes.

Interestingly, routes connecting downtown Pittsburgh showed slightly better OTP compared to non-downtown routes, contrary to initial expectations. Although the difference was not statistically significant, it merits further exploration given its potential implications for route efficiency. Performance across PRT’s garages revealed that buses from the Collier garage consistently outperformed others, even though these buses must navigate the often-congested Fort Pitt Tunnel. This outperformance raises questions about operational practices or structural differences at Collier compared to garages in Ross, East Liberty, and West Mifflin.

Regarding service days, PRT categorizes them as Weekday, Saturday, and Sunday, which limits detailed analysis by assuming uniformity within these groups. While overall differences in performance by service day are minor, Sunday service consistently achieved higher OTP, likely due to lower ridership and reduced bus frequency. Although students may find the longer Sunday wait times frustrating, these lower frequencies appear to enhance punctuality. In contrast, Saturday service typically had the worst OTP, potentially due to higher ridership and its impact on schedules.

Seasonal analysis revealed additional insights. For instance, Saturday Winter service demonstrated the best relative performance across all groups and seasons, while Sunday Spring and Summer services performed best within their respective seasons. Fall service, encompassing only September, saw the strongest weekday performance. However, the uncharacteristic dip in May and September Sunday OTP remains unexplained but may be tied to ridership fluctuations or local events.

Looking forward, future work could benefit from analyzing ridership data in tandem with on-time performance to better understand the relationship between passenger volume and delays. Incorporating ridership insights might shed light on whether increased demand directly correlates with performance declines and could offer targeted solutions to mitigate these issues. Additionally, applying the same level of in-depth analysis conducted for bus service to rail service could yield valuable findings about the factors contributing to the superior performance of PRT's rail network. This comparative perspective might reveal best practices or operational strategies that could be adapted for bus services. Addressing these research areas could lead to a more comprehensive understanding of service dynamics.

# Appendix

Link to dataset: https://data.wprdc.org/dataset/port-authority-monthly-average-on-time-performance-by-route



