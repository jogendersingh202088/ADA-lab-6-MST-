from heapq import heapify, heappush, heappop


class Graph:
    # constructor
    def __init__(self):
        self.adjacency_list = {}

    # method to add edges
    def add_edge(self, v1, v2, w=1):
        if v1 in self.adjacency_list:
            self.adjacency_list[v1].append((v2, w))
        else:
            self.adjacency_list[v1] = [(v2, w)]

        if v2 in self.adjacency_list:
            self.adjacency_list[v2].append((v1, w))
        else:
            self.adjacency_list[v2] = [(v1, w)]

    # method to solve for minimum spanning tree using prims algorithm
    def prims_mst(self):
        vertices = g.adjacency_list.keys()
        total_vertices = len(vertices)  # finding total number of vertices
        source = list(vertices)[0]  # select a source from the vertices

        result = []
        minheap = []

        # adding adjacent nodes of source to min heap
        for neighbour in g.adjacency_list[source]:
            destination = neighbour[0]
            weight = neighbour[1]
            heappush(minheap, (weight, source, destination))  # (w,s,d)

        visited = {source}  # mark source as visited

        while (len(minheap) != 0 and len(result) < total_vertices-1):
            cur_node = heappop(minheap)
            cur_source = cur_node[2]

            # skip the loop if current node is already visited
            if cur_source in visited:
                continue

            result.append((cur_node[1], cur_node[2], cur_node[0]))
            for neighbour in g.adjacency_list[cur_source]:
                destination = neighbour[0]
                weight = neighbour[1]

                # add the neighbour only if it is not already visited
                if destination not in visited:
                    heappush(minheap, (weight, cur_source, destination))

            # Mark current node as visited
            visited.add(cur_source)

        return result

    # method to display the adjacency list
    def display(self):
        for vertex in self.adjacency_list.keys():
            print(f"{vertex} -> {self.adjacency_list[vertex]}")


if __name__ == "__main__":

    num_edges = int(input("Enter number of edges: "))

    print("\nStart entering edges (s,d,w): ")
    edges = [input().split(" ") for i in range(num_edges)]

    # Graph Object
    g = Graph()

    # Adding edges to graph
    for edge in edges:
        v1, v2, w = edge
        g.add_edge(v1, v2, int(w))

    # Finding Minimum spanning Tree using prim's algorithm
    result = g.prims_mst()

    print("\nEdges present in MST in the form (source,destination,weight): ")
    print(result)
