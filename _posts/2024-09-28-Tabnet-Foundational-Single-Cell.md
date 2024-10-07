## Architecture


[Tabnet](https://www.youtube.com/watch?v=ysBaZO8YmX8)

Input

Batchnorm Layer: 

Step 1:
Feature Transformer:
Attentive transformer: creates a Mask for the next Feature transformer
Feature transformer: creates predictions with Relu and next features for attentive transformer.

Every step output is then summed for the final process of classification, regression...
You can also use the masks to get information on what the model is selecting for the classification

Feature transformer block: 
- Succesion of 4 consecutive GLU blocks
GLU Block:
- Fully connected layer - Batchnorm - GLU
- GLU is Sigmoid times(bitwise multiplication) input features

There are some shared blocks across all steps and also some independent blocks for each step. 

Attentive transformer
Fully connected - Batch normalization + Sparsemax with prior scales
What's the prior? At the beginning all ones. How much you have used them across the models.
For next steps is going to be gamma - previous usage...
Gamma close to 1 tries to use different features at each step.
Gamma bigger use the same feature. 
Sparsemax is an sparse version of the SoftMax

The more steps the bigger the model
All steps contribute equally to the final mapping layer
Masks can be averaged and give instance wise interpretation
A feature that has been masked a lot has a low importance.

# To be Foundational you need
Label transfer
Batch Integration
Gene perturbation prediction. 

We could add some interpretability with another heatmap. 

#Pretraining - Training by predicting randomly masked features. 

# Can be used with categorical features and embeddings. 
