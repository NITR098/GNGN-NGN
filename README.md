# Learning Data Topologies with Neural Networks

# Introduction
There are many varieties of neural networks that have been applied towards feature extraction, Clustering, and Classification. Popular approaches include the Multi-Layer Perceptron(MLP) trained with gradient descent, standard Back Propagation Feed Forward Neural Networks, Auto-Associative Neural Networks(AANN), and Kohonen’s Self Organizing Maps(SOM). The key to most Neural Networks lies in the construction of the hidden layer (or layers). AANN requires more than 1 hidden layer to represent non-linearly separable problems. The number of features extracted by the AANN is equal to the number of nodes in the single standard hidden layer. Usually this layer is kept small to ensure efficient encoding. MLP’s can be seen as implementing a non-linear projection of the feature space in their hidden layer. They must be constructed so that the number of input nodes matches the number of original features (the dimensionality of the data) and the number of output nodes matches the number of pattern classes. The number of hidden nodes in the hidden layer, and the number of hidden layers are problem specific, which does not lend itself to unsupervised learning tasks. Kohonen’s SOM neural network is markedly different from the classic neural network approach. Instead of using a standard feed forward approach, SOM uses Competitive Hebbian Learning to map an input space to a low dimensional representation of the input space. This is by nature a form of feature extraction, since it reduces dimensionality of the input space. Competitive Hebbian Learning is a form of competitive learning where, instead of a winner take all, only the single closest node gets to update scenario, the closest node and its topological neighbors all move towards the input single. Usually, the learning rates for the neighbors are less than that of the closest node.

# Neural Gas Network (NGN)

This network is one of the **Competitive Neural Networks** which tries to learn the abstract topologies of data structure. Neural gas is an artificial neural network, inspired by the self-organizing map and introduced in 1991 by _**Thomas Martinetz**_ and _**Klaus Schulten**_. The neural gas is a simple algorithm for finding optimal data representations based on feature vectors. The algorithm was coined "neural gas" because of the dynamics of the feature vectors during the adaptation process, which distribute themselves like a gas within the data space. This algorithm consists of these steps:
1. Select Input Vector and Initialization. $\omega_i$ is random locations of neurons, $C_{i,j}$ is index of edges between neurons and $t_{i,j}$ is time interval from the last $C_{i,j}$ edge reinforcement where if this parameter exceeds a threshold value, naturally this edge should be broken.
$$ {{\omega_i} \in {\mathbb{R}^n}} , {i = 1,2,...,N} $$
$$ {{C_{i,j}} = 0} , {i,j = 1,2,...,N} $$
$$ {{t_{i,j}} = 0} , {i,j = 1,2,...,N} $$
2. Competion and Ranking : Find the distances between random neurons and data locations and find their ranks (${K_i}$).
3. Adaptation: As known as learning step of algorithm with below rule. $\zeta {e^{ - \left( {\frac{{{K_i}}}{\lambda }} \right)}}$ known as learning rate for neurons.
$${\omega _i}^{new} = {\omega _i}^{old} + \zeta {e^{ - \left( {\frac{{{K_i}}}{\lambda }} \right)}}(x - {\omega _i}^{old}),\forall i = 1,2,...,N$$
4. Creating Links: Create a node between high-rank neurons if there is not a link already.
5. Aging: If neuron $i$ has a $0$ order rank ($K_i = 0$), the age of all edges increases. Therefore, all the edges that have connection with neuron $i$ their age increase.
6. Remove Old Links: If the age between neurons $i$ and $j$ is more than a certain value (Threshold), then that neighborhood should be broken.
$$ {t_{i,j}} > T \to {C_{i,j}} = 0,{C_{j,i}} = 0 $$

# Growing Neural Gas Networks (GNGN)
In 1995, an extended version of Neural Gas, entitled Growing Neural Gas (GNG) network is proposed by _**Bernd Fritzke**_, which begins only with 2 neurons, and the network grows during the execution of the algorithm.


# Datasets
We used Clustering Datasets provided by [**University of Eastern Finland**](http://cs.joensuu.fi/sipu/datasets/).
# References
* Thomas Martinetz and Klaus Schulten, “A neural-gas network learns topologies,” _Elsevier Artificial Neural Networks_, pp.397–402, 1991.
* Bernd Fritzke, “A growing neural gas network learns topologies,” in _Advances in Neural Information Processing Systems_, pp.625–632, 1995.
