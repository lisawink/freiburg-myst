---
title: The effect of urban form on the intra-urban variability of the heat island
subject: Tutorial
subtitle: 2-dimensional building and street parameters
short_title: Overview
authors:
  - name: Lisa Winkler
    affiliations:
      - University of Freiburg
    orcid: 0000-0002-7859-8394
    email: lisa.winkler@meteo.uni-freiburg.de
license: CC-BY-4.0
abstract: |
  Analysing 2-dimensional urban form around Freiburg's weather stations with respect to air temperature
---

### Background


Parameters calculated using `momepy` and `geopandas`

### 2D Urban form Parameters
| **Category**    | **Parameter**                            | **Abbrev.** | **Unit**  | **Element**            | **Equation**                           | **Description** | **Source** |
|------------------|-----------------------------------------|-------------|-----------|------------------------|--------------------------|-----------------------------------------|--------------------------|
| Dimension        | [Building Number](BuAre.html)                          | BuNum       | count        | Building            |               | Number of buildings | geopandas |
| Dimension        | [Building Area](BuAre.html)                          | BuAre       | m²        | Building                |                                          | | geopandas |
| Dimension        | [Building Perimeter](map.html)                      | BuPer       | m         | Building                |                                        | | momepy |
| Dimension        | Longest Axis Length                     | BuLAL       | m         | Building                |  $max(axis_1,axis_2,...,axis_n)$      | Length of the longest axis of object |
| Dimension        | Centroid Corner Distance                | BuCCD       | m         | Building                |                                         | Distance between centroid and corner |
| Dimension        | Number of Corners                       | BuCor       | count     | Building                |                                         | | momepy |
| Dimension        | Courtyard Area                          | CyAre       | m         | Building                |                                         | |
| Dimension        | Courtyard Index                         | CyInd       | ratio     | Building                |                                       | Area of courtyard over total area of building |
| Shape        | Circular Compactness                         | BuCCo       | ratio     | Building                |     $\frac{\text{area}}{\text{area of enclosing circle}}$      
| Shape            | Compactness Weighted Axis               | BuCWA       | m         | Building                |  $d_i = (\frac{\pi}{4}-\frac{16area_i}{perimeter_i^{2}})$ | Longest axis length weighted by compactness |
| Shape            | Convexity                               | BuCon       | ratio     | Building                |   $\frac{\text{area}}{\text{area of convex hull}}$        | Area deviation between a polygon and its convex hull - polygon’s degree of being curved inward or outward | momepy |
| Shape            | Elongation                              | BuElo       | ratio     | Building                |  $\frac{\frac{p - \sqrt{p^2 - 16a}}{4}}{\frac{p}{2} - \frac{p - \sqrt{p^2 - 16a}}{4}}$ | Elongation of minimum bounding rectangle |
| Shape            | Equivalent Rectangular Index            | BuERI       | ratio     | Building                | $\sqrt{\frac{\text{area}}{\text{area of bounding rectangle}}} \cdot \frac{\text{perimeter of bounding rectangle}}{\text{perimeter}}$ |
| Shape            | Facade Ratio                            | BuFR        | ratio     | Building                |  $area/perimeter$                       |
| Shape            | Form Factor                             | BuFF        | ratio     | Building                |  $\frac{(perimeter*height)+area}{volume^{2/3}}$ | Surface to volume ratio |
| Shape            | Fractal Dimension                       | BuFD        | ratio     | Building                |  $\frac{2\log\left(\frac{\text{perimeter}}{4}\right)}{\log(\text{area})}$  | perimeter-area method that quantifies the degree of complexity | momepy |
| Shape            | Fractality                       | BuFra        | ratio     | Building                |  $\mathrm{FR}_2=1-\frac{\log \left(A_{\mathrm{PN}}\right)}{2 \times \log \left(P_{\mathrm{PN}}\right)}$ | measures the edge roughness orsmoothness | 3d-building-metrics |
| Shape            | Rectangularity                          | BuRec       | ratio     | Building                |  $\frac{\text{area}}{\text{area of minimum bounding rectangle}}$ | area deviation between a polygon and its minimum area bounding rectangle - polygon’s degree of being curved inward | momepy |
| Shape            | Shape Index                             | BuShI       | ratio     | Building                |  $\frac{\sqrt{\frac{\text { area }}{\pi}}}{0.5 * \text { longest axis }}$ | |
| Shape            | [Square Compactness](BuSqC.html)        | BuSqC       | ratio     | Building                | $\left(\frac{4 \sqrt{\text { area }}}{\text { perimeter }}\right)^2$ | |
| Shape            | Squareness (Corner Deviation)       | BuCorDev       | deg       | Building                |                         | Mean deviation of angles at corners from 90 degrees |
| Shape        | Circularity | BuCir      | ratio        | Building                | $\frac{A_{\text{PN}}}{A_{\text{EPC}}} = \frac{4 \pi A_{\text{PN}}}{P_{\text{PN}}^2}$| Area deviation between a polygon and its equal-perimeter circle | 3d-building-metrics |
| Shape            | Convexity     | BuCon      | ratio     | Building                |  $\frac{\text{area}}{\text{area of convex hull}}$        | area deviation between a polygon and its convex hull, revealing curvature. | 3d-building-metrics |
| Shape            | Fractality                       | BuFra        | ratio     | Building                |  $\mathrm{FR}_3=1-\frac{\log \left(V_{\mathrm{MS}}\right)}{\frac{3}{2} \times \log \left(A_{\mathrm{MS}}\right)}$ | edge roughness or smoothness | 3d-building-metrics |
| Shape            | [Squareness](visualisations/BuSqu.ipynb)  | BuSqu       | ratio     | Building                |  $\frac{P_{\text{EAC}}}{P_{\text{PN}}} = \frac{4 \sqrt{A_{\text{PN}}}}{P_{\text{PN}}}$ | perimeter deviation between a polygon and its equal-area square | 3d-building-metrics |
| Shape            | Cohesion                          | BuCoh       | ratio     | Building                |  $\frac{0.9054 \times \sqrt{\frac{A_{\text{PN}}}{\pi}}}{\frac{1}{n \cdot (n - 1)} \sum_{i=1}^{n} \sum_{j=1}^{n} d_{\text{igp}_{ij}}}$ | Overall accessibility from all points to others within a polygon | 3d-building-metrics |
| Shape            | Proximity                          | BuProx       | ratio     | Building                |  $\frac{\frac{2}{3} \times r_{\text{EAC}}}{\mu_{r_{\text{igp}}}} = \frac{\frac{2}{3} \times \sqrt{\frac{A_{\text{PN}}}{\pi}}}{\mu_{r_{\text{igp}}}}$ | Overall accessibility from all inner points to the center of a polygon | 3d-building-metrics |
| Shape            | Exchange                          | BuEx       | ratio     | Building                |  $\frac{A_{\text{PN} \cap \text{EAC}}}{A_{\text{PN}}}$ | How much area inside a circle is exchanged with the area outside to create the polygon | 3d-building-metrics |
| Shape            | Spin                          | BuSpi       | ratio     | Building                | $\frac{0.5 \times \frac{A_{\text{PN}}}{\pi}}{\mu_{r_{\text{igp}}^2}}$ | Focuses on compactness of shape extremities | 3d-building-metrics |
| Shape            | Perimeter Compactness          | BuPerC       | ratio     | Building                |  $\frac{P_{\text{EAC}}}{P_{\text{PN}}} = \frac{2 \cdot \sqrt{\pi \cdot A_{\text{PN}}}}{P_{\text{PN}}}$ | Focuses on the compactness of a polygon’s boundary | 3d-building-metrics |
| Shape            | Depth                          | BuDep       | ratio     | Building                |  $\frac{\mu_{PN_{d_{\text{igp}}, b}}}{\mu_{EAC_{d_{\text{igp}}, b}}} = \frac{3 \cdot \mu_{PN_{d_{\text{igp}}, b}}}{\sqrt{\frac{A_{\text{PN}}}{\pi}}}$ | Highlights irregular changes along a polygon’s boundary | 3d-building-metrics |
| Shape            | Girth                         | BuGir       | ratio     | Building                | $\frac{r_{\text{LIC}}}{r_{\text{EAC}}} = \frac{r_{\text{LIC}}}{\sqrt{\frac{A_{\text{PN}}}{\pi}}}$ | Measures the thickness of the layer insulating the core from the periphery | 3d-building-metrics |
| Shape            | Dispersion                          | BuDisp       | ratio     | Building                |  $1 - \frac{\mu_{r_{\text{dev}}}}{r_{\text{ADC}}} = 1 - \frac{\mu_{r_{\text{dev}}}}{\mu_{r_{\text{ibp}}}}$ | Indicates whether a phenomenon propagates equally in all directions | 3d-building-metrics |
| Shape            | Range                      | BuRan      | ratio     | Building                |  $\frac{r_{\text{EAC}}}{r_{\text{SCC}}} = \frac{\sqrt{\frac{A_{\text{PN}}}{\pi}}}{r_{\text{SCC}}}$ | Measures the distance between the furthest faces of a polygon, sensitive to remote sections | 3d-building-metrics |
| Shape            | Roughness Index       | BuRough       | ratio     | Building                |  $\frac{\mu_{r_{\text{ibp}}}^2}{A_{\text{PN}} + P_{\text{PN}}^2} \times 42.62$ | Created as a measure of compactness. Advantages: (1) Less sensitive to elongation (aspect ratio of a polygon), and (2) more responsive to boundary roughness (intrusions and protrusions). 
| Distribution        | Building Adjacency                      | BuAdj       | ratio     | Neighbourhood           | $BuAdj_{blg} = \frac{\sum blg_{adj}}{\sum blg}$ | How much buildings tend to join together into larger structures |
| Distribution        | Mean Inter-Building Distance            | BuIBD       | m         | Neighbourhood           |  $IBD_{blg} = \frac{1}{n} \sum_{i=1}^{n} d_{blg, blg_i}$ |
| Distribution        | [Shared Walls Ratio](BuSWR.html)            | BuSWR       | ratio     | Building                |  $\frac{length of shared walls}{sum of building perimeter}$ | |
| Orientation      | [Orientation](BuOri.html)               | BuOri       | deg       | Building                |                                          | Deviation of orientation of the bounding rectangle from cardinal directions |
| Orientation      | Alignment                               | BuAli       | deg       | Building                |  $\frac{1}{n} \sum_{i=1}^{n} dev_i = \frac{dev_1 + dev_2 + \cdots + dev_n}{n}$ |  Mean deviation of orientation of adjacent buildings | momepy |
| Orientation      | Street Alignment                        | StrAli      | deg       | Building, Street Segment |                                          | Deviation of the building orientation from the street orientation | momepy |
| Distribution     | Street Width                            | StrW        | m         | Street Segment           |                                          | | momepy |
| Distribution     | Street Width Deviation                  | StrWD       | m         | Street Segment           |                                          | Deviation of width along a street segment | momepy |
| Distribution     | Street Openness                         | StrOpe      | ratio     | Building, Street Segment |  $Ope_{sp} = 1 - \frac{\sum_{hit}}{2 \sum_{sec}}$ | Ratio of street profile sections intersecting buildings. Refers to the presence of buildings along the street; wider gaps between buildings will lead to a higher openness | momepy |
| Distribution     | Street Height             | StrH    | m     | Building | mean, std || Height of buildings along a street segment | momepy |
| Distribution     | Street Height Deviation   | StrHD   | m     | Building | mean, std || Height deviation of buildings along a street segment| momepy |
| Distribution     | [Street Height-Width Ratio](StrHW.html) | StrHW       | ratio     | Building, Street Segment |                                          | Height to width ratio of buildings along a street segment | momepy |
| Dimension        | Street Segment Length                   | StrLen      | m         | Street  Segment          |                                          | Length of individual street segment | momepy |
| Dimension        | Total Street Length                     | StrCNS      | m         | Street Network           |                                          | Total length of continuous street segments | momepy |
| Intensity        | Buildings per Meter of Street Segment   | BpM         | count/m   | Building, Street Segment |  $\frac{\text{no. of buildings along street segment}}{\text{length of street segment}}$ | | momepy |
| Shape            | Street Linearity                        | StrLin      | ratio     | Street Segment           |  $Lin_{edg} = \frac{l_{eucl}}{l_{edg}}$ | Ratio of Euclidean distance between the first and the last point of a line and its length https://onlinelibrary.wiley.com/doi/full/10.1111/gean.12302  | momepy |
| Connectivity     | [Local Closeness Centrality (400m)](StrClo400.html) | StrClo      | 1/m       | Street Network         |                                         | Average distance to every other node from each node within 400m and 1200m radius | momepy |
| Connectivity     | Local Betweenness Centrality (400m,1200m)| StrBet     | ratio    | Street Network         |  $c_B(v)=\sum_{s, t \in V} \frac{\sigma(s, t \mid v)}{\sigma(s, t)}$ networkx |  The extent to which node lies on paths between other nodes | momepy |
| Connectivity     | Squares Clustering Coefficient         | StrSCl      | ratio     | Street Network         |                                         | The degree to which nodes in graph tend to cluster together | momepy |
| Connectivity     | Cyclomatic Complexity                  | StrCyc      | count     | Street Network         | $\alpha=e-v+1$                 | |  momepy |
| Connectivity     | Edge Node Ratio                        | StrENR      | ratio     | Street Network         |   $\alpha=\frac{e}{v}$               | Ratio of edges to nodes | momepy |
| Connectivity     | Gamma                                  | StrGam      | ratio     | Street Network         | $\alpha=\frac{e}{3(v-2)}$                  | Connectivity ratio of edges to nodes |momepy |
| Connectivity     | Node Degree of Junction                | StrDeg      | count     | Street Network         | $\operatorname{deg}_{\text {node }_i}=\sum_j e d g_{i j}$ | Number of edges connected to node |momepy |
| Connectivity     | Node Density                          | StrND       | count/m   | Street Network         |                                         | Number of nodes / Cumulative length of street network within neighbourhood |momepy |
| Connectivity     | Local Meshedness                       | StrMes      | ratio     | Street Network         |                                          | Ratio of faces in a network to maximum loops in network with same number of nodes |momepy |


Parameters calculated using `3d-building-metrics`

### 3D Urban form Parameters
| **Category** | **Parameter**               | **Abbrev.**| **Unit**| **Element**            |  **Equation**       | **Description**                | **Source** |
|--------------|-----------------------------|------------|---------|------------------------|--------------------|----------------------------------|--------|
| Dimension    | [Building Height](BuHt.html)| BuHt_3D    | m     | Building || | LoD1 |
| Dimension    | [Surface Area](BuSA_3D.html)| BuSA_3D    | m²    | Building || | 3d-building-metrics |
| Dimension    | [Volume](BuVol_3D.html)     | BuVol_3D   | m²    | Building || | 3d-building-metrics |
| Dimension    | Minimum Vertical Elongation | BumVE_3D   | m²    | Building || Elongation of a polyhedron using its minimum bounding box: shortest side against height | 3d-building-metrics |
| Dimension    | Maximum Vertical Elongation | BuMVE_3D   | m²    | Building || Elongation of a polyhedron using its minimum bounding box: longest side against height | 3d-building-metrics |
| Dimension    | Surface Count               | BuSurf_3D  | count | Building |                                         | Number of surfaces of shape | 3d-building-metrics |
| Shape        | Hemisphericality            | BuHem_3D   | ratio | Building | $\frac{3 \sqrt{2 \pi} V}{A_{mesh}^{\frac{3}{2}}}$| Volume deviation between a polyhedron and its equal-area hemisphere | 3d-building-metrics |
| Shape        | Convexity                   | BuCon_3D   | ratio | Building |  $\frac{\text{mesh volume}}{\text{volume of convex hull}}$        | volume deviation between a polyhedron and its convex hull - building’s degree of being curved inward or outward | 3d-building-metrics |
| Shape        | [Fractality](BuFra_3D.html) | BuFra_3D   | ratio | Building | $\mathrm{FR}_3=1-\frac{\log \left(V_{\mathrm{MS}}\right)}{\frac{3}{2} \times \log \left(A_{\mathrm{MS}}\right)}$ | Surface roughness or smoothness | 3d-building-metrics |
| Shape        | Cuboidness                  | BuCubo_3D  | ratio | Building | $\frac{\text{mesh volume}}{\text{Object-Oriented Bounding Box of the mesh}}$ | Volume deviation between a polyhedron and its minimum volume bounding box - polyhedral’s degree of being curved inwards | 3d-building-metrics |
| Shape        | Cubeness                    | BuCube_3D  | ratio | Building | $\frac{\text{AEVS}}{\text{AMS}} = \frac{6 \sqrt{\text{VMS}^2}}{\text{AMS}}$ | surface area deviation between a polyhedron and its equal-volume cube | 3d-building-metrics |
| Shape        | Cohesion                    | BuCoh_3D   | ratio | Building | $nCI_3 = \frac{\frac{36}{35} \times \sqrt[3]{\frac{3}{4} \cdot \frac{\text{VMS}}{\pi}}}{\frac{1}{n(n-1)}} \sum_{i=1}^{n} \sum_{j=1}^{n} d_{ij}^{gp}$ | overall accessibility from all points to others within a polyhedron | 3d-building-metrics |
| Shape        | Proximity                   | BuProx_3D   | ratio | Building | $\frac{\frac{3}{4} \times r_{\text{EVS}}}{\mu_{r_{\text{igp}}}} = \frac{\frac{3}{4} \times \sqrt[3]{\frac{3}{4} \cdot \frac{\text{VMS}}{\pi}}}{\mu_{r_{\text{igp}}}}$ | overall accessibility from all inner points to the center of a polyhedron | 3d-building-metrics |
| Shape        | Exchange                    | BuEx_3D    | ratio | Building | $\frac{V_{\text{MS} \cap \text{EVS}}}{V_{\text{MS}}}$ | Measures how much volume inside a sphere is exchanged with the volume outside to create the polyhedro | 3d-building-metrics |
| Shape        | Spin                        | BuSpi_3D   | ratio | Building | $\frac{\frac{3}{5} \times \left(\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}\right)^2}{\mu_{r_{\text{igp}}^2}}$ | Focuses on compactness of polyhedron extremities | 3d-building-metrics |
| Shape        | Circumference Compactness         | BuCf_3D    | ratio | Building | mean, std | $\frac{4 \pi \times \left(\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}\right)^2}{A_{\text{MS}}}$ | Focuses on the compactness of a polyhedron’s boundary | 3d-building-metrics |
| Shape        | Depth                       | BuDep_3D   | ratio | Building | $\frac{4 \times \mu_{\text{MS}_{d_{\text{idgp,b}}}}}{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}$ | Highlights irregular changes along a polyhedron’s boundary | 3d-building-metrics |
| Shape        | Girth                       | BuGir_3D   | ratio | Building | $\frac{r_{\text{LIS}}}{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}$ | Measures the thickness of the layer insulating the core from the periphery | 3d-building-metrics |
| Shape        | Dispersion                  | BuDisp_3D   | ratio | Building | $1 - \frac{\mu_{r_{\text{dev}}}}{r_{\text{ADS}}} = 1 - \frac{\mu_{r_{\text{dev}}}}{\mu_{r_{\text{ibp}}}}$ | Indicates whether a phenomenon propagates equally in all directions | 3d-building-metrics |
| Shape        | Range                       | BuRan_3D   | ratio | Building | $\frac{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}{r_{\text{SCS}}}$ | Measures the distance between the furthest faces of a polyhedron, sensitive to remote sections | 3d-building-metrics |
| Shape        | Equivalent Prism Index      | BuEPI_3D   | ratio | Building | $\left(\sqrt[3]{\frac{V_{\text{MS}}}{V_{\text{OOBB}}}}\right)^2 \times \frac{A_{\text{OOBB}}}{A_{\text{MS}}}$ | deviation of a polyhedron from an equivalent cuboid by scaling its minimum volume bounding box to match its volume | 3d-building-metrics |
| Shape        | Roughness (Shape Boundary)  | BuRough_3D    | ratio | Building | $\frac{\mu_{r_{\text{ibp}}}^3}{V_{\text{MS}} + A_{\text{MS}}^{\frac{3}{2}}} \times 48.735$ | Created as a measure of compactness. Advantages: (1) Less sensitive to elongation (aspect ratio of a polyhedron), and (2) more responsive to boundary roughness (intrusions and protrusions) | 3d-building-metrics |
| Shape        | Form Factor                 | BuFF_3D    | ratio | Building | $\frac{A}{V^{\frac{2}{3}}}$ | compactness of a 3D object which attempts to remove the bias introduced by the size of an object | 3d-building-metrics |
| Distribution | [Shared Walls Ratio](BuSWR_3D.html)| BuSWR_3D   | ratio | Building || Area of shared walls| 3d-building-metrics |
| Distribution | Sky View Factor             | BuSVF_3D   | ratio | Building || | DSM, Ferdi |



### Definitions

Building adjacency refers to how much buildings tend to join together into larger structures and is the number of joined built-up structures divided by number of buildings in the neighbourhood. Mean inter-building distance refers to the mean proximity between adjacent buildings in the neighbourhood. Adjacency is defined by a delaunay triangulation of the building polygons. Shared walls is defined as the length of shared walls of adjacent buildings. 

Orientation is defined as the deviation of orientation of the bounding rectangle from cardinal directions, alignment is the mean deviation of orientation of adjacent buildings (defined by delaunay triangulation) and street alignment is the deviation of the building orientation from the street orientation.

Width of a street profile is the mean length of a street profile sections along street segments. Street openness is the ratio of street profile sections intersecting buildings and it refers to the presence of buildings along the street; that is, wider gaps between buildings will lead to a higher openness. Linearity of a street segment is the ratio of Euclidean distance between the first and the last point of a line and its length https://onlinelibrary.wiley.com/doi/full/10.1111/gean.12302

### Factor Analysis across Buildings, Street Segments and Reference Areas/Circles


### Simple linear model with two PCs

1. PCA of all the parameters aggregated to 150m around the weather stations;
2. choose the PCs with the strongest relationship to temperature (from individual linear regression); and
3. plot the linear regression of both PCs with temperature.

:::{image} ./images/9bxvl4.gif
:alt: A rotating 3D plot
:width: 1000px
:align: center
:figcaption: PC1, PC4 and temperature of weather stations
:::

> `R^2: 0.559788042465736`

### Results

- Diversity of building shape in Freiburg leads to higher night-time temperatures
  - function of variance in building shape as well as skewness from outliers (extreme building shapes)

### Predicting temperature

Using a simple linear regression between temperature and HW ratio at a radius of 200m, we can predicted the temperature for all streets in Freiburg: [map of predicted temp](HW_predicted_temp.html)
