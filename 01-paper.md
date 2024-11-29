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

## Background

Building adjacency refers to how much buildings tend to join together into larger structures and is the number of joined built-up structures divided by number of buildings in the neighbourhood. Mean inter-building distance refers to the mean proximity between adjacent buildings in the neighbourhood. Adjacency is defined by a delaunay triangulation of the building polygons. Shared walls is defined as the length of shared walls of adjacent buildings. 

Orientation is defined as the deviation of orientation of the bounding rectangle from cardinal directions, alignment is the mean deviation of orientation of adjacent buildings (defined by delaunay triangulation) and street alignment is the deviation of the building orientation from the street orientation.

Width of a street profile is the mean length of a street profile sections along street segment. Street openness is the ratio of street profile sections intersecting buildings and it refers to the presence of buildings along the street; that is, wider gaps between buildings will lead to a higher openness. Linearity of a street segment is the ratio of Euclidean distance between the first and the last point of a line and its length https://onlinelibrary.wiley.com/doi/full/10.1111/gean.12302

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

The communication and collaboration tools that we are building in the Project Jupyter are built to follow the FORCE11 recommendations [](doi:10.4230/DAGMAN.1.1.41). Specifically:

1. rethink the unit and form of scholarly publication;
2. develop tools and technologies to better support the scholarly lifecycle; and
3. add data, software, and workflows as first-class research objects.

By bringing professional, high-quality tools for science communication into the research lifecycle, we believe we can improve the collection and preservation of scholarly metadata (citations, cross-references, annotations, etc.) as well as open up new ways to communicate science with interactive figures & equations, computation, and reactivity.

The tools that are being built by the Project Jupyter are focused on introducing a new Markup language, MyST (Markedly Structured Text), that works seamlessly with the Jupyter community to enhance and promote a new path to document creation and publishing for next-generation scientific textbooks, blogs, and lectures. Our team is currently supported by the [Sloan Foundation](https://sloan.org), ([Grant #9231](https://sloan.org/grant-detail/9231)).

MyST enables rich content generation and is a powerful format for scientific and technical communication. JupyterBook uses MyST and has broad adoption in publishing tutorials and educational content focused around Jupyter Notebooks.

> The components behind Jupyter Book are downloaded 30,000 times a day, with 750K downloads last month.

The current toolchain used by [JupyterBook] is based on [Sphinx], which is an open-source documentation system used in many software projects, especially in the Python ecosystem. `mystjs` is a similar tool to [Sphinx], however, designed specifically for scientific communication. In addition to building websites, `mystjs` can also help you create scientific PDFs, Microsoft Word documents, and JATS XML (used in scientific publishing).

`mystjs` uses existing, modern web-frameworks in place of the [Sphinx] build system. These tools come out-of-the-box with prefetching for faster navigation, smaller network payloads through modern web-bundlers, image optimization, partial-page refresh through single-page application. Many of these features, performance and accessibility improvements are difficult, if not impossible, to create inside of the [Sphinx] build system.

In 2022, the Executable Books team started work to document the specification behind the markup language, called [myst-spec](https://github.com/jupyter-book/myst-spec), this work has enabled other tools and implementations in the scientific ecosystem to build on MyST (e.g. [scientific authoring tools](https://curvenote.com/for/writing), and [documentation systems](https://blog.readthedocs.com/jupyter-book-read-the-docs/)).

The `mystjs` ecosystem was developed as a collaboration between [Curvenote], [2i2c] and the [ExecutableBooks] team. The initial version of `mystjs` was originally release by [Curvenote] as the [Curvenote CLI](https://curvenote.com/docs/cli) under the MIT license, and transferred to the [ExecutableBooks] team in October 2022. The goal of the project is to enable the same rich content and authoring experiences that [Sphinx] allows for software documentation, with a focus on web-first technologies (Javascript), interactivity, accessibility, scientific references (e.g. DOIs and other persistent IDs), professional PDF outputs, and JATS XML documents for scientific archiving.

## MyST Project

In this paper we introduce `mystjs`, which allows the popular MyST Markdown syntax to be run directly in a web browser, opening up new workflows for components to be used in web-based editors, [directly in Jupyter](https://github.com/jupyter-book/jupyterlab-myst) and in JupyterLite. The libraries work with current MyST Markdown documents/projects and can export to [LaTeX/PDF](https://myst.tools/docs/mystjs/creating-pdf-documents), [Microsoft Word](https://myst.tools/docs/mystjs/creating-word-documents) and [JATS](https://myst.tools/docs/mystjs/creating-jats-xml) as well as multiple website templates using a [modern](https://myst.tools/docs/mystjs/accessibility-and-performance) React-based renderer. There are currently over 400 scientific journals that are supported through [templates](https://github.com/myst-templates), with [new LaTeX templates](https://myst.tools/docs/jtex/create-a-latex-template) that can be added easily using a Jinja-based templating package, called [jtex](https://myst.tools/docs/jtex).

In our paper we will give an overview of the MyST ecosystem, how to use MyST tools in conjunction with existing Jupyter Notebooks, markdown documents, and JupyterBooks to create professional PDFs and interactive websites, books, blogs and scientific articles. We give special attention to the additions around structured data, standards in publishing (e.g. efforts in representing Notebooks as JATS XML), rich [frontmatter](https://myst.tools/docs/mystjs/frontmatter) and bringing [cross-references](https://myst.tools/docs/mystjs/cross-references) and [persistent IDs](https://myst.tools/docs/mystjs/external-references) to life with interactive hover-tooltips ([ORCID, RoR](https://myst.tools/docs/mystjs/frontmatter), [RRIDs](https://myst.tools/docs/mystjs/external-references#research-resource-identifiers), [DOIs](https://myst.tools/docs/mystjs/citations), [intersphinx](https://myst.tools/docs/mystjs/external-references#intersphinx), [wikipedia](https://myst.tools/docs/mystjs/external-references#wikipedia-links), [JATS](https://myst.tools/docs/mystjs/typography), [GitHub code](https://myst.tools/docs/mystjs/external-references#github-links), and more!). This rich metadata and structured content can be used directly to improve science communication both through self-publishing books, blogs, and lab websites — as well as journals that incorporate Jupyter Notebooks.

## Features of MyST

MyST is focused on scientific writing, and ensuring that citations are first class both for writing and for reading (see [](#citations))..

:::{figure} ./images/citations.png
:label: citations
Citations are rendered with a popup directly inline.
:::

MyST aims to show as much information in context as possible, for example, Figure 2 shows a reading experience for a referenced equation: you can immediately **click on the reference**, see the equation, all without loosing any context -- ultimately saving you time. [](doi:10.1145/3411764.3445648) found that these ideas both improved the overall reading experience of articles as well as allowed researchers to answer questions about an article **26% faster** when compared to a traditional PDF!

![](./images/9bpjlb.gif)
**Figure 2**: In context cross-references improve the reading experience.

One of the important underlying goals of practicing reproducibility, sharing more of the methods and data behind a scientific work so that other researchers can both verify as well as build upon your findings. One of the exciting ways to pull for reproducibility is to make documents directly linked to data and computation! In Figure 3, we are showing outputs from a Jupyter Notebook directly part of the published scientific narrative.

![](./images/9bpjlb.gif)
**Figure 3**: Embedding data, interactivity and computation into a MyST article.

To drive all of these features, the contents of a MyST document needs to be well defined. This is critical for powering interactive hovers, linked citations, and compatibility with scientific publishing standards like the Journal Article Metadata Tag Suite (JATS). We have an emerging specification for MyST, [`myst-spec`](https://spec.myst.tools), that aims to capture this information and transform it between many different formats, like PDF, Word, JSON, and JATS XML (Figure 4). This specification is arrived at through a community-centric MyST Enhancement Proposal ([MEP](https://compass.executablebooks.org/en/latest/meps.html)) process.

![](./images/structured-data.gif)
**Figure 4**: The data behind MyST is **structured**, which means we can transform it into many different document types and use it to power all sorts of exciting features!

One of the common forms of scientific communication today is through PDF documents. MyST has excellent support for creating PDF documents, using a data-driven templating library called `jtex`. The document in Figure 5 was created using MyST!

![](./images/pdf-two-column.png)
**Figure 5**: A PDF rendering through MyST.

## Conclusion

There are many opportunities to improve open-science communication, to make it more interactive, accessible, more reproducible, and both produce and use structured data throughout the research-writing process. The `mystjs` ecosystem of tools is designed with structured data at its core. We would love if you gave it a try -- learn to get started at <https://myst.tools>.




[2i2c]: https://2i2c.org/
[curvenote]: https://curvenote.com
[docutils]: https://docutils.sourceforge.io/
[executablebooks]: https://executablebooks.org/
[jupyterbook]: https://jupyterbook.org/
[jupyterlab-myst]: https://github.com/jupyter-book/jupyterlab-myst
[sphinx]: https://www.sphinx-doc.org/
