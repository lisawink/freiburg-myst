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

### Urban form parameters
| **Category**    | **Parameter**                            | **Abbrev.** | **Unit**  | **Element**            | **Aggregation**         | **Equation**                           | **Description** |
|------------------|-----------------------------------------|-------------|-----------|------------------------|--------------------------|-----------------------------------------|--------------------------|
| Dimension        | Building Area                           | BuAre       | m²        | Building                | count, sum, mean, std    |                                         | |
| Dimension        | Building Height                         | BuHt        | m²        | Building                | mean, std     |                                         | |
| Dimension        | Building Perimeter                      | BuPer       | m         | Building                | mean, std     |                                        | |
| Dimension        | Longest Axis Length                     | BuLAL       | m         | Building                | mean, std     |  $max(axis_1,axis_2,...,axis_n)$      | Length of the longest axis of object |
| Dimension        | Centroid Corner Distance                | BuCCD       | m         | Building                | mean, std     |                                         | Distance between centroid and corner |
| Dimension        | Number of Corners                       | BuCor       | count     | Building                | mean, std     |                                         | |
| Dimension        | Courtyard Area                          | CyAre       | m         | Building                | sum, mean, std     |                                         | |
| Dimension        | Courtyard Index                         | CyInd       | ratio     | Building                | mean, std             |                                       | Area of courtyard over total area of building |
| Shape            | Compactness Weighted Axis               | BuCWA       | m         | Building                | mean, std                    | $d_i = (\frac{\pi}{4}-\frac{16area_i}{perimeter_i^{2}})$ | Longest axis length weighted by compactness |
| Shape            | Convexity                               | BuCon       | ratio     | Building                | mean, std        |  $\frac{\text{area}}{\text{area of convex hull}}$        | |
| Shape            | Elongation                              | BuElo       | ratio     | Building                | mean, std     | $\frac{\frac{p - \sqrt{p^2 - 16a}}{4}}{\frac{p}{2} - \frac{p - \sqrt{p^2 - 16a}}{4}}$ | Elongation of minimum bounding rectangle |
| Shape            | Equivalent Rectangular Index            | BuERI       | ratio     | Building                | mean, std   | $\sqrt{\frac{\text{area}}{\text{area of bounding rectangle}}} \cdot \frac{\text{perimeter of bounding rectangle}}{\text{perimeter}}$ |
| Shape            | Facade Ratio                            | BuFR        | ratio     | Building                | mean, std               | $area/perimeter$                       |
| Shape            | Form Factor                             | BuFF        | ratio     | Building                | mean, std               | $\frac{(perimeter*height)+area}{volume^{2/3}}$ | |
| Shape            | Fractal Dimension                       | BuFD        | ratio     | Building                | mean, std               | $\frac{2\log\left(\frac{\text{perimeter}}{4}\right)}{\log(\text{area})}$  | |
| Shape            | Rectangularity                          | BuRec       | ratio     | Building                | mean, std               | $\frac{\text{area}}{\text{area of minimum bounding rectangle}}$ | |
| Shape            | Shape Index                             | BuShI       | ratio     | Building                | mean, std               | $\frac{\sqrt{\frac{\text { area }}{\pi}}}{0.5 * \text { longest axis }}$ | |
| Shape            | Square Compactness                      | BuSqC       | ratio     | Building                | mean, std               | $\left(\frac{4 \sqrt{\text { area }}}{\text { perimeter }}\right)^2$ | |
| Shape            | Squareness                              | BuSqu       | deg       | Building                | mean, std               |                                         | Mean deviation of angles at corners from 90 degrees |
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


