202301211614

Status: #idea

Tags:

# Google finetuning playbook

This readme is a good resource for markup!

### Before starting

The article assumes that "enough" of data cleaning and problem formulation has been done, that there is a pipeline set up for training and validation, that it is easy train and validate, that appropriate metrics have been chosen and implemented.

1. Problem formulation and data cleaning
2. Make it easy to train/validate
3. Choose and implement metrics

### Optimizers

ADAM has 4 hyperparameters and _you_ should optimize _all_ of them.


### Batch size

All batch sizes are equivalent given that all hyperparameters are properly tuned (particularly regularization and optimizier hyperparameters). Batch size is exclusively chosen based on increasing throughput.

1. Measure throughput - batch size * batches_per_second
2. Increase batch size, observe throughput increases accordingly
3. Address I/O or sync bottlenecks if throughput does not increase as expected.

Interestingly, this implies that gradient accumulation is fucking stupid (my words, not theirs)



---
# References

https://github.com/google-research/tuning_playbook#guide-for-starting-a-new-project