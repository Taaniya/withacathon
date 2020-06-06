# Intelligent Resource Predictor – Hospital Beds

India, along with the rest of the world is facing a global health crisis unlike any in the known  history — one that is killing people, spreading human suffering, and upending people’s lives. 
But this is much more than a health crisis. It is a human, economic and social crisis. The coronavirus disease (COVID-19), is attacking societies at their core and testing the infrastructure built over the centuries. The resultant shortfall in the resources is having a devastating effect in people’s lives. 
The number of people infected with the disease is growing at spurts which is burdening the already stretched Health Infrastructure including Hospitals, Testing Centers and other Health facilities.
Our solution proposes to forecast the number of people who would be infected by Covid-19 based on the historical data available and subsequently the number of persons, among the infected lot, who would require hospital admission.
Considering the number of hospital beds available currently for the patients, it further predicts the number of beds that would be required to admit the fresh cases that would arise every day. This analysis is intended to be used by the hospitals to plan for the expansion of their Covid-19 treating facilities.  
In future, it can be further extended to predict the care facilities required for isolating and providing food and medications to the infected patients and their families.  
Today’s healthcare organizations face increasing pressure to achieve better care coordination and improve patient care outcomes. To accomplish these results, organizations are turning to machine learning . This area of science   deals with the use of data and machine learning algorithms, predicting the likelihood of future outcomes based on past data.
The combination of machine learning and human-centered design can ensure that healthcare/goverment  providers address inefficiencies along the patient journey and tailor services to meet the demand of the challenges  times


For this purpose , we have used COVID-19 India data present in kaggle at [location](https://www.kaggle.com/sudalairajkumar/covid19-in-india) to estimate gap between available beds and required bed among all states using machine learning .
The dataset contain following files :-

AgeGroupDetails.csv
HospitalBedsIndia.csv
ICMRTestingLabs.csv
IndividualDetails.csv
StatewiseTestingDetails.csv
covid_19_india.csv
population_india_census201

### Problem :

This problem set is broken into three parts 
*	Predict number of positive patients for each state using previous days data for 7 days for now .
*	Predict number of patients requiring hospitalization based on data assumptions 
*	Number of beds equipped for treating COVID-19 patients is some fraction of total hospital beds available in a state

### Assumptions :
For arriving at this conclusion , we have made following assumptions:-
*	Percentage Distribution of age group for actual and predicted covid-19 patients for  all states is following

Category	    Age Group 	Percentage Distibution
Young 	        0-18	           25
Youth	         18-60             45
Senior-Citizen	60+	             30


We have further assumed that observed that 50% of young & youth and all senior citizen need to be admitted to hospital.

Total patient who require to be admitted =65/100*(Total patient predicted to be suffering from Covid-19)

*	Among all hospital beds that are available in a state only 5% of bed is equipped to treat COVID-19 patients
Number of beds equipped for treating covid-19 patients   =0.05*(Total available beds in a city)

### Exploratory Data Analysis :

![](/images/top5_confirmed.png)

![](/images/top5_deceased.png)

We have used LSTM - class of neural network models in machine learning that learns input information forming a sequence is RNN – Recurrent Neural Networks. These models can predict for current instance using the information fed to them in the past

### Modelling Approach :

We developed two models for identifying total number of bed requirement-
Model A(covid-19-analysis-univariate-lstm) :  Univariate LSTM model with past positive count of patient as a features to predict positive count of patient on a given day.  After identifying number of patients for a given day , we dwell down to number of patients who need to be admitted using following formulae

Total patient who require to be admitted =65/100*(Total patient predicted to be suffering from Covid-19)

Once the above statistics is identified number of beds that need to be equipped for treating COVID –19 patients can be calculated using below formulae

Number of beds equipped for treating covid-19 patients   =0.05*(Total available beds in a city)

![](/images/gaps_in_beds.png)

Model B(covid19-India-resource-predictor):- Multivariate LSTM model with past positive count, total positive samples of patient, population density  as a features to predict positive count of patient on a given day.  After identifying number of patients for a given day , we dwell down to number of patients who need to be admitted using following formulae.

Total patient who require to be admitted =65/100*(Total patient predicted to be suffering from Covid-19)
Once the above statistics is identified number of beds that need to be equipped for treating COVID –19 patients can be calculated using below formulae
Number of beds equipped for treating covid-19 patients   =0.05*(Total available beds in a city)

![](/images/positive_prediction_MH.png)

![](/images/positive_prediction_DL.png)










