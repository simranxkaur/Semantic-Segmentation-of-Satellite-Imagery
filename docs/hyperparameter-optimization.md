**Introduction**

![hyperopt](https://user-images.githubusercontent.com/98201516/202880476-3674ed34-e6f1-45ea-88d7-8baf9e6ccf12.png)

As defined by the “Algorithms for Hyper-Paramter Optimization” paper, Hyper-Parameter Optimization involves optimizing a loss function over a graph-structured configuration space. Traditionally, humans have been able to perform the job of hyper-parameter optimization well but it has come to light that with GPUs and computer clusters being able to run more trials, algorithmic approaches are able to achieve better results. As seen in Figure 1, HyperOpt is a tool that automates the search for optimal hyperparameter configuration based on a Bayesian Optimization and supported by the SMBO methodology. SMBO methods sequentially construct models to approximate the performance of hyperparameters based on historical measurements, and then subsequently choose new hyperparameters to test based on this model. One such SMBO approach is Tree of Parzen Estimators (TPE), which will be the focus of this paper. The TPE approach models P(x|y) and P(y) where x represents hyperparameters and y the associated quality score.

                                          
<img width="284" alt="search space" src="https://user-images.githubusercontent.com/98201516/202880547-6a58b239-8d37-4f56-bb6e-1ada345e67ce.png">


**Algorithm Overview**

1)Define a domain of hyperparameter over which to search.

2)Create an objective function which takes in hyperparameters and outputs a score that needs to be minimized.

3)Get a set of observations using randomly selected set of hyperparameters

4)Take the observations and divide them into two groups based on performance. The first group (x1) has the observations that provided the best score. The second group (x2) has the rest.

5)Two densities l(x1) and g(x2) are modeled using Parzen Estimators (also known as kernel density estimators) which average the kernels centered on existing data points

6)Draw sample hyperparameters from l(x1), evaluating them in terms of l(x1)/g(x2), and returning the set that yields the minimum value under l(x1)/g(x1) (corresponds to greatest improvement). These hyperparameters are then evaluated on the objective function.

7)Update the observation list from step 3

8)Repeat step 4-7 for the number of trials specified

**Conclusion**

<img width="434" alt="results" src="https://user-images.githubusercontent.com/98201516/202880584-5a5f770a-5551-46d3-9a8d-ecf42409a667.png">


As seen in figure 3, the TPE algorithm presented here has uncovered new best results on both of these datasets: convex and mnist rotated background images. The results are significantly better than what DBNs (Deep Belief Networks) were able to achieve in the past. The TPE algorithm is also found to be practical: the hyper parameter optimization for each dataset was done in just 24 hours using five GPU processors. 
	All in all, using a reliable technique, such as TPE, to perform hyperparameter optimization is important. If the hyperparameters are not correctly tuned, the estimated model parameters achieve inadequate results since the loss function is not minimized.

**Results**

(a) Plots of 10 Segmented Images

![ex1](https://user-images.githubusercontent.com/98201516/202880625-6c50f21a-7739-473a-ba27-9bfb4d7a2386.png)

![ex2](https://user-images.githubusercontent.com/98201516/202880628-e6d6d2c2-b360-4cc4-9801-5f725f659e6f.png)

![ex3](https://user-images.githubusercontent.com/98201516/202880630-5381a36d-de48-489e-9d6c-0943d6b4edbb.png)

![ex4](https://user-images.githubusercontent.com/98201516/202880635-106ffb5b-aa9f-400d-be6a-5a8c9e17a0bb.png)

![ex5](https://user-images.githubusercontent.com/98201516/202880641-e2a3a054-32f6-4abc-ba3b-f2991d3f006f.png)

![ex6](https://user-images.githubusercontent.com/98201516/202880643-6fb05dd5-a056-4824-941b-7fd5ffdc3b32.png)

![ex7](https://user-images.githubusercontent.com/98201516/202880650-8a15fa14-8a0e-4eee-9d63-519ac9eaf857.png)

![ex8](https://user-images.githubusercontent.com/98201516/202880654-43343775-2f85-4d4c-afd2-2505b3d74492.png)

![ex9](https://user-images.githubusercontent.com/98201516/202880660-733d8723-4f71-4e21-a8f3-129d39638e42.png)

![ex10](https://user-images.githubusercontent.com/98201516/202880662-e95c0dfa-4d60-4fc0-bde8-e1bee5835308.png)

(b) Training and validation loss vs epochs 

![training loss](https://user-images.githubusercontent.com/98201516/202880666-fe19c549-3fcd-4cc6-bc0f-993c7ae1e235.jpg)

(c) Precision and Recall Values 

![precisionrecall](https://user-images.githubusercontent.com/98201516/202880669-8a6d664c-7e24-492c-a4f7-cdf8f92d300d.jpg)


 
 
 
