**Introduction**

![figure1](https://user-images.githubusercontent.com/98201516/205528928-b0f4023c-002c-48af-9631-15b464f6a0f6.png)

                                                              Figure 1

One simple way to improve the performance of any machine learning algorithm is to train an ensemble of models on the same data and then to take the average of their results. A major downside to this method, however, is that it is very computationally expensive, especially when it comes to deploying it to a large number of users. The process of taking an ensemble of models and the knowledge gained from them and transferring it to a single model is called distillation. These specialist models, unlike a mixture of experts, can be trained rapidly.
To give further background as to the reasoning behind distillation, a cumbersome model
is appropriate to use for training as long as it makes it easier to drive structure from the data. This cumbersome model can refer to an ensemble of separately trained models or a single very large model trained with a strong regularizer such as dropout. Once this cumbersome model is trained, distillation, a different type of training, is then used to transfer the knowledge to a small model that is more suitable for deployment. The overview of this process is pictured in Figure 1. After all, knowledge is just a map from input vectors to output vectors. 

**Distillation**

<img width="163" alt="Figure 2" src="https://user-images.githubusercontent.com/98201516/205529010-bb1cc452-f8b3-40f2-8652-9c64f3bb98a0.png">

                                                               Figure 2

A “softmax” output layer is usually used to produce class probabilities in neural networks. The softmax output layer converts the logit produced for each class into a probability by comparing it with other logits. In figure 2, the formula shows how the class probability, qi, is calculated. T is a temperature that is usually set to 1 but using a higher value produces a softer distribution over classes. A simple way to explain the algorithm behind distillation is that the distilled model is trained on a transfer set and a soft target distribution is used for each case in the transfer set. The soft target distribution is produced by using the cumbersome model with a high temperature in its softmax. The same high temperature is used when training the distilled model. 

**Algorithms for knowledge distillation**

The relationship between a cumbersome model and a distilled model can also be seen as a teacher-student model where the distilled model is learning from the cumbersome model. This section will focus on popular methods used to train student models to acquire knowledge from teacher models. 

**Adversarial distillation**
Adversarial learning is used to train a generator model that learns to generate data samples that very closely resemble the true data distribution. A discriminator modelis then tasked to discriminate between the authentic and synthetic data samples. In the context of knowledge distillation, adversarial learning enables the student and teacher models to learn a better representation of the true data distribution. 

**Multi-Teacher distillation**

<img width="396" alt="Figure3" src="https://user-images.githubusercontent.com/98201516/205529087-446708bd-6e7c-41dd-835f-ab5d3514dfa0.png">

                                                                Figure 3
Multi-teacher distillation refers to the distillation that was discussed earlier: a student model acquires knowledge from multiple different teacher models.

**Cross-Model distillation**

<img width="394" alt="Figure4" src="https://user-images.githubusercontent.com/98201516/205529121-aa22545b-c625-4c09-bde3-e6c7ff3ed6f3.png">

                                                                Figure 4

Figure 4 shows the cross-model distillation training scheme. The diagram demonstrates how the teacher is trained in one modality and its knowledge is distilled into the student which requires knowledge from a different modality. This type of distillation is used most commonly in the visual domain.

**Results**

**10 Segmented Images from the Validation Set**

![ex1](https://user-images.githubusercontent.com/98201516/205533110-9bcced46-adf0-4fb3-be02-fddcbc12e640.png)
![ex2](https://user-images.githubusercontent.com/98201516/205533158-e416ac6c-6f40-45b1-b03b-958e4c09baec.png)
![ex3](https://user-images.githubusercontent.com/98201516/205533168-c38c9363-01f9-4956-afcb-5b5d8856f584.png)
![ex4](https://user-images.githubusercontent.com/98201516/205533189-0c8dc530-a442-4d01-8c5f-243c5b4768b2.png)
![ex5](https://user-images.githubusercontent.com/98201516/205533204-9d277f77-1691-47e9-9a3f-65e458fb4f40.png)
![ex6](https://user-images.githubusercontent.com/98201516/205533217-d1badb70-6e17-41c4-be3a-0a4c3ab2b03b.png)
![ex7](https://user-images.githubusercontent.com/98201516/205533230-c2fddb99-881b-47fb-9bb0-93b2fa1d3598.png)
![ex8](https://user-images.githubusercontent.com/98201516/205533243-99b01fab-bd9a-4a32-8a91-d95f28e23cbc.png)
![ex9](https://user-images.githubusercontent.com/98201516/205533251-07b05d7b-bda3-4943-95ad-be24b0e8e4c7.png)
![ex10](https://user-images.githubusercontent.com/98201516/205533261-73a4be8b-ce31-45ca-b46d-16aedd84af93.png)

**Training and Validation Loss vs Epochs**

![loss](https://user-images.githubusercontent.com/98201516/205533329-4f8569ad-675a-48de-956e-5ec53e8cf177.png)

**Precision and Recall Values**

![precision-recall](https://user-images.githubusercontent.com/98201516/205533346-bfe819d1-b77e-4fe3-9516-10e5fc799e52.png)

