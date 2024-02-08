202305061550

Status: #idea

Tags:

# Calibrated Chaos - Variance between Runs of Neural Netowkr Training is Harmless and Inevitable


###

$C_{x, y}(\theta) = 1$  given $f_{\theta}(x)=\bar{y}$  iff $y==\bar{y}$
 - C is an indicator function for if $f_{\theta}$ gets sample x right

$\bar{C}_{x,y}=\mathbb{E}_{\theta \sim A}[C_{x,y}(\theta)]$

### Variance in test-set peformance
Variance is inevitable and is a result of random chance (test set being sampled from a test-set distribution. Performance on the distribution is the same). They show this by splitting the test set in two and showing that high performance on one half is not indicative of high performance on the other half. Since the peformance on the two sets are uncorrelated, we would also expect the performance on the entire test set to be uncorrelated with the rest of the test distribution.

But there has to be some correlation, if not, what's the point of using the test set?

What would the performance between the two sets being collerated tell us? 


### Variance is primarely caused by ANN training being a chaotic system

Variance is primarely caused by training being extremely sensitive to initial conditions. Changing the first batch, "poking" or changing one weight, having the first batch be 32 vs 64 fp, causes as much variance as completely different inits.

### Consequences

If we can't train a massive amount of models, how can we select a model based on test set performance?
How can we know if a new model is better than the old?






---
# References