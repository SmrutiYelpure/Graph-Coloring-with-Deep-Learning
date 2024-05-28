<div class="title">
  <h1>Graph Coloring with Deep Learning</h1>
</div>

<p>A deep learning-based hybrid approach for the graph coloring problem, with a focus on register allocation in compilers. This repository provides an implementation of the algorithm described in the research paper "Deep Learning-based Hybrid Graph-Coloring Algorithm for Register Allocation" by Dibyendu Das, Shahid Asghar Ahmad, and Kumar Venkataramanan.</p>

<div class="description">
  <h2>Description</h2>
  <p>This project aims to learn a good heuristic for coloring interference graphs used in the register allocation phase of compilers. The algorithm combines a deep learning model and a color correction phase to achieve efficient graph coloring.</p>
  <p>The deep learning model is a Recurrent Neural Network (RNN) with Long Short-Term Memory (LSTM) layers. It takes the adjacency matrix of a graph as input and outputs the colors assigned to each node. The color correction phase resolves any invalid colorings by reassigning colors to adjacent nodes with the same color.</p>
  <p>The implementation is designed to handle moderate-sized interference graphs with up to 100 nodes. It performs favorably compared to optimal coloring on popular graphs and LLVM's greedy register allocator for SPEC CPU® 2017 benchmarks.</p>
</div>

<div class="usage">
  <h2>Usage</h2>
  <ol>
    <li>Install the required dependencies:
      <pre><code>pip install tensorflow numpy</code></pre>
    </li>
    <li>Run the example code:
      <pre><code class="python"># Generate or load some graphs
graphs = [
    Graph([[0, 1, 1, 0], [1, 0, 1, 1], [1, 1, 0, 1], [0, 1, 1, 0]]),
    Graph([[0, 1, 0, 1], [1, 0, 1, 0], [0, 1, 0, 1], [1, 0, 1, 0]]),
    # ... more graphs
]

# Train the model
model = train(graphs)

# Infer colors for a new graph
new_graph = Graph([[0, 1, 0, 1], [1, 0, 1, 1], [0, 1, 0, 0], [1, 1, 0, 0]])
colors = infer(model, new_graph)

# Apply color correction
corrected_colors = color_correction(new_graph, colors)
print("Corrected colors:", corrected_colors)</code></pre>
    </li>
  </ol>
</div>

<div class="code-structure">
  <h2>Code Structure</h2>
  <ul>
    <li><code>GraphColoringModel</code>: Defines the deep learning model architecture with LSTM layers and a dense layer for color prediction.</li>
    <li><code>color_correction</code>: Implements the color correction phase by iterating through invalid edges and reassigning colors to resolve conflicts.</li>
    <li><code>Graph</code>: Represents a graph with an adjacency matrix and provides utilities for extracting edges and neighbors.</li>
    <li><code>preprocess_data</code>: Preprocesses the input graphs by converting adjacency matrices to input and output formats suitable for the deep learning model.</li>
    <li><code>train</code>: Trains the deep learning model on a set of graphs.</li>
    <li><code>infer</code>: Performs inference on a new graph using the trained model.</li>
  </ul>
</div>

<div class="contributing">
  <h2>Contributing</h2>
  <p>Contributions are welcome! Please follow the standard GitHub workflow:</p>
  <ol>
    <li>Fork the repository</li>
    <li>Create a new branch</li>
    <li>Make your changes</li>
    <li>Open a pull request</li>
  </ol>
</div>

<div class="license">
  <h2>License</h2>
  <p>This project is licensed under the <a href="LICENSE">MIT License</a>.</p>
</div>

<div class="acknowledgments">
  <h2>Acknowledgments</h2>
  <ul>
    <li>The authors of the research paper for their work and insights</li>
    <li>The LLVM project and its contributors</li>
    <li>The Standard Performance Evaluation Corporation (SPEC) for the CPU benchmarks</li>
  </ul>
</div>
