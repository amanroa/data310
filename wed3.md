# City Data
## Aashni Manroa, Tao Chen, Maggie Kettelberger, Gwen Wagner

## Background

## Procedures

We tested 3 models with this data. However, all 3 models all had similar trends.
For levels 2 and 3 of wealth, all our models were very accurate.

When we tested level 2 of wealth, the first model of 
Numeric cols [size,gender, age, edu] + bucketized cols (age) performed the best
while the other two models performed the same.


    dataframe['wealthC'] = np.where(dataframe['wealthC']==2, 1, 0)

Numeric cols [size,gender, age, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.9960975646972656

Numeric cols [size,gender, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.9863414764404297

Numeric [size, edu] bucket[age] indicator [gender]
- Loss: nan
- Accuracy: 0.9863414764404297 

In the model testing level 3, all 3 models had equal accuracies. 


    dataframe['wealthC'] = np.where(dataframe['wealthC']==3, 1, 0)


Numeric cols [size,gender, age, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.9170731902122498

Numeric cols [size,gender, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.9170731902122498

Numeric [size, edu] bucket[age] indicator [gender]
- Loss: nan
- Accuracy: 0.9170731902122498

For levels 4 and 5 of wealth, the accuracy greatly decreased. 
This could be because there are less wealthy people in the data, 
so the model had fewer values to train on.

When we tested level 4, we found that the Numeric cols
[size,gender, edu] + bucketized cols (age) model performed the best, 
with Numeric cols [size,gender, age, edu] + bucketized cols (age) coming second.


    dataframe['wealthC'] = np.where(dataframe['wealthC']==4, 1, 0)


Numeric cols [size,gender, age, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.6360975503921509

Numeric cols [size,gender, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.6370731592178345

Numeric [size, edu] bucket[age] indicator [gender]
Loss nan
Accuracy 0.6341463327407837

All the models had the same accuracies when we tested level 5.

    dataframe['wealthC'] = np.where(dataframe['wealthC']==5, 1, 0)


Numeric cols [size,gender, age, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.4585365951061249

Numeric cols [size,gender, edu] + bucketized cols (age)
- Loss: nan
- Accuracy: 0.4585365951061249

Numeric [size, edu] bucket[age] indicator [gender]
- Loss: nan
- Accuracy: 0.4585365951061249

Overall, our models performed better on predicting lower wealth.
Both Numeric cols [size, gender, age, edu] + bucketized cols (age)
and Numeric cols [size, gender, edu] + bucketized cols (age)
performed better overall than the Numeric [size, edu] bucket[age] indicator [gender]
model.
