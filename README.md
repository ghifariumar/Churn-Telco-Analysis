# Churn-Telco-Analysis

### **Telecom Churn Prediction**

[Data Source](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) 

### **Contents**

1. Business Problem Understanding
2. Data Understanding
3. Data Preprocessing
4. Modeling
5. Conclusion
6. Recommendation

### **Business Problem Understanding**

**Context**

Telecommunication company is a company that provides infrastructure for people to communicate through electronic transmission. People could subscribe to different plan offered by each telecommunication provider such as internet connection, messaging, telephone, etc. With the development of technology in each sector, connectivity is more needed than ever and telecomunication company played a big role in this information era.  

Target :

0 : Customer doesn't churn

1 : Customer churn

**Problem Statement**

As telecomunication developed and gives profit to shareholder, new entrants and competitors has emerge within the incumbent. In order for the company to deliver a great service with competitive price, it needs to be cost effective in every way. One of the way to be cost effective is to retain customers and prevent customer churning. As what [Harvard Business Review](https://hbr.org/2014/10/the-value-of-keeping-the-right-customers#:~:text=Depending%20on%20which%20study%20you,the%20one%20you%20have%20happy) shows that acquiring new customers are more costly than retaining existing ones.  

![image](https://user-images.githubusercontent.com/99155979/175281508-7820b581-585a-437c-a6bc-0071b7cadd33.png)

Image Source: https://paginas.fe.up.pt/~als/mis10e/ch9/chpt9-3bullettext.htm

Originally, telecommunication company pays attention more on consumer loyalty and when customers reach the end of their contract terms. Special promotion will be offered when a customer has high loyalty score and the loyalty score is set based on transaction frequency. However, it does not take into account customer who has lower transaction frequency but with high transaction value.There are also other case where a customer are spending more than a hundred dollars a month but is only transacting once a month; in consequence the customer is classified with a low loyalty score. Telco company should take a more active role in analysing customer's history uasage pattern and formulate a strategy to retain customer.

**Before**
![image](https://user-images.githubusercontent.com/99155979/175281567-4febb2bc-8711-4a4f-a065-2d7ba2af04b9.png)

 **Goals**

![image](https://user-images.githubusercontent.com/99155979/175281692-65ebef09-795d-45f5-a436-301a09aa46a3.png)

A Telecomunication company has possessed data which contains it's customer's details and their usage history. With the data available, the company wanted to obtain value from it by processing it to get insights and predictive models for its uses. The predictive model will be built to predict customer probability of churning. And this ratio of probability will be used in the new flow to improve services and products.

There are two types of marketing strategy: the untargeted and the targeted. First, focusing on brand loyalty and mass advertising. Second, relies on targeted action and giving special program and incentives (recduce price, custom plan, etc).
With machine learning, we could do targeted approach that are based on churn probability which can be useful in retaining price-sensitive customers or those who need special services from the service provider and in the end improving company's margin. 

**BUSINESS QUESTION**

1. How does type of contract affect churn percentage?
2. How does monthly charges paid by subscriber played a role in customer churn?
3. Which type of internet service affects customer churn most and how to improve it?
4. Which type of payment method affects churn rate the most?
5. Does Tenure affects churn rate and how?
6. Which type of additional features affects churn and customer amount?

**Analytic Approach**

This project will aims at creating a model that is predicting (Predictive) churn probability using the data.The data will be analyze to obtain pattern that differentiate between customers who will remain and customer who will churn. With the classification model obatained prescribtion will be formulated to prevent customer from churning.

**Metric Evaluation**

<img width="641" alt="image" src="https://user-images.githubusercontent.com/99155979/175283886-23088cbd-314b-43f3-8186-7d083eabd805.png">

Type 1 error : False Positive (Model predicts customer churn while it does not churn)

Consequence: retention cost (promotion) spent in vain
            
Type 2 error : False Negative (Model predict customer does not churn while it does churn)

Consequence: losing potention revenue

RECALL(+) CHURN

Based on the consequence, our goal is to construct a model that will minimize potential loss of revenue by having the least value of recall.

<img width="549" alt="image" src="https://user-images.githubusercontent.com/99155979/175282010-836f71f5-01d5-4374-8009-d429196b6010.png">

### **Data Understanding**

**Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| customerID | Object | Customer ID |
| gender | Object | Whether the customer is a male or a female |
| SeniorCitizen | Integer | Whether the customer is a senuior citizen or not (1,0) |
| Partner | Object | Whether the customer has a partner or not (Yes, No) |
| Dependents | Object | Whether the csutomer has dependendents or not (Yes, No) |
| tenure | Integer | Number of months customer has stayed with the company |
| PhoneService | Object | Whether the customer has a phone service or not (Yes, No) |
| MultipleLines | Object | Whether the cutomer has multiple lines or not (Yes, No) |
| InternetService | Object | Customer's internet service provider (DSL, Fiber optic, No) |
| OnlineSecurity | Object | Whether the customer has online security or not (Yes, No, No internet service) |
| OnlineBackup | Object | Whether the customer has online backup or not (Yes, No, No internet service) |
| DeviceProtection | Object | Whether the customer has device protection or not (Yes, No, No internet service) |
| TechSupport | Object | Whether the customer has tech support or not (Yes, No, No internet service) |
| StreamingTV | Object | Whether the customer has streaming TV or not (Yes, No, No internet service) |
| StreamingMovies | Object | Whether the customer has streaming movies or not (Yes, No, No internet service) |
| Contract | Object | The contract term of the customer (Month-to-month, One year, Two year) |
| PaperlessBilling | Object | Whether the customer has paperless billing or not (Yes, No) |
| PaymentMethod | Object | The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic)) |
| MonthlyCharges | Float | The amount charged to the customer monthly |
| TotalCharges | Object | The total amount charged to the customer |
| Churn | Object | Whether the customer churned or not (Yes or No) |
<br>

<img width="625" alt="image" src="https://user-images.githubusercontent.com/99155979/175282136-ddfba81e-def2-4dc8-9376-f2d69307a5fd.png">

<img width="630" alt="image" src="https://user-images.githubusercontent.com/99155979/175282309-3c3307be-907f-4307-b4d0-d37f3c037052.png">

<img width="536" alt="image" src="https://user-images.githubusercontent.com/99155979/175282377-68f0b2e7-1de7-4117-a7d6-2f7e35ac872a.png">

<img width="503" alt="image" src="https://user-images.githubusercontent.com/99155979/175282583-ac78bfef-06e2-41ae-a221-ec2d312994f6.png">

<img width="335" alt="image" src="https://user-images.githubusercontent.com/99155979/175282672-ff823fc3-0322-478e-bc46-38267da6f17b.png">

<img width="307" alt="image" src="https://user-images.githubusercontent.com/99155979/175282747-8839d69d-8f92-47a0-afd4-431fdc6bd7ad.png">

<img width="674" alt="image" src="https://user-images.githubusercontent.com/99155979/175282810-38b19a53-be45-4ccf-9782-009a1b2e1d04.png">

<img width="468" alt="image" src="https://user-images.githubusercontent.com/99155979/175282931-22a049aa-2206-4427-a2b4-3fc192006465.png">

How does type of contract affect churn percentage?

Based on graph above, it is known that a two year contract has the lowest churn rate, followed by one year contract and then month to month. This shows that the longer the time of contract, the more commitment the subscriber have. A month to month contract has the highest churn rate of 42%. With this in mind, encouraging customer to subscribe a longer contract would decrease churn rate. It can be done by giving more privilege and incentives for longer contract. 6 months contract would be one program alternative that could be done.

<img width="485" alt="image" src="https://user-images.githubusercontent.com/99155979/175283197-46d659e4-c9c4-4917-9ec0-b83eeff75376.png">

How does monthly charges paid by subscriber played a role in customer churn?

The graph above shows that the lower the charge that customer pay each month the less the churn rate is. Monthly charge of 80 dollars or more has the highest churn rate. Focusing on this group range of monthly charge is important. There are several ways that can be done to decrease the rate of churning while still maintaining their rate of spending. 
- give low cost incentives such as 5 mbps speed boost, free call among user.
- promotion program such as discount voucher for online application (spotify, apple store, netflix, games etc)

<img width="227" alt="image" src="https://user-images.githubusercontent.com/99155979/175283329-110142c0-10f7-46e5-9e30-e92c25b2ac4f.png">

Which type of internet service affects customer churn most and how to improve it?

DSL has the highest subscriber, followed by fiber optic. However the churn percentage of each services shows a different insights. Although Fiber Optic is the best in terms of speed, it has the highest churn rate. It shows that there is something wrong with this services. Either the fiber optic service offered isn't attractive enough compared to competitor's one or the service offered is not good enough. Further investigation needs to be done in this area.

Possible fiber optic problem
- Quality assurance constraint (fragile fiber optic cable)
- Constant signal loss
- High Traffic results in slow speed
- high price 

<img width="520" alt="image" src="https://user-images.githubusercontent.com/99155979/175283387-ba46ddca-ec6d-49cd-b975-8165a06f31f9.png">

Which type of payment method affects churn rate the most?

There are 4 types of payment method. Most of them has the similar amount. Electronic checks method has the highest number overall with also the higest number of churn, followed by mailed check. This shows that checked method still has its own market but a lot of people are switching from it. Encouraging customers towards a simpler payment method will results in lower churn rate.

<img width="436" alt="image" src="https://user-images.githubusercontent.com/99155979/175283438-17bee5a8-d337-42f5-a199-379d37731bc1.png">

Does Tenure affects churn rate and how?

The figure above shows that consumer churn happens on the first half year. After it goes beyond half year less customer are churning. There are several reasons that explains this phenomenon. First, the first 6 months of a customer is the time where customer are trying out the service and after that they are deciding whether they are continuing with the service or they are swithing to try on other carrier. Second, the trends that flattens down on the churn(Yes) section shows that the longer a customer has subscribed, the less the probability they churn. The effort of switching at this time might be a lot more than the benefit they will get fromm swithing. And they might just already being comfortable with the current service. 

Therefore, being more active and engaging to customer on the first year of customer lifetime is crucial. Developing programs and promotions might be an alternative.

<img width="283" alt="image" src="https://user-images.githubusercontent.com/99155979/175283492-df20ead6-21e0-4eb0-9147-818a0b73aac8.png">

Which type of additional features affects churn and customer amount?

The first plot shows the total number of customers for each additional service, while the second shows the number of clients that churn. We can see that:

Customers with the first 4 additionals (security to tech support) are more unlikely to churn
Streaming service is not predictive for churn


### Conclusion & Recommendation

Based on the classification report , we could conclude that our model could help telco company in filtering customers tendency of churning. 

we could predict correctly .... % of churning.

with this insights obtained from the model, company needs to take the right approach towards customer that has high probabilty of churning. The right approach determines whether the customer will or will not churn. 

Explanatory data analysis that are done reveal that there are several factors that affects customer churn. And from the condition that we experience, these are the things that could be done to improve the company churning rate. 
- Contract Type - as month to month contract has the highest churn rate compared to longer contract. We encourage product team to formulate new product with 6 month contract and Marketing team to make a campaign that encourage subscriber to commit for a longer time. 
- Monthly Charges Paid - A monthly charge 80 dollars or more has the highest churn rate while giving the highest revenue. We need to maintain the spending while decreasing the rate of churning by giving more perks and incentives for high spender such as internet speed boost, free call, discount voucher for application.
- Type of Internet Services - Fiber optic proves to be the highest churn contributor compared to other services. We need to improve fiber optic serivces by improving its reliability in speed, and stable connection.
- Payment Method - Among the 4 payment method, the two checks method has higher rate of churning. We could improve this by encouraging user to migrate to automated payment system like credit card or  bank transfer.
- Tenure - The longer the tenure the lower the probability of churning. Paying more attention to subscriber in the first 6 months of it's customer life needs to be done.

<img width="574" alt="image" src="https://user-images.githubusercontent.com/99155979/175283757-0b3a84e7-6f66-4004-914b-d97f34f28ee1.png">

From the research journal done by California State University we could assume that the retention cost to be $80 per customer.

With the model being in use, we have save and increase the margin by: 

- Spending Budget on all customer:
    - Cost per Customer spent: $80
    - Number of Customer: 7043
    - Total Money spend for retaining: $563,440

- Spending Budget on targeted customer (From 7043 customer in the data around 27% are predicted to churn)
    - Cost per Customer spent: $ 80
    - Targeted Customer: 7043 * 27%(churn percentage) = 1902 customer
    - Total Money spend for retaining: $80 * 1902 = $152,129

Money Spend Difference: $563,440 - $152,129 = $411,311
Based on the simple calculation performed above we could conclude that we could increase our margin by $411,311

- Spending Budget based on Confusion Matrix

<img width="293" alt="image" src="https://user-images.githubusercontent.com/99155979/179441101-52a1195c-4bc5-424d-8b60-651b8456931b.png">

    - Retention Cost Wasted
      $80 * 147 = $11,760
    - Acquiring Cost needed to recover lost customer
      $300 * 148 = $44,400
    - Without model
      (227 + 148 + 147 + 885) * $80 = $112,800
    - Saving
      $112,800 - $44,400 = $68,400
    
- Setting a threshold for targeted action. 
    - 0 - 0.3 = no action needed
    - 0.3 - 0.7 = half retention cost per customer = $40
    - 0.7 - 1 = full retention cost per customer = $80 
    - Assumption will varies depending on real scenarios.

Improvement that could be done:
- Improve network coverage
- Personalised rate plan based on each customer's historical data
- Domestic calls between intra-network (on-net) and inter-network (off-net)
types. 
- simplifying rate plan structures
- value-added service such as global roaming and data service
- An ‘unlimited’ usage plan for customers with high wireless usage needs
- loyalty programmes in which customers can accumulate dollar points for gifts redemption.
- roll-over minutes’ so that customers can retain the value of their unused minutes
- allowing customers to share their minutes with friends and family members
- historical usage information presented graphically in their
monthly invoices for customer to understand better
- recommending cost effective rate plans to customer on a periodical basis

Project limitation
This research has not examined other external factor that influence.....
Further research could be done to cover other areas and gain more insights in this field.


