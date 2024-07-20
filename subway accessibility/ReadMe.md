# Subway Accessibility -- The Centrality Measure Based on `Netwrokx`

- I learn this from the `networkx` online video [^1: [图机器学习NetworkX代码实战-创建图和可视化_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1kM41147zV/?spm_id_from=333.999.0.0&vd_source=2b9e0f17be3c1cacca4a47dcc2f3b36e)], which is the translated version of Standford course CS224W (Graphical Machine Learning)
- For the coding part, I use `python` jupyter notebook
- I use the **Beijing** subway as an example try, while the website offers some processes for the **Shanghai** subway

## Brief Note for `graph data mining` learning

### Introduction

- Components of a Network
  - Objects: nodes, vertices
  - Interactions: links, edges
  - System: network, graph
- Directed vs. Undirected Graphs
  - Undirected
    - node degree - the # of edges adjacent to node i
    - avg. degree: $$\bar{k}=\frac{1}{N}\sum_{i=1}^N k_i=\dfrac{2E}{N}$$
  - Directed
    - in-degree
    - out-degree
    - $$\bar{k}=\frac{1}{N}\sum_{i=1}^N k_i=\dfrac{E}{N}$$
  - Bipartite graph
  - Folded/Projected Bipaetite Graphs
  - Ontology
  - Adjacency Matrix
  - Networks are Sparse Graphs
    - Edge list
    - Adjacency list

### Centrality Evaluation

- Node Degree

- Eigenvector centrality

  - a node $$v$$ is important if surrounded by important neighboring nodes $$u\in N(v)$$
  - centrality: $$c_v=\dfrac{1}{\lambda}\sum_{u\in N(v)}c_u$$
    - $$\lambda$$ is normalization constant - will be the largest eigenvalue of A
  - recursive manner
  - solution: $$\lambda c=Ac$$
    - $$A$$ is the adjacency matrix
    - $$A_{uv} =1$$  if $$u\in N(v)$$
    - $$c$$ is the eigenvector of $$A$$
    - Perron-Frobenius Theorem: always exist $$\lambda_{max}$$ → $$c_{max}$$

- Betweenness Centrality

  - A node is important if it lies on the shortest paths between other nodes


    $$ c_v=\sum_{s\ne v\ne t}\dfrac{\text{\#(shortest paths between s and t that contain v)}}{\text{\#(shortest paths between s and t)}} $$
    

- Closeness Centrality

  - A node if important if it has smallest shortest path lengths to all other nodes


    $$ c_v=\dfrac{1}{\sum_{u\ne v}\text{shortest path length between u and v}} $$
    

### Node Features

- Node Degree

- Clustering Coefficient

  - Measures how connected $$v$$’s neighboring nodes are
 

    $$ e_v=\dfrac{\#\text{edges among neighboring nodes}}{\begin{pmatrix} k_v\\ 2 \end{pmatrix}}\in[0,1] $$


- Graphlets

  - Graphlet Degree Vector (GDV): a count vector of graphlets rooted at a given node



## Using Beijing subway as an example

- Timing data source [首末车时间 | 北京地铁官方网站](https://www.bjsubway.com/station/smcsj/)
- I tried for node/degree centrality, eigenvector centrality (not converge), betweenness centrality, closeness centrality, and page rank to attain the centrality measure for the Beijing subway

- Coding language: python

- Core module: `networkx`

- Available data for replication: Beijing subway station timing information in 2024

  - One sight for the original data I manually copied from the website (very tiring work!)

    | station1   | starttime | line |
    | ---------- | --------- | ---- |
    | 古城       | 22:51     | 1    |
    | 八角游乐园 | 22:54     | 1    |
    | 八宝山     | 22:57     | 1    |
    | 玉泉路     | 22:59     | 1    |
    | 五棵松     | 23:02     | 1    |
    | 万寿路     | 23:05     | 1    |
    | 公主坟     | 23:07     | 1    |
    | 军事博物馆 | 23:10     | 1    |
    | 木樨地     | 23:12     | 1    |

  - You can image the first step is to generate the arrived station (station 2)



[^1[图机器学习NetworkX代码实战-创建图和可视化_哔哩哔哩_bilibili]: https://www.bilibili.com/video/BV1kM41147zV/?spm_id_from=333.999.0.0&vd_source=2b9e0f17be3c1cacca4a47dcc2f3b36e
