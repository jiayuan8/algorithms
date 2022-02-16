## All Pair Shortest Path

- Floyd-Warshall algorithm

```python
def shortest_path(n, e):
            dist = [[n + 1 for i in range(n)] for j in range(n)]
            for i in range(n):
                dist[i][i] = 0
            for s, t in e:
                dist[s - 1][t - 1] = 1
                dist[t - 1][s - 1] = 1
            for k in range(n):
                for i in range(n):
                    for j in range(n):
                        if dist[i][j] > dist[i][k] + dist[k][j]:
                            dist[i][j] = dist[i][k] + dist[k][j]
                            
            return dist
```

- - Time Complexity: $O(V^3)$
  - Space Complexity: $O(V^2)$

