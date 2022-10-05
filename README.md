# Overview
This repository is created to show results on Trivago recommendations case (https://recsys.trivago.cloud/challenge/).
The goal of the challenge is to create a recommendation model that would suggest users most suitable hotels when searching. 
Our result based on MRR metrics is 0.62 on test dataset. With the first place in the competition scoring 0.68. 
# DEA 
Actually, there is no necessity in deep DEA as all the variabels are case sensitive. We presented engineered features such as:
- lenth of session (skewed distribution even after clipping) 
- number of filters changed during session (right skewed)
- number of actions per session (most users are idle) 
- distribution of prices of clicked hotels (right skewed)
- last action in session (75% to clickouts on hotels)
# Dataset creation
It is necessary to choose the right way for data combination, in this case we made groupby by sessions to analyze each session separately. Thus, for each session there are 10 features to run through the neural network and make predictions:
- impression appeared - number of current impression appearance
- time passed impression appeared - time passed after the last appearance of current impression in the list of current session references
- filter changed - number of changed filters
- price per salary - ratio of current impression price to wages
- steps last impression appeared - the number of steps after the last appearance of current impression in the list of current session references
- last action part impression - action type at the time of the last appearance of current impression in the list of current session references
- impression position - position of the current impression
- label - target reference label of the last click, which necessary to be predicted
- price - price of current impression
- sorted price position - position of the current price in the sorted price list
Final dataset consist of 826842 sessions with 25 impressions and 6 features for each.
# CNN model
For the prediction of the last click impression we implemented various CNN models with different architectures. The best model was selected after 10 epochs of training and then predictions on the test dataset were made. The best architecture consist of 2 Convolution, 3 Dense layers with 100 nodes in each layer. 

The used metric for the prediction is MRR metric, which is popular for the recommendation NN systems. The result of the test prediction is 0.62 on the MRR metric, the predicted data can be viewed in the Results.csv file. 

The reciprocal rank countplot results on the test dataset:

![image](https://user-images.githubusercontent.com/109418051/194177177-f75550e8-8be7-478e-b765-02522d3f2b87.png)


