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
