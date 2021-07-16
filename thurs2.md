# Beans and Eurosat Image Training

## Beans

When I trained the beans dataset, I got some interesting outputs. 

    loss: 0.8523 - accuracy: 0.6336 - val_loss: 0.7224 - val_accuracy: 0.7212

My accuracy was about 63%, and my val_accuracy was around 72%. This
is an okay performance for a dataset with only about 1,300 images
to use. 1,034 of those images were used for training, 128 for 
testing, and 133 for validation. I believe that if we had more 
images in all 3 datasets, the accuracy would have been higher.

## Eurosat 

These were the outputs I got when I trained the eurosat dataset:

    loss: 0.7017 - accuracy: 0.7433 - val_loss: 0.5920 - val_accuracy: 0.7811

Both the accuracy and the val_accuracy were higher in this case. I
think that this is because there were 27,000 samples in this dataset.
80% of that was for training (so 21,600), 10% were for testing (2,700),
and 10% were for validation (also 2,700). Having more samples 
means that the model has more of a chance to generalize and 
predict the testing/validation images better.

## Image Augmentation

## Beans

My accuracies after image augmentation on the beans dataset 
are both lower than the 
original accuracies. I chose the second option of creating 
a random generator. 

    loss: 1.0987 - accuracy: 0.3325 - val_loss: 1.0992 - val_accuracy: 0.3077

I was able to run 3 epochs, and it took around 12 minutes. 

## Eurosat

My accuracies for the eurosat dataset were also significantly
lower than the original ones:

    loss: 1.8328 - accuracy: 0.2973 - val_loss: 1.6687 - val_accuracy: 0.3489

I also ran 3 epochs, with a total of about 5 minutes. 

In conclusion, the image augmentation using the random generator
method did not help the model, in fact, it hurt the model.





