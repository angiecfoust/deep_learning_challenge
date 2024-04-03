# Deep Learning Challenge
<br>
<h2>Background/Challenge Information</h2><br>
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. Using my knowledge of machine learning and neural networks, I used the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup. The overall goal was to create a model with at least 75% accuracy.
<br>
<br>
<h2>Process</h2><br>
After loading the data set into a Pandas DataFrame (using Google Colab), I performed the following preprocessing steps to prepare the data:
* determined the target variable (IS_SUCCESSFUL) and features
* dropped unnecessary columns (EIN and NAME)
* determined cut off values to bin the APPLICATION_TYPE and CLASSIFICATION data
* used 'pd.getdummies' to encode the categorical data
* split the resulting data into training and testing datasets
<br>
Once the data was prepared, I used Keras/TensorFlow to set up a model and define layers. From there the model was compiled, trained, evaluated, and finally exported to an HDF5 file. Subsequent to creating this nuearl network, three attempts were made to improve the accuracy score manually (i.e. choosing on my own which changes to make to both the data set and the Keras model) before opting to run a Keras Tuner to auto-optimize the model. Lastly, I created a final model then compiled, trained, and evaluated the model before exporting to an HDF5 file.
<br>
<br>
<h2>Results</h2><br>
Below is a description and breakdown of the results for each of the included files/neural networks.
<br>
<b>Starter_Code</b>: This was the first predictive model; the specifics for preprocessing are listed above in the Process section.<br>
* Model/Layer details:<br>
    		- Activation: Relu, 80 neurons, 43 input dimensions<br>
    		- Hidden Layer: Relu, 30 neurons<br>
    		- Output Layer: Sigmoid, 1 neuron<br>
    		- 100 epochs<br>
* Results:
  		- Accuracy: 0.729329<br>
  		- Loss: 0.56<br>
  		- Target accuracy not achieved<br>
<br>
<b>AlphabetSoupCharity_Optimization_1</b>: This was the first attempt to improve on the original model.<br>
* Preprocessing Changes:
  - Two additional columns were dropped from the dataset- ORGANIZATION, SPECIAL_CONSIDERATIONS
  - Binning cutoffs were adjusted for APPLICATION_TYPE and CLASSIFICATION columns- < 1000 and < 2000, respectively.
* Model/Layer details:
  - Activation: Tanh, 100 neurons, 32 input dimensions
  - Hidden Layer: Relu, 40 neurons
  - Hidden Layer: Relu, 20 neurons
  - Output Layer: Sigmoid, 1 neuron
  - 100 epochs
* Results:
  - Accuracy: 0.7266
  - Loss: 0.58
  - Target accuracy not achieved; Not an improved model
<br>
<b>AlphabetSoupCharity_Optimization_2</b>: This was the second attempt to improve on the original model.<br>
* Preprocessing Changes:
  - One additional columns was dropped from the dataset- INCOME_AMT
  - Binning cutoffs were adjusted to < 4000 for the CLASSIFICATION column
* Model/Layer details:
  - Activation: Relu, 100 neurons, 32 input dimensions
  - Hidden Layer: Relu, 50 neurons
  - Output Layer: Sigmoid, 1 neuron
  - 150 epochs
* Results:
  - Accuracy: 0.7296
  - Loss: 0.566
  - Target accuracy not achieved; This is a slightly improved model
<br>
<b>AlphabetSoupCharity_Optimization_3</b>: This was the final "manual" attempt to improve on the original model.<br>
* Preprocessing Changes:
  - Three additional columns were dropped from the dataset- ORGANIZATION, SPECIAL_CONSIDERATIONS, INCOME_AMT
* Model/Layer details:
  - Activation: Relu, 80 neurons, 28 input dimensions
  - Hidden Layer: Relu, 80 neurons
  - Hidden Layer: Relu, 40 neurons
  - Output Layer: Sigmoid, 1 neuron
  - 100 epochs
* Results:
  - Accuracy: 0.7264
  - Loss: 0.57
  - Target accuracy not achieved; Not an improved model
<br>
<b>Keras_Tuner_Check</b>: As the previous attempts failed to reach the target accuracy, I opted to use Keras Tuner to define the optimal model.<br>
* Preprocessing Changes:
  - None; the original data preprocessing was used
* Top Identified Model/Layer details:
  - Activation: Relu, 81 neurons, 43 input dimensions
  - Hidden Layer: Relu, 1 neurons
  - Output Layer: Sigmoid, 1 neuron
* Tuner Accuracy Results for top parameters:
  - Accuracy: 0.7345
  - This would still not result in achieving a target accuracy of 75%, but it is an improved model.
<br>
<b>AlphabetSoupCharity_Optimization_FINAL</b>: This model uses the optimization results from the Keras Tuner to attempt to improve on the original model.
* Preprocessing Changes:
  - The intial preprocessing was used.
* Model/Layer details:
  - Activation: Relu, 81 neurons, 43 input dimensions
  - Hidden Layer: Relu, 1 neurons
  - Output Layer: Sigmoid, 1 neuron
  - 100 epochs
* Results:
  - Accuracy: 0.7304
  - Loss: 0.557
  - Target accuracy not achieved; Is an improved model, but not significantly so.
<br>
<br>
<h2>Summary</h2><br>
Unfortunately none of the 5 models created met the 75% accuracy target, however, Keras Tuner was utilized and did come up with a model that resulted in slightly higher accuracy. My recommendation would be to continue making adjustments to the preprocessing to further improve the predictive model.

