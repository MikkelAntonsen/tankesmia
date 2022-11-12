[Source](https://arxiv.org/pdf/2006.07159.pdf)

Imagenet has one label per image and it is not always obvious which object has been labeled for each image.
The authors clean the imagenet validation set and add multiple tags to each image if there are multiple objects that fit.
They make an oracle model that guesses one of the multiple labels that fit. They compare the performance of the oracle to a model trained on imagenet. The model performs better than the oracle (better than random chance), indicating that the model is overfit to some labeling bias in imagenet.

They do some experiments to show that increased performance on regular imagenet validation is correlated with increased performance on the fixed validation set. Over a certian error threshold, the correlation is weaker. The argument is that over this threshold you're making less progress and getting better at fitting noise.
