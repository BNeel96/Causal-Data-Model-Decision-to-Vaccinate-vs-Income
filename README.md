# Causal-Data-Model-Decision-to-Vaccinate-vs-Income

**Basic Information**

* **Person or organization developing model**: Neel Barge, `nbarge96@gwu.edu`
* **Model date**: June, 2022 to July, 2022

**About Causal Inference**
- The notion of causality is a fundamental concept in human thinking.
- Current ML / AI techniques remain purely prediction-based. In other words: machine learning is very good at high-dimensional pattern
recognition (\is this a cat or dog?). But nothing in the theoretical basis of ML allows to capture the asymmetry inherent to causal relationships.
- If we want machines to be able to interact meaningfully with us, they should be equipped with a notion of cause and effect.
- This project is an attempt to reason Cause and Effect using a Causal Model to address Startegic and Business Decision Making challenges in the Industry.

**Intended use**
- Primary intended uses:
  - To find Causal Relationship between Individual's 'Income' and their 'Decision to Vaccinate' (The Indian Made Covid-19 Vaccine - Covaxin was released at Rs.1200 to Private Hospitals, which was  expensive than it's counterparts Sputnik V at Rs.948 and Covishiled at Rs.600.). Rising Vaccine price is a challenge for people with low affordability which is usually proportional to Individual's Income and is one of the major factor determining their Decision to Vaccinate.
  - The intended use is to build a Causal Discovery Model, and then validate it using Data Science techniques.
  - Primary intended users: Students and academics interested in Causal Inference using Causal Models.
  - Out-of-scope use cases: This is solely for educational purpose for learning. Any use beyond an educational example is out-of-scope.
- Describe the business value of your model
  - Causality is a conceptual framework aimed at bringing together people skilled in Data Science techniques and business domain experts for effective business decision making instead of pure data-driven methods in Data Science and Machine Learning.
- Describe how your model is designed to be used
  - The Causal Model is created by citing scientific journals and by consulting with Invested Stakeholders in the Vaccine Maufacturing Company. Although, the Dataset in this project is generated in Excel using formulas which are discussed in the Data Gathered section. In reality, this data could come from the Human Resource Team of the Company. 
- Describe the intended users for your model.
  - Causal Method of Analysis is an alternative approach to build AI with a notion of cause and effect, against the prediction based Machine Learning technologies used for Strategic Business Decision Making.
- State whether your  model can or cannot be used for any additional purposes
  - This Model is restricted to Educational purpose, aimed at understanding 'how to implement Causal Modleing in an Hypothetical Business Case'.

**About Business Case**

You are an Analyst for a Major COVID-19 Vaccine Manufacturer of India. Having encountered a business decision problem where company observed lower vaccination outcomes (hence lower Return on Investment) even after the release of Indigenous Vaccine. You suspect the high cost placed on the vaccine by the Company Management and Central Government is responsible for this outcome, whereas the Managment is divided on this result; one half interpreting it as  lack of awareness and fear among masses to vaccinate while the other half hpothesizes that is due to the large proportion of divided Income groups. You take lead to prove that there is a Causal Relationship between the variables and decide to prove it by building a Causal Model. 

By talking to invested stakeholders accross the company you come up with 12 variables. And build a Causal Model with them.

The Company Management and Central Government have put the prices of Vaccines at nearly Rs.1000(for simplified calculation purpose) for Private Hospitals, while the Government Hospital are giving out the same vaccine for free. The number of Government hospitals are not sufficient to contain the requirement. You hypothesize that lowering the cost of can lead to wider vaccination. So, you with a group of Data Analyst perform Causal Inference on all the parameters to find out the influence of Treatment Variable: Income on the Outcome Variable: Vaccination or Decision to Vaccinate.

**Data Gathered**
- Source of training data: The Data was created with formulas on researching Scientic Journals and materials Online.
- Define the meaning of all data columns.
 
|Name|Modeling Role|	Measurement Level| Description|
|----|-------------|-------------------|------------|
**Education** | input| int| The level of Education that the Individual completed before taking the Job. Here, it is assumed that graduation leads to higher Income.|
**Family Wealth**| input| int| Family Wealth is an unobserved variable which can affect Income and Education both. As Families with higher wealth tend to provide good education to their children as well as can lead to higher Individual Income owing to the Industry Influence.|
**Income**| input| int| The Earning Capacity of an individual. It depends on two variables that is Education received and the Family Wealth possessed by them. It is considered that Higher the Education received, higher would be the Income of the Individual. Also, if the Family Income has a direct impact on the Income.|
**Afford**| input| int| Affordability is an individual???s capacity to buy a Vaccine for themselves. It is influenced by persons Income and FamilyWealth.| 
**Age**| input| int| Usually, higher the age, higher is the income and stable is the job as it is considered in this data that people tend to take up administrative or supervisory roles as they get older. Aged people were also prioritized by the Government to take up the vaccines that lead to people above 45 years of age to get vaccinated. Also, if the Age is higher it would lead to a higher possibility of an Individual having Kids, making them willing to pay for vaccines to ensure their children???s safety. Further, as Covid witnessed more deaths among middle aged and people above 45 years of age. The Fear is assumed to have been associated with Age, where higher the Age higher is the fear due to Covid.| 
**Vehicle**| input| int|Having a vehicle allows a person to maintain social distancing in India. So owning a vehicle has an impact on Individuals ability to reach hospitals and vaccine drive centers during the Covid outbreak. Ideally, people with monthly income above the mean can afford to maintain the vehicle. Also, if you are an Essential Worker, there is a chance that you have a secure job and may possess a vehicle to reach the workplace.|  
**Fear**| input| int|Fear can be an instrumental factor in getting vaccinations among all age groups, but here we are focusing on Fear among higher Age groups. Assuming that the HR has collected this Data from User???s we can directly associate it with decision to vaccinate.| 
**Kids**| input| int|Having Kids can compel Individuals to vaccinate to assure their safety. Also, Age tends to affect people???s decision to have children.| 
**Essential Workers**| input| int| Essential Worker is expected to vaccinate himself under high priority as their services are required in the workplace. Hence, Essential Worker has a direct association with decision to vaccinate.| 
**Govt Mandate**| input| int| The Government of India had made priority provisions for the vaccination of people above 45 years of age. They were provided with free vaccinations at the Government Hospitals as well as prioritized at the Private Hospitals for first few months.| 
**Health**| input| int| HR has collected the Health Survey from each employee, where the employees are supposed to rate their Health on the scale of 1 to 10. 1 being ???Major Health Issues??? and 10 being ???Fit???| 
**Vaccination**| Outcome| int| Decision to Vaccinate is an Outcome variable and it determines the likeliness of the person to vaccinate.| 

**Data Modeled**
|Name| Formula Used| Formula Description|
|----|-------------|--------------------|
**Education** | ROUND(RAND(),0)+IF(B2>19300,1,0)|  The Education takes a random value and rounds it off to 1 or 0, which indicates if the Individual did their Graduation or No-Graduation. The ability to afford and complete Graduation also depends on the Family Wealth. The Average Family Wealth in India is Rs. 19300 per month, so if the family is above earning above this average, then the score for Education increases by 1.|
**Family Wealth**| ROUND(NORM.INV(RAND(),19300,5000),0)| Since the Average Indian family income is Rs. 19300, we take an Inverse Normal Distribution to assign this variable the appropriate values.|
**Income**| ROUND(31900*A2+B2*0.5+(E2-18)*500,0)| The Income of an Individual depends on 3 variables i.e. Education, FamilyWealth and Age. Since the Education makes a significant impact to a person???s ability to earn, this is adjusted by multiplying the Average Indian Monthly Income by Categorical Variable Education. Further, the influence of FamilyWealth has been incorporated by assuming that 50% of FamilyWealth per Month has contribution to your Monthly Personal Income. Finally, age leads to promotions and rise in pay, this has been compensated by adding Rs. 500 to Income for every year after 18 years of age.|
**Afford**| IF(C2>=31900,1,0) +IF(B2>=19300,1,0)| Affordability is an individual???s capacity to buy a Vaccine for themselves. This depends on two variables namely Income and FamilyWealth. So, a person can get a score of 0,1 or 2 depending upon Income and FamilyWealth.|
**Age**| 18+ROUND(RAND ()*52,0)| Age is considered between 18 on the lower end and 70 on the higher for the population.|
**Vehicle**| IF(D2>=1,1,0)| Having a vehicle depends on the Affordability, so a person above Afford score of 1 is considered to have access to Vehicle.| 
**Fear**| IF(E2>28.4,1,0)| Since Fear is related to Increase in Age. If the Age of an individual is above the Average Indian Age of 28.4 years, they are considered Fearful of Covid and assigned a score of 1, otherwise 0.|
**Kids**| IF(E2>18, IF(C2>31900,1,0),0)| Decision to have a kid depends on various variables. Primarily, the Individual should be aged above 18 years, and should have a stable Income which is considered as the Average Individual Income in this case.|
**Essential Workers**| ROUND(RAND (),0)| A Essential Person is assigned at random in this Data.|
**Govt Mandate**| IF(E2>45,1,0)| Government Mandate/priority to vaccinate, is for people above the Age of 45 years.|
**Health**|Round(RAND()*10,0)| Out of 10, how would the employee rate their health given any conditions.|
**Vaccination**|STANDARDIZE(D2,AVERAGE($D$2:$D$1000),STDEV($D$2:$D$1000)) + IF(E2>28.4,1,0)+IF(F2=1,1,0)+IF(G2=1,1,0)+IF(H2=1,1,0)+IF(I2=1,1,0)+IF(J2=1,1,0) + STANDARDIZE(L2,AVERAGE($L$2:$L$1000),STDEV($L$2:$L$1000))| The Decision to vaccinate is based on variables Afford, Age, Vehicle, Fear, Kids, EssentialWorker, GovtMandate and Health. Except Afford and Health all the variables return binary values depending on the condition. If the person earns above National Average, then they will consider vaccinating. Similarly, if the Age is above National Average of 28.4, they will consider vaccinating. If they possess a Vehicle or have Kids, possess Fear, are Essential Workers, have been Prioritized by the Government or have Health Conditions they will consider vaccinating. Since Afford and Health are categorical, they are standardized. If the Health is bad or Affordability score is low, then a negative score is obtained, which leads to lowering the vaccination score. The Vaccination Score for a person who is highly likely to Vaccinate is higher and positive while a person who is unlikely to get vaccinated is lower and negative.|

**Model details**
- State the Treatment and Outcome variable in the causal model
  -  Income and Vaccination.
