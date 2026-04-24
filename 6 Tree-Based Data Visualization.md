🌳 Experiment: Hierarchical Data Visualization using Tree-Based Techniques
🎯 Aim

To analyze hierarchical data and visualize parent–child relationships using tree-based data visualization techniques in order to gain meaningful structural insights.

⚙️ Procedure
Prepare a dataset in hierarchical format (Parent → Child relationships).
Construct a tree structure with multiple levels (Root → Category → Subcategory → Item).
Use Node–Link Diagram to represent relationships between nodes.
Generate a Treemap to visualize proportional distribution within the hierarchy.
Create a Sunburst Chart to display multi-level relationships in a radial format.
Analyze the structure and relationships among nodes.

import pandas as pd
import networkx as nx
import matplotlib.pyplot as plt

data = {
    "Parent": ["A", "A", "B", "B"],
    "Child": ["B", "C", "D", "E"]
}

df = pd.DataFrame(data)

G = nx.from_pandas_edgelist(df, 'Parent', 'Child')
pos = nx.spring_layout(G)

nx.draw(G, pos,
        with_labels=True,
        node_color='grey',
        node_size=3000,
        font_size=17)

plt.title("Tree from dataset - URK24CS7097")
plt.show()

import plotly.graph_objects as go
import networkx as nx

G = nx.Graph()
G.add_edge("Root", "Branch1")
G.add_edge("Root", "Branch2")
G.add_edge("Branch1", "Leaf1")
G.add_edge("Branch1", "Leaf2")
G.add_edge("Branch2", "Leaf3")
G.add_edge("Branch2", "Leaf4")

pos = nx.spring_layout(G)

edge_x, edge_y = [], []
for edge in G.edges():
    x0, y0 = pos[edge[0]]
    x1, y1 = pos[edge[1]]
    edge_x.extend([x0, x1, None])
    edge_y.extend([y0, y1, None])

edge_trace = go.Scatter(x=edge_x, y=edge_y, mode='lines')

node_x, node_y, labels = [], [], []
for node in G.nodes():
    x, y = pos[node]
    node_x.append(x)
    node_y.append(y)
    labels.append(node)

node_trace = go.Scatter(
    x=node_x,
    y=node_y,
    mode='markers+text',
    text=labels,
    textposition="top center",
    marker=dict(size=20)
)

fig = go.Figure(data=[edge_trace, node_trace])
fig.update_layout(title="Interactive Tree Explorer - URK24CS7097")
fig.show()

import plotly.express as px
import pandas as pd

data = {
    "Category": ["Furniture", "Furniture", "Technology", "Technology"],
    "Subcategory": ["Chairs", "Tables", "Phones", "Accessories"],
    "Product": ["Executive Chair", "Study Table", "iPhone 13", "Keyboard"],
    "Sales": [5000, 3000, 7000, 1500]
}

df = pd.DataFrame(data)

treemap = px.treemap(
    df,
    path=["Category", "Subcategory", "Product"],
    values="Sales",
    title="Treemap of Product Sales"
)

treemap.show()

import plotly.express as px

sunburst = px.sunburst(
    df,
    path=["Category", "Subcategory", "Product"],
    values="Sales",
    title="Sunburst Chart of Hierarchical Data"
)

sunburst.show()

✅ Result

The experiment was successfully performed using tree-based visualization techniques.

Hierarchical relationships were clearly represented
Structural insights were effectively obtained
Multiple visualization methods provided different perspectives of the same data

Thus, the objective of analyzing hierarchical data using tree-based visualization techniques was achieved successfully.
