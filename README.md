# Descriptive-Analysis
In this Project,lets deep dive into descriptive analysis using python libraries such as Numpy and Pandas. For Data visualization I am using matplotlib.pyplot and seasborn libraries. 

### Index 
1) Preliminary Analysis of the Dataset
2) Non-graphical Analysis
3) Graphical Analysis - Univariate and Bivariate Analysis
4) Marginal and conditional Probability
5) Insights and Recommendations

### Load the DataFrame
```df=pd.read_csv('aerofit_treadmill.csv')```

Observations on the shape of data, data types of all the attributes, conversion
of categorical attributes to 'category' (If required), missing value detection,
statistical summary 
```df.shape```
```df.dtypes```
```df.columns```
```df.isnull().sum()``` To check whether the Columns consists any Null Values.
### Visual Analysis After Pre-processing 
``` python
 df1=pd.DataFrame(df['Age'])
bins = [0, 10, 20, 30, 40,50,60]
labels = ['0-10', '10-20', '20-30', '30-40','40-50','50-60']
df['Age_Group'] = pd.cut(df1['Age'], bins=bins, labels=labels)
```

``` python
sns.countplot(x='Gender',data=df)
plt.show()
```
### Analysis based on fitness 

``` python
plt.figure(figsize=(10, 5))
plt.subplot(3,3,1)
sns.barplot(x='Age_Group',y='Fitness',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,3)
sns.barplot(x='MaritalStatus',y='Fitness',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,7)
sns.barplot(x='Gender',y='Fitness',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,9)
sns.lineplot(x='Education',y='Fitness',data=df)
plt.xticks(rotation=90)
plt.show()
```

### Analysis based on Income 

``` python
plt.figure(figsize=(15, 10))
plt.subplot(3,3,1)
sns.barplot(x='MaritalStatus',y='Income',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,3)
sns.barplot(x='Gender',y='Income',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,7)
sns.barplot(x='Age_Group',y='Income',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,9)
sns.lineplot(x='Education',y='Income',data=df)
plt.xticks(rotation=90)
plt.subplot(3,3,5)
sns.barplot(x='Product',y='Income',data=df)
plt.xticks(rotation=90)
plt.show()
```

###Analysis based on Miles

```python
plt.figure(figsize=(10, 5))
plt.subplot(3,3,1)
sns.barplot(data=df,x='Age_Group',y='Miles')
plt.xticks(rotation=90)
plt.subplot(3,3,3)
sns.barplot(data=df,x='Gender',y='Miles')
plt.xticks(rotation=90)
plt.subplot(3,3,7)
sns.barplot(data=df,x='MaritalStatus',y='Miles')
plt.xticks(rotation=90)
plt.subplot(3,3,9)
sns.barplot(data=df,x='Product',y='Miles')
plt.xticks(rotation=90)
plt.show()
```
### Analysis based on Usage 
```python
plt.figure(figsize=(10, 5))
plt.subplot(2,3,1)
sns.barplot(data=df,x='Age_Group',y='Usage')
plt.xticks(rotation=90)
plt.subplot(2,3,3)
sns.barplot(data=df,x='Gender',y='Usage')
plt.xticks(rotation=90)
plt.subplot(2,3,5)
sns.barplot(data=df,x='MaritalStatus',y='Usage')
plt.xticks(rotation=90)
plt.show()
```

### Outliers Detection 
```python
plt.figure(figsize=(15, 10))
plt.subplot(2,3,1)
sns.boxplot(y='Age',data=df)
plt.subplot(2,3,3)
sns.boxplot(y='Usage',data=df)
plt.subplot(2,3,4)
sns.boxplot(y='Miles',data=df)
plt.subplot(2,3,6)
sns.boxplot(y='Education',data=df)
plt.show()
```

### Marginal Probability for Gender vs Product
```Python
Contingency_product_gender = pd.crosstab(df['Product'], df['Gender'], margins=Tr
marginal_product_gender = np.round(pd.crosstab(df['Product'], df['Gender'], marg
marginal_product_gender

contingency_table = pd.crosstab(df['Product'], df['Gender'])
conditional_gender_given_product = np.round(contingency_table.div(contingency_ta
conditional_gender_given_product

contingency_product_ms = pd.crosstab(df['Product'], df['MaritalStatus'], margins
marginal_product_ms = np.round(pd.crosstab(df['Product'], df['MaritalStatus'], m
marginal_product_ms

contingency_table2 = pd.crosstab(df['Product'], df['MaritalStatus'])
conditional_ms_given_product = np.round(contingency_table2.div(contingency_table
conditional_ms_given_product

```
### Marginal Probability for product vs marital status vs gender

``` python
Contingency_product_gender_marital = pd.crosstab(index=[df['Product'], df['Gende
marginal_product_ms_gender=np.round(pd.crosstab(index=[df['Product'], df['Gender
marginal_product_ms_gender

contingency_table3= pd.crosstab(index=[df['Product'], df['Gender']], columns=df[
conditional_ms_gender_given_product = np.round(contingency_table3.div(contingenc
conditional_ms_gender_given_product
```
Bivariate Analysis based on Fitness:

The age group between 40-50 rated themself higher in fitness followed by 20-30 age group.

Customers who are single rated themself higher compared to the custometrs who are partnered.

Male customers rated themslef higher compared to the female customers.

When the liplot is plotted for fitness vs education , it is observed that fitness rating increased with increase in education.
Bivariate Analysis based on Income:

The Bivariate analysis from icome vs maritalstatus show that partnered custometrs have higher income compared to the customers who are single.

The Bivariate analysis from icome vs gender show that male customers have higher income compared to the female customers.

The Bivariate analysis from product vs income shows thats customers with higher income prefer higher end product and customers with less income prefers lower end product.
The age group between 40-50 has higher income compared to other age group customers
The Bivariate analysis from education vs income shows customers with higer education will earn higher income.
Bivariate analysis based on miles:

The bivariate analysis from age group vs miles shows customers in age group 20-30 walk more miles followed by 40-50 age group.
The bivariate analysis from gender vs miles shows male customers walk more miles compared to female customers

Both single and partnered will walk equally.

The customers who bought KP781 product will walk more miles compared to the cutomers who bought KP481 anf KP281 products.
Bivariate analysis based on usage:

The age group between 20-30 usage is high follwed by 40-50 age group
Male customer usage is more compared to female customers.
Single and partnered usage is almost same.
Analysis based on HeatMap:

From the heat map drwan between numerical variables we can observe that , finess and miles(0.79) are highly correlated followed by usage and miles(0.76) and usage and fitness(0.67).

6).Recommendations - Actionable items for business. No technical jargon. No complications. Simple action items that everyone can understand

Promote High-End Products to High-Income Segments: Focus marketing efforts for high-end models like KP781 towards high-income customers. Emphasize the product's premium features and benefits.

Target Age 20-30 for All Products: Since the 20-30 age group has the highest purchase rate, design campaigns that appeal specifically to this demographic across all product lines.

Create Gender-Specific Campaigns for KP781: Since KP781 buyers are predominantly male, tailor ads or product information that addresses male customers’ fitness and status goals.

Offer Bundles for Partnered Customers: Since partnered customers tend to buy mid-range and high-end products, offer bundle deals or special partner benefits to increase engagement.

Highlight Fitness Benefits: Market the products based on fitness improvements since higher fitness levels correlate with frequent product use. Showcase testimonials and fitness progress stories.

Design Promotions Around Marital Status: Consider offering discounts for single individuals on the KP281 model, which they tend to prefer, while offering loyalty rewards for partnered customers who show more interest in mid-range models.

Develop Income-Based Financing Options: Offer flexible payment options for high-end models, enabling more customers from diverse income levels to purchase these products.
Age-Based Product Recommendations: Provide personalized product recommendations to customers based on age, as purchasing behavior varies significantly between age groups.
Encourage Frequent Use: Since increased treadmill usage correlates with higher customer satisfaction, provide fitness challenges or milestones for customers to keep them engaged.
Promote Education-Based Benefits: As higher education levels correlate with a preference for higher-end products, focus on informational content for educated customers highlighting product quality and advanced features.
insights based on the conditional and marginal probabilities calculated in the analysis:

Gender Preference Across Products:

Males have a higher likelihood of purchasing the high-end product, KP781, compared to females (conditional probability shows KP781 is preferred by males at a rate of 82.5%).

Both genders equally purchase KP281 and KP481, indicating these products appeal broadly and can be marketed without heavy gender-specific targeting.

Product Popularity by Marital Status:

KP281 and KP481 are preferred by partnered customers at a rate of 60%, while KP781 shows a similar trend with 57.5% partnered buyers. Partnered customers are more likely to purchase any product, indicating a potential market bias towards partnered individuals for all models.
Product Choice Based on Income:

KP281, an economical model, is preferred by customers with lower income, as shown by its higher marginal probability among this demographic. KP781, the high-end model, is favored by higher-income customers, supporting a clear segmentation by income for product positioning.
Impact of Marital Status and Gender on High-End Product (KP781):

Male and partnered customers are more likely to choose KP781. The probability analysis suggests that male, partnered individuals represent a primary customer base for high-end models, which can inform targeted campaigns for this demographic.
Gender and Marital Status Combined Influence on KP281:

Single individuals, regardless of gender, show a stronger preference for the budget model KP281. This suggests single individuals prioritize affordability, making KP281 a preferred choice among this group.
Overall Purchase Patterns:

Partnered individuals contribute 59.4% of total sales across all products, showing they have a higher purchase frequency. Aerolift can consider tailored promotions or loyalty programs for partnered customers to sustain this purchasing trend.
Broad Appeal of KP281:

KP281 has a nearly equal purchase distribution across male and female customers (each contributing about 22% to overall sales), indicating it is Aerolift's most universally appealing model. This product may not require significant demographic-specific marketing.
Single vs. Partnered Probability by Product:

Both single and partnered customers have nearly the same likelihood of buying KP281 and KP481, indicating these products appeal equally across marital statuses, though KP781 is more appealing to partnered individuals.
Probability Insight for Cross-Selling Opportunities:

Since KP481 has a strong preference among partnered males, there is an opportunity to cross-sell higher-end models to partnered customers who initially purchase KP481.
Distribution by Demographic Segmentation:

The marginal and conditional probability distributions by demographic data show that strategic segmentation by income, marital status, and gender for each product line can optimize marketing resources and focus on high-return customer groups.


