[source](https://arxiv.org/abs/2207.04186)

# Idea
Randomly sample boxes on an image and create an augmented version of the image+boxes.
Train a network to maximize the representation of the corresponding boxes between the two images using a SSL loss.

They also construct two different auxilliary tasks, predicting box coordinates and predicting boxes from the sampled set using contrastive loss?

# Contrastive loss on classification vs detection

On object classification we're trying to make two images have the same representation, but in object detection the representation has change (in the global view). Therefore you'd want to compare the boxes directly (local view) for contrastive loss.

We could learn to find the same points in two augmented views, but we don't know where to put them in the output (centernet has 80 different outputs for heatmaps).
Idea: Can be do a random projection from the last feature layer to a 1 dimensional heatmap for each point? To disentangle the classification of a point from it's positional encoding in the output.
Could we do a random projection from the penultimate layer to the heatmap and do a contrastive loss in an area of the heatmap?
Could we do a contrastive loss for the whole heatmap?
Could we do a loss by predicting the augmentation (predicting the parameters of transformation (angle/scale etc))?