Introduction
                                 
Figure 1
	As defined by the “Algorithms for Hyper-Paramter Optimization” paper, Hyper-Parameter Optimization involves optimizing a loss function over a graph-structured configuration space. Traditionally, humans have been able to perform the job of hyper-parameter optimization well but it has come to light that with GPUs and computer clusters being able to run more trials, algorithmic approaches are able to achieve better results. As seen in Figure 1, HyperOpt is a tool that automates the search for optimal hyperparameter configuration based on a Bayesian Optimization and supported by the SMBO methodology.SMBO methods sequentially construct models to approximate the performance of hyperparameters based on historical measurements, and then subsequently choose new hyperparameters to test based on this model. One such SMBO approach is Tree of Parzen Estimators (TPE), which will be the focus of this paper. The TPE approach models P(x|y) and P(y) where x represents hyperparameters and y the associated quality score.

                                          
Figure 2

Algorithm Overview
Define a domain of hyperparameter over which to search.
Create an objective function which takes in hyperparameters and outputs a score that needs to be minimized.
Get a set of observations using randomly selected set of hyperparameters
Take the observations and divide them into two groups based on performance. The first group (x1) has the observations that provided the best score. The second group (x2) has the rest.
Two densities l(x1) and g(x2) are modeled using Parzen Estimators (also known as kernel density estimators) which average the kernels centered on existing data points
Draw sample hyperparameters from l(x1), evaluating them in terms of l(x1)/g(x2), and returning the set that yields the minimum value under l(x1)/g(x1) (corresponds to greatest improvement). These hyperparameters are then evaluated on the objective function.
Update the observation list from step 3
Repeat step 4-7 for the number of trials specified
Conclusion

Figure 3
As seen in figure 3, the TPE algorithm presented here has uncovered new best results on both of these datasets: convex and mnist rotated background images. The results are significantly better than what DBNs (Deep Belief Networks) were able to achieve in the past. The TPE algorithm is also found to be practical: the hyper parameter optimization for each dataset was done in just 24 hours using five GPU processors. 
	All in all, using a reliable technique, such as TPE, to perform hyperparameter optimization is important. If the hyperparameters are not correctly tuned, the estimated model parameters achieve inadequate results since the loss function is not minimized. TPE 

Results

Plots of 10 Segmented Images












Training and validation loss vs epochs 

(c) Precision and Recall Values 



 
