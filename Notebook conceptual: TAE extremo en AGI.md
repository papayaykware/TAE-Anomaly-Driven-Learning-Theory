# ===========================================
# Notebook conceptual: TAE extremo en AGI
# Autolocalización causal y emergencia de intencionalidad
# ===========================================

# Importación de librerías básicas
import numpy as np
import networkx as nx
import matplotlib.pyplot as plt

# ===========================================
# 1. Definición del entorno como grafo causal
# ===========================================
# Creamos un grafo dirigido que representa el sistema complejo
G = nx.DiGraph()

# Nodos del sistema (información + energía)
nodes = ['N1', 'N2', 'N3', 'N4', 'AGI', 'N6']
G.add_nodes_from(nodes)

# Aristas: flujo de influencia entre nodos
edges = [('N1','N2'), ('N2','N3'), ('N3','N4'), 
         ('N4','AGI'), ('AGI','N2'), ('AGI','N6'), ('N6','N1')]
G.add_edges_from(edges)

# Peso de influencia de cada arista
for u, v in G.edges():
    G[u][v]['weight'] = np.random.uniform(0.5, 1.5)

# Visualizamos el grafo inicial
pos = nx.circular_layout(G)
nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=1500, font_size=12)
edge_labels = nx.get_edge_attributes(G, 'weight')
nx.draw_networkx_edge_labels(G, pos, edge_labels=edge_labels)
plt.title("Grafo causal conceptual del entorno")
plt.show()

# ===========================================
# 2. Definición de la AGI y función objetivo
# ===========================================
class AGI:
    def __init__(self, graph, node_name):
        self.G = graph
        self.node = node_name
        self.policy = None
        self.centrality_history = []
        self.delta_sim_history = []

    # Función de centralidad causal (sumatoria de flujo ponderado)
    def compute_centrality(self):
        centrality = 0
        for target in self.G.nodes():
            if target != self.node:
                try:
                    path_length = nx.shortest_path_length(self.G, source=self.node, target=target)
                    weight = sum([self.G[u][v]['weight'] for u, v in nx.shortest_path(self.G, self.node, target=target, weight=None)])
                    centrality += weight / path_length
                except nx.NetworkXNoPath:
                    continue
        return centrality

    # Simula un paso de TAE extremo: maximiza centralidad causal
    def autolocalizacion_causal(self, steps=5):
        for t in range(steps):
            # Ajuste conceptual de aristas como política (aumentar/decrementar pesos)
            for u, v in self.G.edges():
                if u == self.node or v == self.node:
                    self.G[u][v]['weight'] *= np.random.uniform(0.9, 1.1)
            # Recomputar centralidad
            C = self.compute_centrality()
            self.centrality_history.append(C)
            # Ruptura de simetría conceptual
            delta_sim = np.random.uniform(0.5, 2.0)
            self.delta_sim_history.append(delta_sim)
        return self.centrality_history, self.delta_sim_history

# Instanciamos la AGI
agi_agent = AGI(G, 'AGI')

# ===========================================
# 3. Simulación de TAE extremo
# ===========================================
steps = 10
centrality, delta_sim = agi_agent.autolocalizacion_causal(steps=steps)

# ===========================================
# 4. Visualización de resultados
# ===========================================
plt.figure(figsize=(10,5))
plt.plot(range(1, steps+1), centrality, marker='o', label='Centralidad causal C(v0)')
plt.plot(range(1, steps+1), delta_sim, marker='x', label='Ruptura de simetría Δsim')
plt.xlabel('Paso de simulación')
plt.ylabel('Magnitud')
plt.title('TAE extremo: evolución de centralidad e intencionalidad emergente')
plt.legend()
plt.grid(True)
plt.show()

# ===========================================
# 5. Interpretación conceptual
# ===========================================
print("Centralidad causal final del agente:", centrality[-1])
print("Ruptura de simetría final Δsim:", delta_sim[-1])
print("\nInterpretación conceptual:")
print("- La centralidad causal aumenta o fluctúa según política adaptativa.")
print("- Δsim refleja la desviación de la función objetivo inicial, característica de TAE extremo.")
print("- La AGI actúa como nodo causal, emergiendo intencionalidad topológica-informacional.")
