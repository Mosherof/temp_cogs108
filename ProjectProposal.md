# COGS 108 Project Proposal 
### Team 82: Owen Guan, Keanu Nazemi, Jessica Fong, Melissa Osheroff, Aaron Moon

## Research Question
Can we accurately predict the average temperature for a specific day in San Diego given information on weather conditions such as rain, clouds, visibility, etc.?

## Background and Prior Work
Temperature is a measure of the intensity of heat in a substance or object; in this case, the focus is on the atmosphere and its relation to weather conditions that range from  rain, time of day, all the way to the intensity of UV rays. It is something that affects individuals every day and can be observed and predicted in a Weather app. The question we want to find to answer is, how does the Weather app predict the temperature? Is it possible for anyone to determine the weather in the future given the vast pools of recorded data for the city we live in, San Diego?

According to the National Weather Services, regardless of the weather type, all data is gathered using the same set of tools via radar, satellites, and various aerial or grounded measurement tools (US Department of Commerce NOAA, para. 1). Forecasters then graph the data using computer programs and create predictive models, conceptually, statistically, and numerically. Importantly, not every model fits best for a specific weather condition or temperature, so either the best model is selected or a mix of at least two models is used for weather forecasting visible to everyday people. For example, numerical modeling is simply the temperature in Farenheit, which is typically used by Americans and by extension, San Diegans. However, it is important to note that due to unpredictability and variance, models for temperature and general weather become more and more unreliable the farther into the future the model is predicting. Even a model still requires the human component to be more accurate (US Department of Commerce NOAA, para. 2). However, with the rapid development of machine learning models and AI, it is possible that the human component can be reduced and maintain or even improve temperature and weather forecasting.
The topic for this project aims to find patterns in weather which can be used to determine future predictions. More specifically, we are building a model which will determine the average temperature for a given day given data on precipitation, wind, humidity, dew point, visibility, and UV index. Along with our algorithm producing a number which represents the temperature in Fahrenheit, we plan on providing visualizations displaying the accuracy of the model. Because all climates differ in behavior and patterns, we decided to focus on weather in the city of San Diego. Additionally, background research highlights the importance of using a large dataset, incorporating statistical methods, and determining the relationship between the different variables.

Previous research works have also aimed at analyzing big data for weather prediction. One example is Weather prediction: A novel approach for measuring and analyzing weather data which proposes a system which takes in rainfall data in order to predict future minimum, maximum, and average (Navadia, para. 2).. Hadoop, an open source software which provides extended projects like Apache PIG which executes parallel data flows. Using Apache PIG and Bayes Algorithm, the relationship between precipitation levels and concurring days was able to be modeled for several series. 

A second example called Analysis Methods for Numerical Weather Prediction  also includes a Bayesian probabilistic argument approach to numerical weather prediction  (Lorenc, para. 8). One of the most stressed components of this article is determining idealized analysis equations and demonstrating using the maximum likelihood best estimate could be found as a solution. Additionally, analysis needs to consider the correlation between a variety of atmospheric fields and scales of motion. For example, rain and clouds often likely predict one another and are therefore largely determined by each other. This makes a nonlinear model much more appropriate which incorporates multiple dimensions.

Sources:
Lorenc, A C. “Rmets Journals.” Analysis Methods for Numerical Weather Prediction, rmets.onlinelibrary.wiley.com/doi/pdf/10.1002/qj.49711247414. Accessed 3 May 2024.

Navadia, Sunil. “IEEE Xplore.” Ieexplor.Ieee.Org, IEEE, 5 Oct. 2017, ieeexplore.ieee.org/Xplore/home.jsp.

US Department of Commerce, NOAA. “Forecast Process.” National Weather Service, NOAA’s National Weather Service, 31 July 2017, www.weather.gov/about/forecast-process. 
## Hypothesis
We hypothesize that the temperature will have a direct relationship with UV index, visibility, pressure,  dew point, and wind and an inverse relationship with humidity, precipitation. This is because UV index and visibility likely relate to how easily the sun’s light (heat)  is reaching San Diego; high pressure is related to settled conditions;  dew point can never be higher than pressure; and wind is created by temperature differences. When looking at the features that we expect to point to lower temperatures, we can expect humidity because warm air can hold more water than cold air; and precipitation because in order for rain to occur, water vapor must decrease in temperature. Although we will ideally be able to pull data for many consecutive years, the accuracy has a potential to be limited due to a possibility of weather features that are not recorded. As temperature is affected by a multitude of factors, some are not easily quantifiable, and thus less accounted for in the model despite their importance.

## Data
The ideal dataset that I would want would be quite high-dimensional. Preferably thousands to tens of thousands of observations, with variables collected at each observation being ones such as rain, cloudiness, UV index, wind speeds, temperature, etc. We could pull this off of a public API, store it as a csv file, and then clean, store, and organize it in a pandas dataframe. Some potential datasets include the following:

- [https://weatherstack.com/product](https://weatherstack.com/product)
- [https://openweathermap.org/api](https://openweathermap.org/api)
- [https://www.meteomatics.com/en/weather-api/?ppc_keyword=darksky%20weather%20api&utm_term=darksky%20weather%20api&utm_campaign=Dark+Sky+API&utm_source=adwords&utm_medium=ppc&hsa_acc=5001518620&hsa_cam=9781935523&hsa_grp=101551521004&hsa_ad=434964826447&hsa_src=g&hsa_tgt=kwd-746423936049&hsa_kw=darksky%20weather%20api&hsa_mt=p&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=Cj0KCQjwltKxBhDMARIsAG8KnqUPEtaIydZfJW-WWhEVwKYrSka-w3Y43Rton6tqUM0QoJlB6d2KHDsaApl1EALw_wcB](https://www.meteomatics.com/en/weather-api/?ppc_keyword=darksky%20weather%20api&utm_term=darksky%20weather%20api&utm_campaign=Dark+Sky+API&utm_source=adwords&utm_medium=ppc&hsa_acc=5001518620&hsa_cam=9781935523&hsa_grp=101551521004&hsa_ad=434964826447&hsa_src=g&hsa_tgt=kwd-746423936049&hsa_kw=darksky%20weather%20api&hsa_mt=p&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=Cj0KCQjwltKxBhDMARIsAG8KnqUPEtaIydZfJW-WWhEVwKYrSka-w3Y43Rton6tqUM0QoJlB6d2KHDsaApl1EALw_wcB)
- [https://www.tomorrow.io/weather-api/](https://www.tomorrow.io/weather-api/)

## Ethics and Privacy
- Are there any biases/privacy/terms of use issues with the data you proposed?
  - The data we seek to analyze for is sourced from government official or reputable sources. These APIs come from groups that practice open data, which means that there is little to no privacy issues due to the open nature of the data. The data is not personal, and there is no way to infringe on an individual’s privacy through this data. 
- Are there potential biases in your dataset(s), in terms of who it composes, and how it was collected, that may be problematic in terms of it allowing for equitable analysis? (For example, does your data exclude particular populations, or is it likely to reflect particular human biases in a way that could be a problem?)
  - The largest bias that is immediately apparent would be based on the location where the data is gathered. There are many areas that have different climates, less access to accurate recording equipment, and less population which would result in less data needing to be collected. Areas that are rural in nature are more likely to be overlooked or misrepresented. To combat this, for areas with less data we will pull from multiple sources to ensure consistency in the data.
- How will you set out to detect these specific biases before, during, and after/when communicating your analysis?
  - Before communicating our analysis, we will comb through the data to check if there are any holes or inconsistencies in the databases we are pulling from.
  - During our analysis, we will cross-reference the results of our model against other similar models that utilize similar datasets. This should help us confirm the accuracy of our data.
  - After communicating our analysis, we will reach out to stakeholders to get feedback on the data. Potential issues or receiving insight into how we can improve the model. The team itself will complete a final analysis to resolve any inconsistencies or errors, and see if we can root out any presenting biases.
- Are there any other issues related to your topic area, data, and/or analyses that are potentially problematic in terms of data privacy and equitable impact?
  - Again, there are little to no privacy issues with weather data. The representation of the data still could remain a concern, due to the fact that more affluent and populated areas are more likely to have ample/more accurate data. We will do our best to ensure that the data is representative of all geographical locations.
- How will you handle issues you identified?
  - We will adhere to the ethical practices of data gathering, as outlined by the professor, this course, and the expectations of this university, as well as Deon’s ethics checklist. We will keep a journal of our process throughout the project, so that if there is an issue, we can go back to see what kind of thinking got us there. We will be regularly testing this design with the stakeholders to ensure we are constantly in a feedback loop. Every member of our team aims to complete a project that is ethical, equitable, and insightful.

## Team Expectations
1. Communicating with team members when taking on a specific portion or are unable to complete previous assigned task
2. Dealing with conflict on project direction by discussion situation one-on-one before bringing it up to the group
3. Dealing with unequal work contribution by meeting collectively to rediscuss how to organize tasks
4. If conflict is unable to be resolved, reach out to the professor
5. If you are experiencing difficulty you must communicate with the team immediately to redistribute your workload
6. Members are expected to attend the weekly meetings, if something comes up you must communicate as soon as possible and catch up with the notes soon after
7. Members must be respectful of other teammate’s ideas, let each other speak, and generally have a good vibe. We're all stressed out students, let's try to make this project go as smoothly as we can!

## Project Timeline Proposal
- Decide research question and check if it is an acceptable project
  - Finish background research by week 5
  - Find previous research for possible data sets
  - Come up with hypothesis
  - Would prefer to have GPU access in datahub to fit a predictive model 
- Plot actual vs prediction
  - Start with an idealistic model and modify based on actual results
- Finish checkpoint #1 by week 6
  - Test and clean multiple high quality sets of data that correlate temperature to conditions like humidity, rain, time of day, etc.
    - Explain which datasets were used and why
    - Pre-process and clean all practical datasets
      - Explain why a specific cleaning method was used or if cleaning is unnecessary
- Finish checkpoint #2 by week 7
  - data analysis and graphing rough draft
    - Have at least 3 data visualizations for temperature: general temperature, temperature vs. rain, temperature vs. clouds, temperature in different geographical locations of San Diego, etc.
- Finish code / writeup by week 8 
  - Finish overview summary once results are finished
  - Submit, push, and pull request on Group 82 Repo
- Everything (presentation)  else by due date
  - Prepare presentation and explain project in class
  - Team evaluations per week and end of the quarter
  - Congratulations for being done!
