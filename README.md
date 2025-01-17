<img src="docs/images/pmp-logo-text.png" alt="logo" width="750px"/>

[![build](https://github.com/pmp-library/pmp-library/workflows/build/badge.svg)](https://github.com/pmp-library/pmp-library/actions?query=workflow%3Abuild)

The Polygon Mesh Processing Library is a modern C++ open-source library for
processing and visualizing polygon surface meshes. Its core features are:

- An efficient and easy-to-use mesh data structure
- Canonical mesh processing algorithms
- Ready-to-use visualization tools

![Demo](docs/images/demo.gif)

See [www.pmp-library.org](http://www.pmp-library.org) for more information.

## Getting Started

Clone the repository:

```sh
git clone --recursive https://github.com/pmp-library/pmp-library.git
```

Configure and build:

```sh
cd pmp-library && mkdir build && cd build && cmake .. && make
```

Run the mesh processing app:

```sh
./mpview ../external/pmp-data/off/bunny.off
```

## Usage

```cpp
#include <pmp/SurfaceMesh.h>

int main(void)
{
    pmp::SurfaceMesh mesh;
    mesh.read("input.obj");
    // .. do something with your mesh
    mesh.write("output.obj");
}
```

## Contributing

Contributions to the pmp-library are welcome. See the
[contributing](https://www.pmp-library.org/contributing.html) section of the
[user guide](https://www.pmp-library.org/userguide.html).

## Acknowledgment

If you are using the pmp-library for research projects, please acknowledge its
use by referencing

```tex
@misc{pmp-library,
title  = {The Polygon Mesh Processing Library},
author = {Daniel Sieger and Mario Botsch},
note   = {http://www.pmp-library.org},
year   = {2020},
}
```

## License

The pmp-library is provided under a simple and flexible MIT-style
[license](https://github.com/pmp-library/pmp-library/blob/master/LICENSE.txt),
thereby allowing for both open-source and commercial usage.

## Differences of forked version

A new remeshing approach for HRTF calculation was implemented. Therefore, changes in SurfaceRemeshing.cpp and MeshProcessingViewer.cpp have been made. It is necessary to set the "ear" parameter to either "left" or "right" to determine the ipsilateral ear. If ear = "none" is set, the classic adaptive remeshing is performed.

The new remeshing for HRTF is a combined approach of:

Marion Dunyach u. a. “Adaptive Remeshing for Real-Time Mesh Deforma-
tion”. en. In: Eurographics Short Papers (2013), S. 4. issn: 1017-4656.
url: https://www.researchgate.net/publication/237008692_Adaptive_Remeshing_for_Real-Time_Mesh_Deformation.

Harald Ziegelwanger, Wolfgang Kreuzer und Piotr Majdak. “A priori mesh
grading for the numerical calculation of the head-related transfer functi-
ons”. en. In: Applied Acoustics 114 (Dez. 2016), S. 99–110. issn: 0003-
682X. doi: 10.1016/j.apacoust.2016.07.005. url: http://www.sciencedirect.com/science/article/pii/S0003682X1630192X
