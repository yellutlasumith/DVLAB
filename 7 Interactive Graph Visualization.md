🔗 Experiment: Interactive Graph Visualization System
🎯 Aim

To design and implement an interactive graph visualization system using Python that allows users to perform basic graph operations such as adding, deleting, and searching nodes and edges.

🛠️ Tools and Technologies Used
🐍 Python 3
📓 Jupyter Notebook
🖼️ Tkinter (GUI)
🌐 NetworkX (Graph Library)
📊 Matplotlib (Visualization)

⚙️ Procedure

Import required libraries (Tkinter, NetworkX, Matplotlib).
Create an initial graph with nodes and edges.
Visualize the graph using a layout algorithm.
Design a GUI with buttons for interaction.
Implement functionality to:
Add nodes
Add edges
Remove nodes
Remove edges
Search nodes
Update and display the graph dynamically after each operation.

1️⃣ Create and Visualize Graph

import tkinter as tk
from tkinter import simpledialog
import networkx as nx
import matplotlib.pyplot as plt

# Create graph
def create_graph():
    G = nx.Graph()
    G.add_edges_from([('A','B'), ('B','C'), ('C','D')])
    return G

# Visualize graph
def visualize_graph(G):
    try:
        print(f"Nodes: {G.nodes()}")
        print(f"Edges: {G.edges()}")

        pos = nx.spring_layout(G)
        plt.figure(figsize=(6,6))
        nx.draw(G, pos,
                with_labels=True,
                node_color='skyblue',
                node_size=2000,
                font_size=14,
                edge_color='gray')
        plt.title("Interactive Graph Visualization")
        plt.show()
    except Exception as e:
        print(f"Error: {e}")

   2️⃣ GUI Design

   def create_gui():
    global root
    root = tk.Tk()
    root.title("Interactive Graph Visualization")

    G = create_graph()

    tk.Button(root, text="Visualize Graph",
              command=lambda: visualize_graph(G)).pack()

    tk.Button(root, text="Add Node",
              command=lambda: add_node(G)).pack()

    tk.Button(root, text="Add Edge",
              command=lambda: add_edge(G)).pack()

    tk.Button(root, text="Remove Node",
              command=lambda: remove_node(G)).pack()

    tk.Button(root, text="Remove Edge",
              command=lambda: remove_edge(G)).pack()

    tk.Button(root, text="Search Node",
              command=lambda: search_node(G)).pack()

    root.mainloop()

if __name__ == "__main__":
    create_gui()

   3️⃣ Add Node

  def add_node(G):
    new_node = simpledialog.askstring("Input", "Enter new node:", parent=root)
    if new_node:
        G.add_node(new_node)
        print(f"Added node {new_node}")
        visualize_graph(G)

4️⃣ Add Edge

def add_edge(G):
    node1 = simpledialog.askstring("Input", "Enter first node:", parent=root)
    node2 = simpledialog.askstring("Input", "Enter second node:", parent=root)

    if node1 and node2:
        G.add_edge(node1, node2)
        print(f"Added edge {node1}-{node2}")
        visualize_graph(G)

5️⃣ Remove Node

def remove_node(G):
    node = simpledialog.askstring("Input", "Enter node to remove:", parent=root)

    if node:
        if node in G:
            G.remove_node(node)
            print(f"Removed node {node}")
            visualize_graph(G)
        else:
            print(f"Node {node} does not exist")

  6️⃣ Remove Edge

  def remove_edge(G):
    node1 = simpledialog.askstring("Input", "Enter first node:", parent=root)
    node2 = simpledialog.askstring("Input", "Enter second node:", parent=root)

    if node1 and node2:
        if G.has_edge(node1, node2):
            G.remove_edge(node1, node2)
            print(f"Removed edge {node1}-{node2}")
            visualize_graph(G)
        else:
            print(f"Edge {node1}-{node2} does not exist")

7️⃣ Search Node

def search_node(G):
    node = simpledialog.askstring("Input", "Enter node to search:", parent=root)

    if node:
        if node in G:
            print(f"Node {node} exists in the graph")
        else:
            print(f"Node {node} not found in the graph")

✅ Result

The interactive graph visualization system was successfully implemented using Python.

Graph operations (add, delete, search) were performed dynamically
GUI provided user-friendly interaction
Visualization updated in real-time

Thus, the objective of designing and implementing an interactive graph visualization system was achieved successfully.            
