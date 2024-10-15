Overview of the Analysis:
The objective of this analysis is to build a binary classification model that predicts whether an organization applying for funding from Alphabet Soup will be successful if funded. The analysis utilizes machine learning, specifically a neural network, to identify patterns in historical data to guide funding decisions.


## Results

### Data Preprocessing

- **What variable(s) are the target(s) for your model?**
1. Target Variable(s):
The target variable for the model is the "IS_SUCCESSFUL" column, indicating whether an organization effectively utilized funding (1) or not (0). Additionally, "STATUS" can be considered as a secondary target variable, denoting an organization's active status.
2. Feature Variable(s):
The feature variables for the model include:
Application type (APPLICATION_TYPE)
Affiliation (AFFILIATION)
Classification (CLASSIFICATION)
Use case (USE_CASE)
Organization type (ORGANIZATION)
Income amount (INCOME_AMT)
Expense amount (EXPENSE_AMT)
Asset amount (ASSET_AMT)
3. Variable(s) to Remove:
Variables to remove from the input data because they are neither targets nor features:
EIN (unique identifier, not informative for modeling)
NAME (organization name, not relevant for prediction)
DATE (application date, potentially redundant with other temporal features)
Other ID columns or duplicate information


Compiling, Training, and Evaluating the Model:

How many neurons, layers, and activation functions did you select for your neural network model, and why?

AlphabetSoupCharity_Optimization.H5  
For the initial model 
Input Layer - 80 Nodes - Relu Activation  
I chose to run 80 nodes for this layer due to the number of dimensions within the dataset (42)  
Hidden Layer - 30 Nodes - Relu Activation  
30 Nodes was selected for this layer, again due to the number of dimensions within the dataset  
Output Layer - 1 Node - Sigmoid Activation  
The initial model resulted in:  
Accuracy: 72.23%  
Loss: 0.5787

Model Optimization:
Using Keras Tuner, I optimized the model by testing different configurations, including:  
Hidden layer count  
Neuron density  
Activation functions  

ran three different optimization models:
AlphabetSoupCharity_Optimization.h5 - This tuner ran the following options:
1-5 Hidden Layers
Activation functions either:
relu
tanh
Up to 80 nodes in the input layer, and up to 40 nodes in the hidden layers
The best model when ran with 100 epochs produced:
Accuracy: 72.44%
Loss: 0.5615

AlphabetSoupCharity_Optimization_V1.h5 - This tuner ran the following options:
6-10 Hidden Layers
Activation functions either:
relu
tanh
Up to 80 nodes in the input layer, and up to 40 nodes in the hidden layers
The best model when ran with 100 epochs produced:
Accuracy: 72.43%
Loss: 0.5605

AlphabetSoupCharity_Optimization_V2.h5 - This tuner ran the following options:  
1-5 Hidden Layers - Due to V2 model having a slightly worse accuracy score compared to V1, I've reverted back to only 1-5 layers.  
Activation functions either:  
relu  
tanh  
Up to 160 nodes in the input layer, and up to 100 nodes in the hidden layers  
I've increased the maximum size of nodes per layer to see if this improves the accuracy performance.  
The best model when ran with 100 epochs produced:  
Accuracy: 72.17%  
Loss: 0.5663  

Were you able to achieve the target model performance?  
Although optimization attempts were made, the target performance was not reached. The best model achieved:  
Accuracy: 72.44%  
Loss: 0.5615  

What steps did you take in your attempts to increase model performance?  
To enhance model performance, I utilized the Keras Tuner library to explore three distinct tuner programs. Key optimization strategies included:
Increasing the number of hidden layers
Adjusting the number of neurons per hidden layer
Optimization results revealed:
The optimal model architecture consisted of 2 hidden layers
The ideal number of neurons per layer ranged from 1 to 26
To further refine the model, I examined the dataset for potential variable removal. Following initial preprocessing, I determined that all remaining data was relevant for the model.
Recommendation for Future Improvement
Given the complexity of the dataset, I suggest collaborating with key stakeholders from the foundation to:
Discuss variable prioritization
Gain a deeper understanding of the dataset's nuances
This stakeholder engagement would facilitate a more informed approach to model optimization and potentially uncover new opportunities for performance enhancement.


Summary of Findings  
The deep learning model achieved an accuracy of approximately 73% on a complex, high-dimensional dataset, falling short of the 75% target. However, optimization efforts successfully reduced the number of required neurons and added only one additional layer compared to the initial model.  
Alternative Approach: Random Forest Algorithm  
A viable alternative to the deep learning model is the Random Forest algorithm, commonly employed in the finance industry. This model offers:
Scalability to large datasets
Robustness against overfitting
Resilience to noisy data
The Random Forest algorithm operates by:
Generating random predictions from multiple decision trees
Averaging these results to construct a robust model







