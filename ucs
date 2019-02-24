In [12]:
import copy
import Queue as Q

class Graph:

# graph dictonary contains all the adjacent nodes of each as key and value pair
# cost_dict contains cost of each edge traversal of (u,v)
# final_dict contains all the possible paths from start node s to goal node g with total cost
def __init__(self):
    self.graph = dict()
    self.cost_dict=dict()
    self.final_dict=dict()

# u and v are nodes: edge u-->v with cost c 
def addEdge(self,u,v,c):
    
    if u not in self.graph:
        qu = Q.PriorityQueue()
        self.graph.update({u:qu})

    self.graph[u].put(v)
    self.cost_dict.update({(u,v):c})
    
# Makes a list to keep track of visited nodes
def tnode(self,n):
    self.visited = [False]*n


def UCS_util(self,s,visited,path,goal,value):
    # Appending node to the current path 
    path.append(s)
    # Marking that node is visited 
    visited[s]=True
    
    # If goal node is reached save the path and return
    if goal==s:
        self.final_dict.update({tuple(path):value})
        return
    
    # Checking if the adjacent node is been visited and explore the new path if haven't
    for i in self.graph[s].queue:
        if visited[i]==False:
            # When new path is being explored add the cost of that path to cost of entire course traversal
            # Send a copy of path list to avoid sending it by reference
            self.UCS_util(i,copy.deepcopy(visited),copy.deepcopy(path),goal,value + self.cost_dict[s,i])

def UCS(self, s,goal):
    self.visited[s] = True
    # List to hold all the nodes visited in path from start node to goal node 
    path=[s]
    
    for i in self.graph[s].queue:
        if self.visited[i] == False:
            # Make a variable to hold the cost of traversal
            value = self.cost_dict[s,i]
            self.UCS_util(i,copy.deepcopy(self.visited),copy.deepcopy(path),goal,value)

# Display all the paths that is been discovered from start node to Goal node
def all_paths(self):
    # Check if there is any path
    if bool(self.final_dict):
        print("All the paths: ")
        for i in self.final_dict:
            print "path: ",i,"cost: ",self.final_dict[i]
    else:
        print "No Path exist between start and goal node"

# Find the most optimal path between start node to goal node
def optimal_path(self):
    if bool(self.final_dict):
        print "best path: ",min(self.final_dict, key=self.final_dict.get)
    else:
        print "No Path exist between start and goal node"
#Creating Graph object and assigning number of nodes
g = Graph()
g.tnode(10)

#Making the Graph
g.addEdge(0, 1, 1); g.addEdge(0, 2, 1); g.addEdge(1, 3, 3);
g.addEdge(2, 5, 2); g.addEdge(3, 6, 4); g.addEdge(3, 5, 2);
g.addEdge(4, 6, 1); g.addEdge(4, 7, 5); g.addEdge(5, 4, 4);
g.addEdge(6, 7, 1); g.addEdge(5, 0, 3); g.addEdge(5, 8, 1);
g.addEdge(8, 4, 1); g.addEdge(8, 9, 3); g.addEdge(9, 7, 1);

#0 is start node and 7 is goal node
g.UCS(0,7)

#Find all the path between 0 and 7
g.all_paths()

#Find the most optimal path between 0 and 7
g.optimal_path()
  File "<ipython-input-12-8912fbf9e066>", line 9
    def __init__(self):
      ^
IndentationError: expected an indented block
In [14]:
class UniformCost:
    def __init__(self, initial_state, actions, result, goal_test, get_cost):
        self.f = []
        self.e = []
        self.res = []
        self.visited = []
        self.initial_state = initial_state
        self.actions = actions
        self.result = result
        self.goal_test = goal_test
        self.get_cost = get_cost
        self.max_memory = 0

    def search(self):
        while self.f:
            self.max_memory = max(self.max_memory, len(self.f) + len(self.e))
            x = self.f[0]
            minv = x[1]
            path = x[0]
            udru = x[2]
            for v in self.f:
                if v[1] < minv:
                    minv = v[1]
                    path = v[0]
                    udru = v[2]
            node = path[-1]
            for v in self.f:
                p = v[0]
                if p[-1] == node and v[1] > minv:
                    self.f.remove(v)

            if self.goal_test(node):
                return [udru, path, minv]

            self.f.remove([path, minv, udru])
            if node not in self.e:
                self.e.append(node)

            for act in self.actions(node):
                v = self.result(node, act)
                if v not in self.e:
                    c = self.get_cost(node, v) + minv
                    path2 = []
                    for p in path:
                        path2.append(p)
                    path2.append(v)
                    udru2 = []
                    for m in udru:
                        udru2.append(m)
                    udru2.append(act)
                    self.f.append([path2, c, udru2])
                    if v not in self.visited:
                        self.visited.append(v)


    def search_uniform(self):
        start = self.initial_state()
        self.f = [[[start], 0, []]]
        self.e = []
        self.res = []
        self.visited = [start]
        p = self.search()
        if not p:
            print("there is no path")
        else:
            print("path found: ")
            print(p[0])
            print("num visited: ", len(self.visited))
            print("num closed list: ", len(self.e))
            print("max memory use: ", self.max_memory)
            print("path cost : ", p[2])
In [ ]:
