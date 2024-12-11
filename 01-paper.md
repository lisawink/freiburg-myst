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

### 2D Urban form parameters
| **Category**    | **Parameter**                            | **Abbrev.** | **Unit**  | **Element**            | **Aggregation**         | **Equation**                           | **Description** | **Source** |
|------------------|-----------------------------------------|-------------|-----------|------------------------|--------------------------|-----------------------------------------|--------------------------|--------------|
| Dimension        | Building Area                           | BuAre       | m²        | Building                | count, sum, mean, std    |                                         | | geopandas |
| Dimension        | Building Perimeter                      | BuPer       | m         | Building                | mean, std     |                                        | | momepy |
| Dimension        | Longest Axis Length                     | BuLAL       | m         | Building                | mean, std     |  $max(axis_1,axis_2,...,axis_n)$      | Length of the longest axis of object |
| Dimension        | Centroid Corner Distance                | BuCCD       | m         | Building                | mean, std     |                                         | Distance between centroid and corner |
| Dimension        | Number of Corners                       | BuCor       | count     | Building                | mean, std     |                                         | | momepy |
| Dimension        | Courtyard Area                          | CyAre       | m         | Building                | sum, mean, std     |                                         | |
| Dimension        | Courtyard Index                         | CyInd       | ratio     | Building                | mean, std             |                                       | Area of courtyard over total area of building |
| Shape        | Circular Compactness                         | BuCCo       | ratio     | Building                | mean, std             |    $\frac{\text{area}}{\text{area of enclosing circle}}$      
| Shape        | Circularity               | BuCir       | ratio     | Building                | mean, std             |    $\frac{A_{\mathrm{PN}}}{A_{\mathrm{EPC}}}=\frac{4 \pi A_{\mathrm{PN}}}{P_{\mathrm{PN}}^2}$ | area deviation between a polygon and its equal-perimeter circle   | 3d-building-metrics |
| Shape            | Compactness Weighted Axis               | BuCWA       | m         | Building                | mean, std                    | $d_i = (\frac{\pi}{4}-\frac{16area_i}{perimeter_i^{2}})$ | Longest axis length weighted by compactness |
| Shape            | Convexity                               | BuCon       | ratio     | Building                | mean, std        |  $\frac{\text{area}}{\text{area of convex hull}}$        | Area deviation between a polygon and its convex hull - polygon’s degree of being curved inward or outward | momepy |
| Shape            | Elongation                              | BuElo       | ratio     | Building                | mean, std     | $\frac{\frac{p - \sqrt{p^2 - 16a}}{4}}{\frac{p}{2} - \frac{p - \sqrt{p^2 - 16a}}{4}}$ | Elongation of minimum bounding rectangle |
| Shape            | Equivalent Rectangular Index            | BuERI       | ratio     | Building                | mean, std   | $\sqrt{\frac{\text{area}}{\text{area of bounding rectangle}}} \cdot \frac{\text{perimeter of bounding rectangle}}{\text{perimeter}}$ |
| Shape            | Facade Ratio                            | BuFR        | ratio     | Building                | mean, std               | $area/perimeter$                       |
| Shape            | Form Factor                             | BuFF        | ratio     | Building                | mean, std               | $\frac{(perimeter*height)+area}{volume^{2/3}}$ | |
| Shape            | Fractal Dimension                       | BuFD        | ratio     | Building                | mean, std               | $\frac{2\log\left(\frac{\text{perimeter}}{4}\right)}{\log(\text{area})}$  | perimeter-area method that quantifies the degree of complexity | momepy |
| Shape            | Fractality                       | BuFra        | ratio     | Building                | mean, std               | $\mathrm{FR}_2=1-\frac{\log \left(A_{\mathrm{PN}}\right)}{2 \times \log \left(P_{\mathrm{PN}}\right)}$ | measures the edge roughness orsmoothness | 3d-building-metrics |
| Shape            | Rectangularity                          | BuRec       | ratio     | Building                | mean, std               | $\frac{\text{area}}{\text{area of minimum bounding rectangle}}$ | area deviation between a polygon and its minimum area bounding rectangle - polygon’s degree of being curved inward | momepy |
| Shape            | Shape Index                             | BuShI       | ratio     | Building                | mean, std               | $\frac{\sqrt{\frac{\text { area }}{\pi}}}{0.5 * \text { longest axis }}$ | |
| Shape            | Square Compactness                      | BuSqC       | ratio     | Building                | mean, std               | $\left(\frac{4 \sqrt{\text { area }}}{\text { perimeter }}\right)^2$ | |
| Shape            | Squareness                              | BuSqu       | deg       | Building                | mean, std               |                                         | Mean deviation of angles at corners from 90 degrees |
| Shape        | Circularity | BuHem       | ratio        | Building                | mean, std     | $\frac{A_{\text{PN}}}{A_{\text{EPC}}} = \frac{4 \pi A_{\text{PN}}}{P_{\text{PN}}^2}$| Area deviation between a polygon and its equal-perimeter circle | 3d-building-metrics |
| Shape            | Convexity     | BuCon_3D      | ratio     | Building                | mean, std        |  $\frac{\text{area}}{\text{area of convex hull}}$        | area deviation between a polygon and its convex hull, revealing curvature. | 3d-building-metrics |
| Shape            | Fractality                       | BuFra_3D        | ratio     | Building                | mean, std      | $\mathrm{FR}_3=1-\frac{\log \left(V_{\mathrm{MS}}\right)}{\frac{3}{2} \times \log \left(A_{\mathrm{MS}}\right)}$ | edge roughness or smoothness | 3d-building-metrics |
| Shape            | Squareness                          | BuCube_3D       | ratio     | Building                | mean, std               | $\frac{P_{\text{EAC}}}{P_{\text{PN}}} = \frac{4 \sqrt{A_{\text{PN}}}}{P_{\text{PN}}}$ | perimeter deviation between a polygon and its equal-area square | 3d-building-metrics |
| Shape            | Cohesion                          | BuCoh_3D       | ratio     | Building                | mean, std               | $\frac{0.9054 \times \sqrt{\frac{A_{\text{PN}}}{\pi}}}{\frac{1}{n \cdot (n - 1)} \sum_{i=1}^{n} \sum_{j=1}^{n} d_{\text{igp}_{ij}}}$ | Overall accessibility from all points to others within a polygon | 3d-building-metrics |
| Shape            | Proximity                          | BuPro_3D       | ratio     | Building                | mean, std               | $\frac{\frac{2}{3} \times r_{\text{EAC}}}{\mu_{r_{\text{igp}}}} = \frac{\frac{2}{3} \times \sqrt{\frac{A_{\text{PN}}}{\pi}}}{\mu_{r_{\text{igp}}}}$ | Overall accessibility from all inner points to the center of a polygon | 3d-building-metrics |
| Shape            | Exchange                          | BuEx_3D       | ratio     | Building                | mean, std               | $\frac{A_{\text{PN} \cap \text{EAC}}}{A_{\text{PN}}}$ | How much area inside a circle is exchanged with the area outside to create the polygon | 3d-building-metrics |
| Shape            | Spin                          | BuSpi_3D       | ratio     | Building                | mean, std               | $\frac{0.5 \times \frac{A_{\text{PN}}}{\pi}}{\mu_{r_{\text{igp}}^2}}$ | Focuses on compactness of shape extremities | 3d-building-metrics |
| Shape            | Perimeter Compactness          | BuCf_3D       | ratio     | Building                | mean, std               | $\frac{P_{\text{EAC}}}{P_{\text{PN}}} = \frac{2 \cdot \sqrt{\pi \cdot A_{\text{PN}}}}{P_{\text{PN}}}$ | Focuses on the compactness of a polygon’s boundary | 3d-building-metrics |
| Shape            | Depth                          | BuDep_3D       | ratio     | Building                | mean, std               | $\frac{\mu_{PN_{d_{\text{igp}}, b}}}{\mu_{EAC_{d_{\text{igp}}, b}}} = \frac{3 \cdot \mu_{PN_{d_{\text{igp}}, b}}}{\sqrt{\frac{A_{\text{PN}}}{\pi}}}$ | Highlights irregular changes along a polygon’s boundary | 3d-building-metrics |
| Shape            | Girth                         | BuGir_3D       | ratio     | Building                | mean, std               | $\frac{r_{\text{LIC}}}{r_{\text{EAC}}} = \frac{r_{\text{LIC}}}{\sqrt{\frac{A_{\text{PN}}}{\pi}}}$ | Measures the thickness of the layer insulating the core from the periphery | 3d-building-metrics |
| Shape            | Dispersion                          | BuDis_3D       | ratio     | Building                | mean, std               | $1 - \frac{\mu_{r_{\text{dev}}}}{r_{\text{ADC}}} = 1 - \frac{\mu_{r_{\text{dev}}}}{\mu_{r_{\text{ibp}}}}$ | Indicates whether a phenomenon propagates equally in all directions | 3d-building-metrics |
| Shape            | Range                      | BuRan_3D       | ratio     | Building                | mean, std               | $\frac{r_{\text{EAC}}}{r_{\text{SCC}}} = \frac{\sqrt{\frac{A_{\text{PN}}}{\pi}}}{r_{\text{SCC}}}$ | Measures the distance between the furthest faces of a polygon, sensitive to remote sections | 3d-building-metrics |
| Shape            | Roughness Index       | BuRI_3D       | ratio     | Building                | mean, std               | $\frac{\mu_{r_{\text{ibp}}}^2}{A_{\text{PN}} + P_{\text{PN}}^2} \times 42.62$ | Created as a measure of compactness. Advantages: (1) Less sensitive to elongation (aspect ratio of a polygon), and (2) more responsive to boundary roughness (intrusions and protrusions). 
| Distribution        | Building Adjacency                      | BuAdj       | ratio     | Neighbourhood           | -                       | $BuAdj_{blg} = \frac{\sum blg_{adj}}{\sum blg}$ | How much buildings tend to join together into larger structures |
| Distribution        | Mean Inter-Building Distance            | BuIBD       | m         | Neighbourhood           | -                       | $IBD_{blg} = \frac{1}{n} \sum_{i=1}^{n} d_{blg, blg_i}$ |
| Distribution        | Shared Walls Ratio                      | BuSWR       | ratio     | Building                | mean, std               | $\frac{length of shared walls}{sum of building perimeter}$ | |
| Orientation      | Orientation                             | BuOri       | deg       | Building                | mean, std     |                                         | Deviation of orientation of the bounding rectangle from cardinal directions |
| Orientation      | Alignment                               | BuAli       | deg       | Building                | mean, std     | $\frac{1}{n} \sum_{i=1}^{n} dev_i = \frac{dev_1 + dev_2 + \cdots + dev_n}{n}$ |  Mean deviation of orientation of adjacent buildings |
| Orientation      | Street Alignment                        | StrAli      | deg       | Building, Street Segment | mean, std    |                                         | Deviation of the building orientation from the street orientation |
| Distribution     | Street Width                            | StrW        | m         | Street Segment           | mean, std     |                                         |
| Distribution     | Street Width Deviation                  | StrWD       | m         | Street Segment           | mean, std     |                                         | Deviation of width along a street segment
| Distribution     | Street Openness                         | StrOpe      | ratio     | Building, Street Segment | mean, std     | $Ope_{sp} = 1 - \frac{\sum_{hit}}{2 \sum_{sec}}$ | To what degree a street is surrounded by buildings |
| Distribution     | Street Height-Width Ratio               | StrHW       | ratio     | Building, Street Segment | mean, std               |                                         | Height to width ratio of buildings along a street segment |
| Dimension        | Street Segment Length                   | StrLen      | m         | Street  Segment          | mean, std               |                                         | Length of individual street segment
| Dimension        | Total Street Length                     | StrCNS      | m         | Street Network           | mean, std               |                                         | Total length of continuous street segments |
| Intensity        | Buildings per Meter of Street Segment   | BpM         | count/m   | Building, Street Segment | mean, std               | $\frac{\text{no. of buildings along street segment}}{\text{length of street segment}}$ | |
| Shape            | Street Linearity                        | StrLin      | ratio     | Street Segment           | mean, std     | $Lin_{edg} = \frac{l_{eucl}}{l_{edg}}$ | Ratio of length of segment between first and last point to length of street segment |
| Connectivity     | Local Closeness Centrality (400m,1200m) | StrClo      | 1/m       | Street Network         | mean, std               |                                         | Average distance to every other node from each node within 400m and 1200m radius |
| Connectivity     | Local Betweenness Centrality (400m,1200m)| StrBet     | ratio    | Street Network         | mean, std   | $c_B(v)=\sum_{s, t \in V} \frac{\sigma(s, t \mid v)}{\sigma(s, t)}$ networkx |  The extent to which node lies on paths between other nodes |
| Connectivity     | Squares Clustering Coefficient         | StrSCl      | ratio     | Street Network         | mean, std                 |                                         | The degree to which nodes in graph tend to cluster together |
| Connectivity     | Cyclomatic Complexity                  | StrCyc      | count     | Street Network         | mean, std                 | $\alpha=e-v+1$                 | 
| Connectivity     | Edge Node Ratio                        | StrENR      | ratio     | Street Network         | mean, std                |   $\alpha=\frac{e}{v}$               | Ratio of edges to nodes |
| Connectivity     | Gamma                                  | StrGam      | ratio     | Street Network         | mean, std                | $\alpha=\frac{e}{3(v-2)}$                  | Connectivity ratio of edges to nodes |
| Connectivity     | Node Degree of Junction                | StrDeg      | count     | Street Network         | mean, std                | $\operatorname{deg}_{\text {node }_i}=\sum_j e d g_{i j}$ | Number of edges connected to node |
| Connectivity     | Node Density                          | StrND       | count/m   | Street Network         | -                        |                                         | Number of nodes / Cumulative length of street network within neighbourhood |
| Connectivity     | Local Meshedness                       | StrMes      | ratio     | Street Network         | mean, std                |                                         | Ratio of faces in a network to maximum loops in network with same number of nodes |


Parameters calculated using `3d-building-metrics`

### Urban form parameters
| **Category**    | **Parameter**                            | **Abbrev.** | **Unit**  | **Element**            | **Aggregation**         | **Equation**       | **Description**                | **Source** |
|------------------|-----------------------------------------|-------------|-----------|------------------------|--------------------------|-----------------------------------------|---------------------------------------|--------|
| Dimension        | Building Height | BuHt        | m        | Building                | mean, std   || | LoD1 |
| Dimension        | Surface Area | BuSA        | m²        | Building                | mean, std   || | 3d-building-metrics |
| Dimension        | Volume | BuVol        | m²        | Building                | mean, std   || | 3d-building-metrics |
| Dimension        | Minimum Vertical Elongation | BumVE        | m²        | Building                | mean, std   || Elongation of a polyhedron using its minimum bounding box: shortest side against height | 3d-building-metrics |
| Dimension        | Maximum Vertical Elongation | BuMVE        | m²        | Building                | mean, std   || Elongation of a polyhedron using its minimum bounding box: longest side against height | 3d-building-metrics |
| Dimension        | Surface Count    | BuSurf      | count     | Building                | mean, std     |                                         | Number of surfaces of shape | 3d-building-metrics |
| Shape        | Hemisphericality | BuHem       | ratio        | Building                | mean, std     | $\frac{3 \sqrt{2 \pi} V}{A_{mesh}^{\frac{3}{2}}}$| Volume deviation between a polyhedron and its equal-area hemisphere | 3d-building-metrics |
| Shape            | Convexity     | BuCon_3D      | ratio     | Building                | mean, std        |  $\frac{\text{mesh volume}}{\text{volume of convex hull}}$        | volume deviation between a polyhedron and its convex hull - building’s degree of being curved inward or outward | 3d-building-metrics |
| Shape            | Fractality                       | BuFra_3D        | ratio     | Building                | mean, std      | $\mathrm{FR}_3=1-\frac{\log \left(V_{\mathrm{MS}}\right)}{\frac{3}{2} \times \log \left(A_{\mathrm{MS}}\right)}$ | Surface roughness or smoothness | 3d-building-metrics |
| Shape            | Cuboidness                          | BuCubo_3D       | ratio     | Building                | mean, std      | $\frac{\text{mesh volume}}{\text{Object-Oriented Bounding Box of the mesh}}$ | Volume deviation between a polyhedron and its minimum volume bounding box - polyhedral’s degree of being curved inwards | 3d-building-metrics |
| Shape            | Cubeness                          | BuCube_3D       | ratio     | Building                | mean, std               | $\frac{\text{AEVS}}{\text{AMS}} = \frac{6 \sqrt{\text{VMS}^2}}{\text{AMS}}$ | surface area deviation between a polyhedron and its equal-volume cube | 3d-building-metrics |
| Shape            | Cohesion                          | BuCoh_3D       | ratio     | Building                | mean, std               | $nCI_3 = \frac{\frac{36}{35} \times \sqrt[3]{\frac{3}{4} \cdot \frac{\text{VMS}}{\pi}}}{\frac{1}{n(n-1)}} \sum_{i=1}^{n} \sum_{j=1}^{n} d_{ij}^{gp}$ | overall accessibility from all points to others within a polyhedron | 3d-building-metrics |
| Shape            | Proximity                          | BuPro_3D       | ratio     | Building                | mean, std               | $\frac{\frac{3}{4} \times r_{\text{EVS}}}{\mu_{r_{\text{igp}}}} = \frac{\frac{3}{4} \times \sqrt[3]{\frac{3}{4} \cdot \frac{\text{VMS}}{\pi}}}{\mu_{r_{\text{igp}}}}$ | overall accessibility from all inner points to the center of a polyhedron | 3d-building-metrics |
| Shape            | Exchange                          | BuEx_3D       | ratio     | Building                | mean, std               | $\frac{V_{\text{MS} \cap \text{EVS}}}{V_{\text{MS}}}$ | Measures how much volume inside a sphere is exchanged with the volume outside to create the polyhedro | 3d-building-metrics |
| Shape            | Spin                          | BuSpi_3D       | ratio     | Building                | mean, std               | $\frac{\frac{3}{5} \times \left(\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}\right)^2}{\mu_{r_{\text{igp}}^2}}$ | Focuses on compactness of polyhedron extremities | 3d-building-metrics |
| Shape            | Circumference          | BuCf_3D       | ratio     | Building                | mean, std               | $\frac{4 \pi \times \left(\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}\right)^2}{A_{\text{MS}}}$ | Focuses on the compactness of a polyhedron’s boundary | 3d-building-metrics |
| Shape            | Depth                          | BuDep_3D       | ratio     | Building                | mean, std               | $\frac{4 \times \mu_{\text{MS}_{d_{\text{idgp,b}}}}}{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}$ | Highlights irregular changes along a polyhedron’s boundary | 3d-building-metrics |
| Shape            | Girth                         | BuGir_3D       | ratio     | Building                | mean, std               | $\frac{r_{\text{LIS}}}{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}$ | Measures the thickness of the layer insulating the core from the periphery | 3d-building-metrics |
| Shape            | Dispersion                          | BuDis_3D       | ratio     | Building                | mean, std               | $1 - \frac{\mu_{r_{\text{dev}}}}{r_{\text{ADS}}} = 1 - \frac{\mu_{r_{\text{dev}}}}{\mu_{r_{\text{ibp}}}}$ | Indicates whether a phenomenon propagates equally in all directions | 3d-building-metrics |
| Shape            | Range                      | BuRan_3D       | ratio     | Building                | mean, std               | $\frac{\sqrt[3]{\frac{3 \cdot V_{\text{MS}}}{4 \cdot \pi}}}{r_{\text{SCS}}}$ | Measures the distance between the furthest faces of a polyhedron, sensitive to remote sections | 3d-building-metrics |
| Shape            | Equivalent Prism Index                          | BuEPI_3D       | ratio     | Building                | mean, std               | $\left(\sqrt[3]{\frac{V_{\text{MS}}}{V_{\text{OOBB}}}}\right)^2 \times \frac{A_{\text{OOBB}}}{A_{\text{MS}}}$ | deviation of a polyhedron from an equivalent cuboid by scaling its minimum volume bounding box to match its volume | 3d-building-metrics |
| Shape            | Roughness Index       | BuRI_3D       | ratio     | Building                | mean, std               | $\frac{\mu_{r_{\text{ibp}}}^3}{V_{\text{MS}} + A_{\text{MS}}^{\frac{3}{2}}} \times 48.735$ | Created as a measure of compactness. Advantages: (1) Less sensitive to elongation (aspect ratio of a polyhedron), and (2) more responsive to boundary roughness (intrusions and protrusions) | 3d-building-metrics |
| Shape            | Form Factor            | BuFF_3D       | ratio     | Building                | mean, std               | $\frac{A}{V^{\frac{2}{3}}}$ | compactness of a 3Dobject which attempts to removethe bias introduced by the size ofan object | 3d-building-metrics |
| Distribution        | Shared Walls Area                      | BuSWA_3D       | ratio     | Building                | mean, std               || Area of shared walls| 3d-building-metrics |
| Distribution        | Sky View Factor                     | BuSVF_3D       | ratio     | Building                | mean, std               || | DSM, Ferdi |


### Definitions

Building adjacency refers to how much buildings tend to join together into larger structures and is the number of joined built-up structures divided by number of buildings in the neighbourhood. Mean inter-building distance refers to the mean proximity between adjacent buildings in the neighbourhood. Adjacency is defined by a delaunay triangulation of the building polygons. Shared walls is defined as the length of shared walls of adjacent buildings. 

Orientation is defined as the deviation of orientation of the bounding rectangle from cardinal directions, alignment is the mean deviation of orientation of adjacent buildings (defined by delaunay triangulation) and street alignment is the deviation of the building orientation from the street orientation.

Width of a street profile is the mean length of a street profile sections along street segments. Street openness is the ratio of street profile sections intersecting buildings and it refers to the presence of buildings along the street; that is, wider gaps between buildings will lead to a higher openness. Linearity of a street segment is the ratio of Euclidean distance between the first and the last point of a line and its length https://onlinelibrary.wiley.com/doi/full/10.1111/gean.12302

### 3D Parameters


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

