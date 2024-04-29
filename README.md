# MIST 4610 Group Project 2
### Group Name:

Sp24_47114_Group 1

### Tableau Packaged Workbooks:
[Question 1 Visualizations](https://outlookuga-my.sharepoint.com/:u:/g/personal/tam54565_uga_edu/EeLQLPm4-WtKtBLcgyfkAGMBaNrzB8cxZrEL8IqqWE7aQw?e=rudOZP)

[Question 2 Visualizations](https://1drv.ms/u/s!Auv_ZxgZOkEbrFXtG0wY_OC8COz1?e=WtkaMV)


### Group Members:

Isabelle Kiser 
[@isabellekiser](https://github.com/isabellekiser)

Will Cobb 
[@wjc56122](https://github.com/wjc56122)

Bhavik Maniklal 
[@BhavikManiklal](https://github.com/BhavikManiklal ) 

Ty Marcinczyk 
[@TylerMar1](https://github.com/TylerMar1)

Ryan Schoessling 
[@rschoess3](https://github.com/rschoess3)

Jaiden Timmons 
[@jaidentimmons](https://github.com/jaidentimmons)


### Dataset Description:

The dataset, sourced from https://catalog.data.gov/dataset/crash-reporting-drivers-data, offers insights into crashes within Montgomery County, Maryland. The Dimensions of the dataset include 43 columns and 170,218 rows,  and it encompasses various facets of crash data. These include:

- Report information: comprising report number, local case number, ACRS report type, and agency name.

- Crash details: covering elements such as crash date/time, municipality, latitude, longitude, location, route type, road name, cross-street type, cross-street name, and off-road description.

- Involved parties: related non-motorist, person ID, driver at fault, driver substance abuse, non-motorist substance abuse, injury severity, driver's license state, and driver distraction status.

- Collision specifics: collision type, vehicle damage extent, vehicle first impact locations, vehicle second impact location, vehicle body type, vehicle movement, vehicle continuing direction, and vehicle going direction.

- Vehicle information: encompassing vehicle ID, vehicle year, vehicle make, vehicle model, and equipment problems.
Environmental conditions: covering weather, surface condition, light, traffic control, and speed limit.

- Special circumstances: comprising circumstance, involvement of driverless vehicles, and incidents involving parked vehicles.
While most columns consist of string data types, exceptions include local case number (integer), crash date/time (Date/Time), speed limit (integer), vehicle year (integer), and longitude & latitude (decimal number).

Using this dataset has allowed us to construct comprehensive visualizations, enabling in-depth analysis of crash-related trends and patterns that helped us answer some important questions.


### Question 1:
__How does the hour of the day influence the prevalence of sobriety and substance abuse in reported crashes in Maryland, and are there specific locations in Maryland where sobriety and substance abuse incidents are markedly more frequent?__

### Importance:
The question regarding how the hour of the day influences the prevalence of sobriety and substance abuse in reported crashes in Maryland, and the identification of specific locations where these incidents are markedly more frequent, holds significant importance in many dimensions. Socially, pinpointing temporal and geographical patterns can facilitate targeted public awareness campaigns, fostering a cultural shift towards more responsible behavior and enhancing community safety. Economically, understanding these patterns helps mitigate the substantial costs associated with crashes, such as medical expenses and productivity losses, by enabling more effective preventive measures. From a public safety perspective, this data allows for strategic planning and resource allocation, such as increasing law enforcement presence during high-risk periods and improving road safety in prone areas, thus preventing accidents and saving lives. This multifaceted importance underscores the value of the data in driving informed decisions and interventions.

### Data Set Manipulation:
Our first question involves analyzing drivers who were sober vs under the influence so we needed to use the "Driver Substance Abuse" data column in our dataset. This column originally had 12 different domains including:
1. ALCOHOL CONTRIBUTED
2. ALCOHOL PRESENT
3. COMBINATION CONTRIBUTED
4. COMBINED SUBSTANCE PRESENT
5. ILLEGAL DRUG CONTRIBUTED
6. ILLEGAL DRUG PRESENT
7. MEDICATION CONTRIBUTED
8. MEDICATION PRESENT
9. N/A
10. NONE DETECTED
11. OTHER
12. UNKNOWN

Our group needed to isolate all domains that included being impaired into one group that contrasted with the crashes where nothing was present. To do this we created this calculated field:

IF [Driver Substance Abuse] = 'UNKNOWN' OR [Driver Substance Abuse] = 'N/A' THEN NULL ELSEIF[Driver Substance Abuse] = 'NONE DETECTED' THEN 'Sober' ELSE 'Under the Influence' END

We named this field "Sober vs Under the Influence" and while using it we filtered out "OTHER", "UNKNOWN", "N/A", and "NULL" in order to purely compare sober vs under the influence crashes. Creating this calculated field was critical in enabling us to visualize exactly what we wanted to through our graphs.

### Graphs and Analysis:
<img width="1222" alt="Screenshot 2024-04-24 at 3 30 57 PM" src="https://github.com/isabellekiser/Group1Project2/assets/150088753/1a3068cd-b4fb-411a-8550-f2ebc39b5a78">

Analyzing the line graph, we observe a noteworthy trend between sober and under-the-influence crashes throughout a 24-hour period. The data points represent the distinct count of report numbers for each category, plotted against the hour of the day.
From midnight (0) to the early morning hours, sober accidents are relatively low numbers. Sober accidents then experience a sharp increase from 6 AM, appearing to peak dramatically between 5 PM and 6 PM. This peak corresponds with typical rush hours and increased vehicular activity as people commute for work and other daytime activities. Post 6 PM, the count for sober accidents gradually declines but remains relatively high until the late evening.
In contrast, under-the-influence crashes maintain a low profile during the day, with a slight uptick in the early afternoon. However, as we transition into the evening and night, particularly from 6 PM onwards, there is a substantial increase in under-the-influence crashes. This rise continues to grow, peaking around the late-night hours. The increase in accidents under the influence during these hours likely correlates with social activities where alcohol and other substances may be consumed, such as dinners, parties, and late-night gatherings.
The inverse relationship between the two types of accidents is particularly interesting; when sober accidents decline as the day progresses into night, the under-the-influence accidents increase. The lower numbers of sober accidents in the late hours may also be attributed to reduced traffic, as fewer people are on the roads. Conversely, the night hours seem to embolden riskier behavior, such as driving under the influence, which could explain the rise in accidents during these times.

This data provides valuable insights for law enforcement and public safety campaigns, suggesting the need for increased vigilance and preventative measures during specific times of the day. The peak hours for under-the-influence crashes might be targeted for sobriety checkpoints or awareness campaigns to reduce the risk of such accidents.


<img width="1221" alt="Screenshot 2024-04-24 at 3 31 18 PM" src="https://github.com/isabellekiser/Group1Project2/assets/150088753/8988edd5-66f3-42cd-91dc-6a117350404f">

This geographic scatter plot illustrates the distribution of sober versus under-the-influence crashes across a geographic area. From the data represented on the map, we can draw several conclusions about the patterns of these accidents.
Sober accidents, marked in teal, are notably concentrated along major roads and within city limits, which are typically areas with higher traffic density and speed. These locations often correspond with highways and main streets where the higher volume of vehicles and complex driving environments increase the likelihood of accidents. The frequency and clustering of accidents in these areas may be indicative of the challenges of navigating busy roads, especially during peak traffic times when the volume of sober drivers is at its highest.
In contrast, under-the-influence accidents, marked in red, show a different distribution pattern. These incidents are more scattered and frequently occur on smaller roads, which tend to be local streets rather than major highways. The pattern suggests that driving under the influence crashes happen relatively close to neighborhoods or outside of central city areas. It makes sense that these would occur on less major roads, as individuals might assume they can safely drive short distances to their homes after consuming substances, underestimating the risk of an accident. This behavior reflects a false sense of security when driving on familiar or local roads, despite the impairment of their driving abilities.

The distinction in the location of these accidents highlights different risk profiles and suggests that prevention efforts might need to be tailored accordingly. For sober accidents, safety campaigns could focus on high-traffic areas and emphasize defensive driving. In the case of under-the-influence accidents, interventions might include promoting the use of ride-sharing services, especially in areas with nightlife establishments, and increasing patrols on secondary roads where such accidents are more prevalent.

### Question 2:
__How does the extent of vehicle damage correlate with the severity of injuries sustained by occupants in Maryland, and how might the inclusion of vehicle movement at the time of the crash affect these outcomes?__

### Importance:
Analyzing the correlation between the extent of vehicle damage and the severity of injuries sustained by occupants in Maryland is pivotal across many domains. Socially, understanding these dynamics can inform public education efforts, emphasizing the importance of vehicle safety features and responsible driving behaviors to reduce injury severity. Economically, such insights contribute to more effective allocation of resources, guiding investments in vehicle safety technologies and healthcare infrastructure to minimize the financial burden of accidents on individuals.

From a public safety standpoint, this analysis enables policymakers to develop evidence-based regulations and initiatives aimed at reducing both the frequency and severity of crashes. By identifying patterns where certain types of vehicle movements correlate with more severe injuries, authorities can implement targeted interventions such as traffic calming measures or enhanced enforcement of traffic laws to mitigate these risks.

This approach empowers law enforcement agencies and emergency responders to better prepare for and respond to incidents, potentially improving outcomes through faster and more appropriate medical intervention. Ultimately, by understanding the relationship between vehicle damage, occupant injuries, and vehicle movement during crashes, this research can drive comprehensive strategies to enhance road safety and protect lives

### Data Set Manipulations:
Our second question does not involve any data manipulation. We felt that data manipulation would not be necessary because we did not have a time element. If we were to do data manipulation we would have used a forecast system. This would mean that future data would be predicted using a time element, but since we did not have a time element this was not necessary for this question in this project.

### Graphs and Analysis:
![image](https://github.com/isabellekiser/Group1Project2/assets/150094078/0a963636-9334-4e95-8b1b-412b7a8ff1f7)

The graph above is a heat map, we chose to display the data in a heat map because they offer a visually intuitive way to understand complex data and facilitate pattern recognition. 

This chart shows us the numeric values of the amount of accidents associated between the type of movement the vehicle was in, along with the extent to which the vehicle was damaged. By analyzing this data, we can identify common scenarios that are more prone to result in accidents and assess the severity of those accidents based on the degree of vehicle damage incurred.

As seen in the visualization above, there are some common trends we can see. The trend to have the biggest disparity seems to be turning left vs turning right. In every category of damage extent, there seems to be at least triple the accidents occuring when drivers were turning left then turning right. This could potentially mean our public service workers need to implement more strict and obvious for left turn lanes as well as stoplights. 

In summary, the numeric values presented in this chart offer valuable insights into the relationship between vehicle movement, damage extent, and accident occurrence, allowing us physical evidence needed to proactively address road safety challenges and strive towards the ultimate goal of reducing the incidence and severity of road traffic accidents.



![image](https://github.com/isabellekiser/Group1Project2/assets/150094078/c05d4179-9dec-4be3-b569-8a21dbc1ccfe)

This bar graph represents the relationship between the extent of vehicle damage and the severity of injuries sustained in each accident. The rows are segmented into two columns, injury severity and vehicle damage. The most obvious observation is that the majority of accidents resulted in no apparent injuries. Of the accidents resulting in no apparent injury, most of the accidents resulted in disabling vehicle damage, followed closely by functional damage and superficial damage.

Analyzing the relationship between vehicle damage extent and severity of injuries can be helpful in many different ways when it comes to the principle of breaking down the casualties related with car crashes. By understanding how the severity of vehicle damage correlates with the severity of injuries sustained by passengers, politicians, researchers, and safety officers can develop targeted problem solving and policies to lessen the risks associated with road traffic accidents.

In conclusion, analyzing the relationship between vehicle damage extent and injury severity is a multi-step problem  with a lot of broad and specific complications for road safety, vehicle design, emergency response, healthcare, and accident investigation. By reflecting on the power of data and insights from this analysis, analysts can work together to create a safer and more efficient transportation system for everyone.


![image](https://github.com/isabellekiser/Group1Project2/assets/150094078/26000876-d2b6-4d2e-97d6-4d1f8d11a6f5)

This data visualization supports this data by offering the actual number of accidents in each group. It's particularly useful when examining categories of injury severity with significantly fewer accidents. It is difficult to compare results when the bars are small, however with the raw numbers it becomes much easier. For example, there were relatively few accidents that resulted in a fatality and it is difficult to comprehend these numbers with just the bar chart. By examining the second visualization, one can see that 125 fatal accidents resulted in a destroyed vehicle which is expected. The data contradict numerous hypotheses. For instance, one would expect a destroyed vehicle to result in at least some degree of injury, however, 3274 accidents where the vehicle was destroyed resulted in no apparent injury. In contrast, an accident with only minor superficial damage to a vehicle would presumably result in little to no injury. Contrary to this belief, there were 52 recorded accidents with serious bodily injury and one accident resulting in a fatality with superficial vehicle damage. These contradictions in logical assumptions highlight the uncertainty present in car accidents.

The differences in injury severity paint a picture where a majority of accidents result in no injury, even though the largest sector of vehicle damage is disabling. For this reason, it is conclusive that modern automobiles offer extremely effective protection from accidents. It would be informative to also create a time series of this data to understand the extent to which vehicle safety has improved over time.
