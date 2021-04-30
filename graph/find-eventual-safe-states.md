
# Find Eventual Safe States


Type: Graph

### Problem

We start at some node in a directed graph, and every turn, we walk along a directed edge of the graph. If we reach a terminal node (that is, it has no outgoing directed edges), we stop.

We define a starting node to be safe if we must eventually walk to a terminal node. More specifically, there is a natural number k, so that we must have stopped at a terminal node in less than k steps for any choice of where to walk.

Return an array containing all the safe nodes of the graph. The answer should be sorted in ascending order.

The directed graph has n nodes with labels from 0 to n - 1, where n is the length of graph. The graph is given in the following form: graph[i] is a list of labels j such that (i, j) is a directed edge of the graph, going from node i to node j.

Sample 1
```
Input: graph = [[1,2],[2,3],[5],[0],[5],[],[]]
Output: [2,4,5,6]
Explanation: The given graph is shown above.
```
Sample 2
```
Input: graph = [[1,2,3,4],[1,2],[3,4],[0,4],[]]
Output: [4]

```

### Solution

Safe nodes are not part of any cycle. 
A node is safe if it is a leaf or all of its outgoing nodes are safe. 
Run a DFS and keep track of safe and unsafe nodes.

```python
class Solution:
    def dfs(self, graph, node, visited):
        if visited[node] == 3:
            return False
        elif visited[node] == 1:
            return True

        visited[node] = 1
        is_cycle = False

        for nei in graph[node]:
            is_cycle = is_cycle or self.dfs(graph, nei, visited)

        if not is_cycle:
            visited[node] = 3


        return  is_cycle
    
    def eventualSafeNodes(self, graph: List[List[int]]) -> List[int]:
        visited = defaultdict(lambda: 0)
        safe_nodes = []
        for node in range(len(graph)):
            if visited[node] == 0:
                self.dfs(graph, node,visited)

        for node in range(len(graph)):
            if visited[node]==3:
                safe_nodes.append(node)

        return safe_node
```
