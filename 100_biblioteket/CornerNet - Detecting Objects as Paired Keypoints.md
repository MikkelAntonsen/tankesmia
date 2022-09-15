[Source](https://arxiv.org/pdf/1808.01244.pdf)

TL and BR corners are detected in different output maps and have to be paired to make boxes. The paper uses the idea of [associative embeddings] which says that the embedding for each corner that belongs to the same object should be similar.
Question: What is an associative embedding and why should the embedding for two similar object corners be close in latent space?
- They will only be close if you use a push/pull loss

