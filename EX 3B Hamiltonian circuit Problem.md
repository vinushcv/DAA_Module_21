# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm
1. Start from each vertex and mark it as visited.
2. Try visiting all other vertices one by one using edges.
3. Use dynamic programming to remember visited sets and paths.
4. If you can visit all vertices exactly once, a Hamiltonian path exists.
5. If no such path is found after checking all options, return "NO".

## Program:
```
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: Vinush CV
Register Number: 212222230176
```
```python
def isSafe(v, pos, path, adj):
    if adj[path[pos-1]][v] == 0:
        return False
    if v in path:
        return False
    return True 
    
def hamPathUtil(path, pos, visited, adj, N):
    if pos == N:
        return True
    for v in range(N):
        if not visited[v] and isSafe(v, pos, path, adj):
            path[pos] = v
            visited[v] = True
            if hamPathUtil(path, pos+1, visited, adj, N):
                return True
            path[pos] = -1
            visited[v] = False
    return False

def Hamiltonian_path(adj, N):
    ######################### Add your Code here ##########################
    path = [-1] * N
    visited = [False] * N
    for start in range(N):
        path[0] = start
        visited[start] = True
        if hamPathUtil(path, 1, visited, adj, N):
            return True
        visited[start] = False
    return False
    
    
    
    
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")

```

## Output:
![image](https://github.com/user-attachments/assets/190b8400-c4ed-42fd-9764-62a113cb4818)



## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
