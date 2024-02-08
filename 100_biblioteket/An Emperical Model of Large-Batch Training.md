202210041159

Status: #idea

Tags:

# An Emperical Model of Large-Batch Training

You train a neural network by moving your parameters along an approximation of the gradient. The gradient you want to approximate is the one of the true distribution. The gradient you access to is the gradient of the whole dataset which is an approximation of the actual gradient.

To train networks faster, you can do an approximation of the full gradient by calculating a gradient on a small batch of the data. A smaller batch leads to more noisy gradients which means you have to take smaller step sizes. A bigger batch takes longer to compute, but you can take longer step sizes.


So what's the optimal batch size?

Idea: jconnect the variance in the gradient to the expected decrease of loss.

This requires the true gradient (of the distribution) and the hessian. This is not feasible so we have to approximate instead.

We can minimize the expected decrease in loss using the estimated gradient with respect to step size, replacing the hessian with a line search.

The derviation gives us a noise scale which says if increasing the the batch size will increase or decrease convergence rate.



---
# References

[Source](https://arxiv.org/pdf/1812.06162.pdf)