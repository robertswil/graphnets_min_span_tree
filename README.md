# graph_nets example

### GNNs and graph_nets
Graph neural networks (GNNs) are a neural framework for making predictions on graph data, and have been around a little while. But in [this paper](https://arxiv.org/abs/1806.01261) Deepmind recently presented a new, highly parameter-efficient GNN architecture called the graph network, and it's a pretty big advancement. It uses a series of message-passing blocks between an encoder and decoder to make any combination of node, edge, and/or graph predictions. They recently released an accompanying [Python package called graph_nets](https://github.com/deepmind/graph_nets) that's built on top of [Sonnet](https://github.com/deepmind/sonnet). 

### This example
This repo is my sandbox for implementing a simple toy problem. I use [networkx](https://networkx.org/) to generate batches of random graphs according to the [GNP algorithm](https://en.wikipedia.org/wiki/Erd%C5%91s%E2%80%93R%C3%A9nyi_model). Then, I set the training target to be the total edge length of the minimum spanning tree. To make the problem harder for the learner (although it's still pretty easy), I randomized the size and connectivity of the graph, and edge weights are drawn from a random log-normal. The model is super efficient: log-cosh loss goes to near zero after 1,000 batches (batch size=32), for a MAPE ~1%.
