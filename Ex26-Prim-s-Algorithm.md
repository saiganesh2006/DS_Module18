# Ex26 Prim’s Algorithm
## DATE:
## AIM:
To write a C program to implement Prim's Algorithm for finding Total Cost of tree.

## Algorithm
1. Define constants infinity = 9999 and MAX = 20; declare global matrices G[MAX][MAX], spanning[MAX][MAX], and integer n.
2. In main(), read the number of vertices n and input the adjacency matrix G[i][j] using scanf.
3. In prims() function, convert G to cost[][] by replacing 0s with infinity; initialize arrays visited[], distance[], and from[].
4. For n-1 edges, find the minimum unvisited vertex, add the edge to spanning[][], update distance[], and mark the vertex as visited.
5. Print the spanning[][] matrix and the total cost computed by prims().

## Program:
```
/*
Program to implement Prim's Algorithm
Developed by: D.B.V.SAI GANESH
RegisterNumber: 212223240025
#include<stdio.h>
#include<stdlib.h>
 
#define infinity 9999
#define MAX 20
 
int G[MAX][MAX],spanning[MAX][MAX],n;
 
int prims();
 
int main()
{
int i,j,total_cost;
scanf("%d",&n);
for(i=0;i<n;i++)
for(j=0;j<n;j++)
scanf("%d",&G[i][j]);
total_cost=prims();

for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
printf("%d ",spanning[i][j]);
printf("\n");
}
printf("\nTotal cost of spanning tree=%d",total_cost);
return 0;
}
 
int prims()
{
int cost[MAX][MAX];
int u,v,min_distance,distance[MAX],from[MAX];
int visited[MAX],no_of_edges,i,min_cost,j;
//create cost[][] matrix,spanning[][]
for(i=0;i<n;i++)
for(j=0;j<n;j++)
{
if(G[i][j]==0)
cost[i][j]=infinity;
else
cost[i][j]=G[i][j];
spanning[i][j]=0;
}
//initialise visited[],distance[] and from[]
distance[0]=0;
visited[0]=1;
for(i=1;i<n;i++)
{
distance[i]=cost[0][i];
from[i]=0;
visited[i]=0;
}
min_cost=0; //cost of spanning tree
no_of_edges=n-1; //no. of edges to be added
while(no_of_edges>0)
{
//find the vertex at minimum distance from the tree
min_distance=infinity;
for(i=1;i<n;i++)
if(visited[i]==0&&distance[i]<min_distance)
{
v=i;
min_distance=distance[i];
}
u=from[v];
//insert the edge in spanning tree
spanning[u][v]=distance[v];
spanning[v][u]=distance[v];
no_of_edges--;
visited[v]=1;
//updated the distance[] array
for(i=1;i<n;i++)
if(visited[i]==0&&cost[i][v]<distance[i])
{
distance[i]=cost[i][v];
from[i]=v;
}
min_cost=min_cost+cost[u][v];
}
return(min_cost);
}
```

## Output:

![image](https://github.com/user-attachments/assets/488f232f-3432-4409-a2a6-b5517345b396)


## Result:
Thus, the C program to implement Prim's Algorithm for finding Total Cost of tree is implemented successfully.
