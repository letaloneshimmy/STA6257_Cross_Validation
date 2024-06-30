## Group:
  - [Github: Andrew Mattick](https://github.com/andyMattick/STA6257_Project_CrossValidation.git)
  - [Github: Curtis Musson](https://github.com/letaloneshimmy/STA6257_Musson_CrossValidation.git)
  - [Discord: Crossvalisdation Board](https://discord.com/channels/1253401001113817270/1253401001545957406)
  - [Canvas: Crossvalisdation Board](https://uwf.instructure.com/groups/46154#)

## Project: 
  - [Website](https://letaloneshimmy.github.io/STA6257_Cross_Validation/)
  - [Slides]()

## More information:
- [Quarto: Markdown Basics](https://quarto.org/docs/authoring/markdown-basics.html)
- [Quarto: Typesetting](https://www.albany.edu/spatial/talk/quarto/lecture/91-quarto-markdown.html#:~:text=Math%20symbols%20in%20Quarto/markdown%20are%20handled%20with,the%20most%20common%20system%20for%20typesetting%20mathematical)
- [Class Web Site](https://uwf.instructure.com/courses/52193/pages/course-website?module_item_id=3144756)
- [GitHub](https://happygitwithr.com/index.html)
- [Video1 RStudio connection to GitHub](https://www.youtube.com/watch?v=MdmnE3AnkQE)
- [Video2 RStudio connection to GitHub](https://www.youtube.com/watch?v=jN6tvgt3GK8)

## Week 2 Atrical Summaries

### Atrical-1 [On Estimating Model Accuracy with Repeated Cross-Validation](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C10&q=On+Estimating+Model+Accuracy+with+Repeated+Cross-Validation.&btnG=) [G Vanwinckelen, H Blockeel, 2012]


#### Goal/why
The authors objective is to evaluate the benefits of estimating model accuracy with Repeated Cross-Validation (CV). Repeated CV is the process of repeat the CV multiple times then calculating a mean and confidence interval around the mean. Their hypothesis is that repeated CV is not useful.

#### Methods
A large data set was used to represent a population P
Nine data sets S were created by randomly sampling P n times.
- Experiment 1: The C4.5 method was used to model each S. S = 9, n = 200
- Experiment 2: The Naive Bayes method was used to model each S. S = 9, n = 200
- Experiment 3: The C4.5 method was used to model each S. S = 9, n = 1000
- Experiment 4: The Naive Bayes method was used to model each S. S = 9, n = 1000

Three 10-Fold CV estimates were calculated for each S. Each of the three CV estimates were repeated at different frequencies (1x, 10x, 30x) 
The mean CV estimate was calculated and a 95% CI was constructed around the mean. 
The population accuracy for each model was calculated.
The mean CV estimate and its upper and lower CI estimates were compared to the population accuracy.

#### results
The 95%CI range decreases as the number of CV repetitions increases. 
The model population accuracy value was within most (29/36) of the 1xCV 95%CI. As the number of CV reps. increase fewer of the model population accuracy value were within the 95%CI.
When the model population accuracy value was outside the 95%CI, most of the model population accuracy value were to the right of the 95%CI. Showing a pessimistic bias. 
The pessimistic bias decreases with an increased sample size.

#### limitations
According to the author repeated CV is recommend to reduce variance. Other CV studies have concluded that variance is greatly reduced when using the 10-fold CV, when compared to the Leave-One-Out CV method.  This experiment was done using the 10-fold CV method. I wounder if this experiment were done using LOOCV if the results/conclusions would be the same/similar.

If I  used Repetitive CV to estimate model error, I would not use the mean CV value,  I would use the max CV error estimate.

#### data that was used
Frank, A. and Asuncion, A. (2010) UCI Machine Learning Repository. University of California, School of Information and Computer Science. Irvine. http://archive.ics.uci.edu/ ml


### Atrical-2 [Assessing Model Fit by Cross-Validation](https://pubs.acs.org/doi/pdf/10.1021/ci025626i?casa_token=iSpUkNhlfsMAAAAA:nzsLXNNwrbIqqpp4fR5o8nYDSRt2Jr7SCMFXFA-n0lsb7G55C3jlDrTEIeJG89MYjxlQ-nmz2Z7ScepT) [@hawkins2003assessing]


### Goal

Provide evidence that, when the sample is small ("dozens or scores rather than the hundreds"), it is better to construct a QSAR model with all available data and use Cross-validation to estimate model error. Verses constructing a QSAR model with a portion of the available data (training set) and using the remaining portion of the data (test set) to evaluate model performance. The authors refer to the later method as "sample splitting".

### methods
#### Data cleaning 
predictors were removing if they:

-	perfectly correlated with another predictor

-	showed no compound to compound variation

-	were available for "a few" compounds

Of the original 379 predictors, 232 were used in the experiment.

#### Calibration
##### Training Set pool
100 of the 469 compounds were randomly selected.
300 ridge regression models were fit to the 100 selected compounds that predicted vapor pressure (y).

-	75 models were constructed with 5  randomly selected predictors (x)

-	75 models were constructed with 10 randomly selected predictors (x)

-	75 models were constructed with 20 randomly selected predictors (x) 

-	75 models were constructed with 50 randomly selected predictors (x) 

##### Assessment
Of the remaining 369 (469-100 training compounds) compounds, 50 were randomly selected for the test set. 
The experimental data set was the 319 remaining compounds 

The 300 models were used to predict the vapor pressure of the compounds in the experimental data set. The R-Squared [1-(sum(yi - yhat)^2 / sum(yi - ybar)^2 )] value for each compound was calculated. The experimenters made the assumption that this R-Squared value was the "True" R-Squared value of the population. 

Four experimental R-Squared values for each of the 300 calibration models were calculated to evaluate their performance.

1. Leave One Out Cross validation

2. Hold Out Set n = 10

3. Hold Out Set n = 20

4. Hold Out Set n = 50

The "true" R-Squared value mean and standard deviation were compared to the experimental R-Squared means and standard deviations. 

### results
With a sample size of 100:

-	The CV and 50-compond holdout set R-Squared values "seemed" to reliable predict the "true" R-Squared.

-	The 20-compond holdout R-Squared values showed more variation than  the CV and 50-compond holdout set R-Squared. The author concluded this method was inferior to CV and the 50-holdout. 

-	The 10-compund holdout R-Squared values showed "enormous" variation. The author concluded this method "useless".


### limitations
The authors conclusions are opinion based. This statistic is smallest than this statistic. This plot looks better that this plot. The is no evidence (hypothesis testing) to support the authors conclusions. 

### data that was used

The data set contains 469 compounds and 379 chemical descriptors. One of the descriptors was vapor pressure. Vapor pressure was the response variable in the models.

The data sets were from:

Basak, S. C.; Gute, B. D.; Grunwald, G. D. Use of topostructural
topochemical, and geometric parameters in the prediction of vapor
pressure: A hierarchical approach. J. Chem. Inf. Comput. Sci. 1997,
37, 651-655.

Basak, S. C.; Gute, B. D.; Grunwald, G. D. Use of topostructural
topochemical, and geometric parameters in the prediction of vapor
pressure: A hierarchical approach. J. Chem. Inf. Comput. Sci. 1997,
37, 651-655.
