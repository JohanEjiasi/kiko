# kiko

Collaborative filtering is a technique used by recommender systems to forecast a user's interests by compiling data on their tastes or preferences from a large number of other users. Collaborative filtering works under the premise that if two users A and B share the same preferences or viewpoints, then A is more likely to share B's viewpoints on unrelated topics.

In this project, I estimate user ratings based on the user's preferences and the preferences of other users who have seen and rated the same or comparable movies.



## Datasets

The current version support only the MovieLens ml-1m.zip dataset obtained from https://grouplens.org/datasets/movielens/. 

## Model Training

- Download the ml-1m.zip dataset from  https://grouplens.org/datasets/movielens/.
- Devide the ```ratings.dat``` file from ml-1m.zip into training and testing datasets ```train.dat``` and ```test.dat```. by using the command 

       python src\data\train_test_split.py 
          
- Use shell to make TF_Record files out of the both ```train.dat``` and ```test.dat``` files by executing the command: 

       python src\data\tf_record_writer.py 
      
- Use shell to start the training by executing the command (optionally parse your hyperparameters):

        python training.py 

### Training Results 

The loss on the training and testing data sets is displayed at the end of each epoch during training. A root mean squared error loss (MSE) has occurred. However, a better metric to verify performance is the mean absolute error (mean_abs_error).The gap between genuine and anticipated ratings is revealed by mean_abs_error. For instance, a mean_abs_error of 0.923 indicates that, on average, the projected rating differs by 0.923 stars from the actual rating.

       epoch_nr: 0, train_loss: 1.421, test_loss: 0.967, mean_abs_error: 0.801
       epoch_nr: 1, train_loss: 0.992, test_loss: 0.961, mean_abs_error: 0.797
       epoch_nr: 2, train_loss: 0.987, test_loss: 0.962, mean_abs_error: 0.798
       epoch_nr: 3, train_loss: 0.981, test_loss: 0.965, mean_abs_error: 0.801
       epoch_nr: 4, train_loss: 0.969, test_loss: 0.974, mean_abs_error: 0.808
       epoch_nr: 5, train_loss: 0.949, test_loss: 0.988, mean_abs_error: 0.822
