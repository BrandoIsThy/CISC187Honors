### https://studio.youtube.com/video/KmSesnEIMuw/edit

1) create a theoretical graph
ij![image](https://github.com/user-attachments/assets/dbe382bf-888b-4c69-806a-080b4837dffe)

2) code for first creating the graph and BFS + DFS. Had to do alot of external research for queue and stack, but more for queue
```
#include <iostream>
#include <vector>
#include <stack>
#include <queue>
using namespace std;

struct Graph {
    int vertices;
    vector<vector<int>> adjList; //did some outside research, because every point is connected to every other in my example,
    // a vector of a vector makes it that the vector adjList, stores vectors representing
    // each node,and each node has vectors,representing the vertices of the node. So like,
    // <adjList[1]<2,3,4>, adjList[2]<1,3,4>, adjList[3]<2,1,4>, adjList[4]<2,3,1>> i think

    Graph(int input) {
        vertices = input;
        adjList.resize(vertices); // Resize to match the number of vertices
    }

    void addEdge(int x, int y) {
        adjList[x].push_back(y); // Create edge from x to y
        adjList[y].push_back(x); // Create edge from y to x (since the graph is undirected)
    }

    void print() {
        for (int i = 0; i < vertices; ++i) { // Loop through all vertices
            cout << "Vertex " << i << ": ";
            for (int j = 0; j < adjList[i].size(); ++j) {
                cout << adjList[i][j] << " "; // Print each neighbor of vertex i
            }
            cout << endl;
        }
    }

    // Depth First Search (DFS) using stack
    void dfs(int start) {
        vector<bool> visited(vertices, false); // Initialize the visited array
        stack<int> s;  // Stack for DFS
        s.push(start); // Push the starting vertex to the stack
        visited[start] = true; // Mark it as visited

        while (!s.empty()) {
            int vertex = s.top(); // Get the current vertex
            s.pop(); // Pop it from the stack

            // Print the current vertex only once
            cout << vertex << " : ";

            // Print its neighbors
            for (int i = 0; i < adjList[vertex].size(); ++i) {
                int adj = adjList[vertex][i];
                if (!visited[adj]) { // If the neighbor is not visited
                    visited[adj] = true; // Mark the neighbor as visited
                    s.push(adj); // Push it to the stack for further exploration
                }
                cout << adj << " "; // Print each neighbor for the current vertex
            }
            cout << endl;
        }
    }

    // Breadth First Search (BFS) using queue
    void bfs(int start) {
        vector<bool> visited(vertices, false); // Initialize the visited array
        queue<int> q;  // Queue for BFS
        q.push(start); // Push the starting vertex to the queue
        visited[start] = true; // Mark it as visited

        while (!q.empty()) {
            int vertex = q.front(); // Get the current vertex
            q.pop(); // Pop it from the queue

            // Print the current vertex only once
            cout << vertex << " : ";

            // Print its neighbors
            for (int i = 0; i < adjList[vertex].size(); ++i) {
                int adj = adjList[vertex][i];
                if (!visited[adj]) { // If the neighbor is not visited
                    visited[adj] = true; // Mark the neighbor as visited
                    q.push(adj); // Push it to the queue for further exploration
                }
                cout << adj << " "; // Print each neighbor for the current vertex
            }
            cout << endl;
        }
    }
};

int main() {
    Graph graph(4);  // Create a graph with 4 vertices: 0, 1, 2, 3

    // Adding edges to form a complete graph (every vertex connected to every other)
    graph.addEdge(0, 1); // Add edge between 0 and 1
    graph.addEdge(0, 2); // Add edge between 0 and 2
    graph.addEdge(0, 3); // Add edge between 0 and 3
    graph.addEdge(1, 2); // Add edge between 1 and 2
    graph.addEdge(1, 3); // Add edge between 1 and 3
    graph.addEdge(2, 3); // Add edge between 2 and 3

    // Print the adjacency list of the graph
    graph.print();

cout <<"BFS: " << endl;
        graph.dfs(0); // Perform DFS from each vertex
    cout <<"DFS: " << endl;
        graph.bfs(0); // Perform BFS from each vertex



}

```
code for the dfs and bfs:

3) Comparing Big O:
  since both use a vector in a vector and a double for loop to read each vector + the vectors that vector holds, both are O(n^2)

   
