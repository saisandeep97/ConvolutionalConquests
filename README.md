# ConvolutionalConquests
Implementation and comparative study of AllConvNets

## Experiment -1 (A basic CNN)
An architecture with Convolution layers and pooling layers followed by fully-connected layers is considered for this experiment. 
Code- 
![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/47a477f6-d261-488b-bf00-d8a370c14176)
Instead of implementing all the methods from scratch, BaselineModel is inherited as a parent class and necessary methods are overridden. 
No of trainable parameters – 2.1 M
Maxepochs is not set but early stopping callback is used  with patience 5. The following metrics are obtained on validation and test set- 
Best epoch – Epoch 4
Best validation loss 1.31
Test loss: 1.35
Test Accuracy: 57%

## Experiment -2 (AllConvNet)
Refer to the paper - https://ieeexplore.ieee.org/document/9129362
The paper on all conv net discusses three different architectures out of which we tried implementing model C. 
Code – 
![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/6a61a265-c9d3-46b0-a9a8-be8bda2c2972)

Forward pass- 
                   ![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/31eb2ebe-9581-484a-9590-b4b16da19b52)
                         
No of trainable parameters – 1.4  M
The following metrics are obtained on validation and test set- 
Best epoch – Epoch 34
Best validation loss 1.96
Test loss: 1.98
Test Accuracy: 47%

Comparison of basic CNN vs AllConvNet – While no of parameters for AllConvNet is significantly less than basic CNN, the accuracy for basic CNN is higher than AllConvNet in  this case.

## Experiment -3 (Basic CNN + Regularization)
We chose basic CNN from the above as it gave better performance than AllConvNet. Now we can add dropouts to our network or modify the transform pipeline to include data augmentation as part of training data. Here we choose to add dropouts for simplicity.  Following is the updated architecture after adding dropout – 
 ![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/82af3ea9-cf31-41b9-8c97-a846f1851780)
The remaining code is the same as basic CNN (experiment -1)
Comparison – 
![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/302ee527-2051-44e1-965c-b75bbb524e0f)

We can observe that the model with dropout included converged must faster compared to a model with no dropout. However, the accuracy is slightly on the lower side. 

## Experiment -4 (Cifar-10 +Transfer learning on CNN + Dropout model)
The same transformation steps as Imagenette are performed for CIFAR-10 downloaded dataset. 
 ![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/bca21ecf-2d60-4828-82c4-c0a3f0836081)
Now, a model from scratch is trained using CNN with dropout architecture.
  ![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/5d895fbc-9966-45a5-9772-644a241d70cc)
For the second part of the experiment, to implement transfer learning, a previously trained CNN with dropout architecture model is imported and trained on cifar -10 dataset as follows – 
![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/1124d4a4-7007-48d3-87f4-49f9417817e0)

Results obtained – 
 ![image](https://github.com/saisandeep97/ConvolutionalConquests/assets/26761365/581bfcd3-1386-400b-86f3-27297820dd51)

## Conclusion – 
The pre-trained model although has slightly less accuracy compared to the model that was trained from scratch, converged a lot quicker and had decent accuracy. 

