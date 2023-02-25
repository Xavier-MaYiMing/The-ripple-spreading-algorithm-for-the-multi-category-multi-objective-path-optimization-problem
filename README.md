### The Ripple-Spreading Algorithm for the Multi-Category Multi-Objective Path Optimization Problem

The multi-category multi-objective path optimization problems aims to determine all Pareto-optimal paths on a graph with multiple additive and multiplicative weights.

| Variables     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| network       | Dictionary, {node 1: {node 2: [[additive weights], [multiplicative weights]], ...}, ...} |
| s_network     | The network described by a crisp weight on which we conduct the ripple relay race |
| source        | The source node                                              |
| destination   | The destination node                                         |
| nn            | The number of nodes                                          |
| na            | The number of additive weights                               |
| nm            | The number of multiplicative weights                         |
| neighbor      | Dictionary, {node1: [the neighbor nodes of node1], ...}      |
| v             | The ripple-spreading speed (i.e., the minimum length of arcs) |
| t             | The simulated time index                                     |
| nr            | The number of ripples - 1                                    |
| epicenter_set | List, the epicenter node of the i-th ripple is epicenter_set[i] |
| path_set      | List, the path of the i-th ripple from the source node to node i is path_set[i] |
| radius_set    | List, the radius of the i-th ripple is radius_set[i]         |
| active_set    | List, active_set contains all active ripples                 |
| objective_set | List, the objective value of the traveling path of the i-th ripple is objective_set[i] |
| Omega         | Dictionary, Omega[n] = i denotes that ripple i is generated at node n |

#### Example

![image](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-multi-category-multi-objective-path-optimization-problem/blob/main/MCMOPOP.png)

The red number associated with each arc is the additive weight, and the green number is the multiplicative weight.

```python
if __name__ == '__main__':
    test_network = {
        0: {1: [[62], [0.9]], 2: [[44], [0.7]], 3: [[67], [0.6]]},
        1: {0: [[62], [0.9]], 2: [[33], [0.8]], 4: [[52], [0.5]]},
        2: {0: [[44], [0.7]], 1: [[33], [0.8]], 3: [[32], [0.8]], 4: [[52], [0.5]]},
        3: {0: [[67], [0.6]], 2: [[32], [0.8]], 4: [[54], [0.8]]},
        4: {1: [[52], [0.5]], 2: [[52], [0.5]], 3: [[54], [0.8]]},
    }
    source_node = 0
    destination_node = 4
    print(main(test_network, source_node, destination_node))
```

##### Output:

```python
[
    {'path': [0, 2, 4], 'objective': [96, 0.35]}, 
    {'path': [0, 1, 4], 'objective': [114, 0.45]}, 
    {'path': [0, 3, 4], 'objective': [121, 0.48]},
]

```

