# Pricing-Model-for-Airbnb-Properties
The business problem we are addressing is helping Airbnb hosts understand the numerical value of their apartments (target), to directly inform how to strategically price their rental properties (action) based on the type of rental and included features / amenities. To do this, our team has tested multiple models that use historical Airbnb data to identify what features of a property affect price. Ultimately, the main question we are trying to answer is as follows: Is there a price that our data model can recommend to maximize value creation and profit?

# Exploratory Data Analysis

Conducted exploratory data analysis and created an interactive dashboard using plotly and flexdashboard in R
https://gorgegj.github.io/JieGao.github.io/dashboard.html
The graphs show that 
1. price demonstrates three evident clustered pattern in terms of bed type.
2. the location impacts price a lot

# Modeling + Evaluation

In modeling our data, we used three different types of models: 
1. Linear regression (LR),
2. REPTree
3. M5P
all with 10-fold cross-validation. By using cross validation we are addressing the potential problem of overfitting. 

In defining the three models we used, linear regression is the most classic and common predictive model for a numeric target variable.5 REPTree is a decision tree that outputs a numeric value and is used as a regression, while the M5P classifier is a decision tree in which each tree node has a linear regression6. From our research and understanding, we can think of M5P as a combination of a decision tree and linear regression model.

The criteria we using are: 

1. Mean absolute error
2. Root mean squared error
3. Relative absolute error
4. Root relative squared error

which are defined in this blog: https://www.futurelearn.com/courses/data-mining-with-weka/0/steps/25396¢

## Main Findings
1. M5P performs best in prediction. 
Regardless of which criteria we use to compare the different models, M5P emerges as the best model among these three. However, all three models perform well in prediction. As an aside, it is important to note that WEKA only reports 5% significant factors in linear regression and also automatically solves any multicollinearity problems with the explanatory variables. WEKA automatically performs feature selection to only select relevant attributes.

2. The most important indicator of Airbnb pricing is room type.
In the REPTree model, the nodes at the top of the decision tree have the most explanatory power. In this visualization, we found that room type, neighbourhood, and review scores rating were at the top.

Moreover, the linear regression model validates these findings with room type having the greatest percent effect on pricing. With shared room as the dummy variable (benchmark), a private room can be priced 38% higher and an entire home apartment can be priced 92% higher than a listing that is a shared room with similar amenities. 
