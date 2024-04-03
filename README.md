# Deep Learning Challenge
<br>
<h2>Background/Challenge Information</h2><br>
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. Using my knowledge of machine learning and neural networks, I used the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup. The overall goal was to create a model with at least 75% accuracy.
<br>
<br>
<h2>Process</h2>
After loading the data set into a Pandas DataFrame (using Google Colab), I performed the following preprocessing steps to prepare the data:
<br>
<br>
<li>determined the target variable (IS_SUCCESSFUL) and features</li>
<li>dropped unnecessary columns (EIN and NAME)</li>
<li>determined cut off values to bin the APPLICATION_TYPE and CLASSIFICATION data</li>
<li>used 'pd.getdummies' to encode the categorical data</li>
<li>split the resulting data into training and testing datasets</li>
<br>
Once the data was prepared, I used Keras/TensorFlow to set up a model and define layers. From there the model was compiled, trained, evaluated, and finally exported to an HDF5 file. Subsequent to creating this nuearl network, three attempts were made to improve the accuracy score manually (i.e. choosing on my own which changes to make to both the data set and the Keras model) before opting to run a Keras Tuner to auto-optimize the model. Lastly, I created a final model then compiled, trained, and evaluated the model before exporting to an HDF5 file.
<br>
<br>
<h2>File Description & Results of Each Trial</h2>
<h3><b>Starter_Code</b></h3>
This was the first predictive model; the specifics for preprocessing are listed above in the Process section.<br>
<h5>Model/Layer details:</h5>
<li>Activation: Relu, 80 neurons, 43 input dimensions</li>
<li>Hidden Layer: Relu, 30 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<li>100 epochs</li>
<h5>Results:</h5>
<li>Accuracy: 0.729329</li>
<li>Loss: 0.56</li>
<li>Target accuracy not achieved</li>
<br>
<h3><b>AlphabetSoupCharity_Optimization_1</b></h3>
This was the first attempt to improve on the original model.<br>
<h5>Preprocessing Changes:</h5>
<li>Two additional columns were dropped from the dataset- ORGANIZATION, SPECIAL_CONSIDERATIONS</li>
<li>Binning cutoffs were adjusted for APPLICATION_TYPE and CLASSIFICATION columns- < 1000 and < 2000, respectively.</li>
<h5>Model/Layer details:</h5>
<li>Activation: Tanh, 100 neurons, 32 input dimensions</li>
<li>Hidden Layer: Relu, 40 neurons</li>
<li>Hidden Layer: Relu, 20 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<li>100 epochs</li>
<h5>Results:</h5>
<li>Accuracy: 0.7266</li>
<li>Loss: 0.58</li>
<li>Target accuracy not achieved; Not an improved model</li>
<br>
<h3><b>AlphabetSoupCharity_Optimization_2</b></h3>
This was the second attempt to improve on the original model.<br>
<h5>Preprocessing Changes:</h5>
<li>One additional columns was dropped from the dataset- INCOME_AMT</li>
<li>Binning cutoffs were adjusted to < 4000 for the CLASSIFICATION column</li>
<h5>Model/Layer details:</h5>
<li>Activation: Relu, 100 neurons, 32 input dimensions</li>
<li>Hidden Layer: Relu, 50 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<li>150 epochs</li>
<h5>Results:</h5>
<li>Accuracy: 0.7296</li>
<li>Loss: 0.566</li>
<li>Target accuracy not achieved; This is a slightly improved model</li>
<br>
<h3><b>AlphabetSoupCharity_Optimization_3</b></h3>
This was the final "manual" attempt to improve on the original model.<br>
<h5>Preprocessing Changes:</h5>
<li>Three additional columns were dropped from the dataset- ORGANIZATION, SPECIAL_CONSIDERATIONS, INCOME_AMT</li>
<h5>Model/Layer details:</h5>
<li>Activation: Relu, 80 neurons, 28 input dimensions</li>
<li>Hidden Layer: Relu, 80 neurons</li>
<li>Hidden Layer: Relu, 40 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<li>100 epochs</li>
<h5>Results:</h5>
<li>Accuracy: 0.7264</li>
<li>Loss: 0.57</li>
<li>Target accuracy not achieved; Not an improved model</li>
<br>
<h3><b>Keras_Tuner_Check</b></h3>
As the previous attempts failed to reach the target accuracy, I opted to use Keras Tuner to define the optimal model.<br>
<h5>Preprocessing Changes:</h5>
<li>None; the original data preprocessing was used</li>
<h5>Top Identified Model/Layer details:</h5>
<li>Activation: Relu, 81 neurons, 43 input dimensions</li>
<li>Hidden Layer: Relu, 1 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<h5>Tuner Accuracy Results for top parameters:</h5>
<li>Accuracy: 0.7345</li>
<li>This would still not result in achieving a target accuracy of 75%, but it is an improved model.</li>
<br>
<h3><b>AlphabetSoupCharity_Optimization_FINAL</b></h3>
This model uses the optimization results from the Keras Tuner to attempt to improve on the original model.
<h5>Preprocessing Changes:</h5>
<li>The intial preprocessing was used.</li>
<h5>Model/Layer details:</h5>
<li>Activation: Relu, 81 neurons, 43 input dimensions</li>
<li>Hidden Layer: Relu, 1 neurons</li>
<li>Output Layer: Sigmoid, 1 neuron</li>
<li>100 epochs</li>
<h5>Results:</h5>
<li>Accuracy: 0.7304</li>
<li>Loss: 0.557</li>
<li>Target accuracy not achieved; Is an improved model, but not significantly so.</li>
<br>
<h2>Summary</h2>
Unfortunately none of the 5 models created met the 75% accuracy target, however, Keras Tuner was utilized and did come up with a model that resulted in slightly higher accuracy. My recommendation would be to continue making adjustments to the preprocessing to further improve the predictive model.

