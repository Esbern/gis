https://github.com/LiangliangNan/PolyFit?tab=readme-ov-file

# Polygonal surface reconstruction from point clouds

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#polygonal-surface-reconstruction-from-point-clouds)

[![](https://github.com/LiangliangNan/PolyFit/raw/main/images/polyfit.png)](https://github.com/LiangliangNan/PolyFit/blob/main/images/polyfit.png)

PolyFit reconstruction pipeline

PolyFit implements the hypothesis and selection based surface reconstruction method described in the following [paper](https://3d.bk.tudelft.nl/liangliang/publications/2017/polyfit/polyfit.html):

```
Liangliang Nan and Peter Wonka. 
PolyFit: Polygonal Surface Reconstruction from Point Clouds. 
ICCV 2017.
```

---

### Obtaining PolyFit

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#obtaining-polyfit)

Prebuilt executable files (for **macOS**, **Linux**, and **Windows**) are available [here](https://github.com/LiangliangNan/PolyFit/releases).

You can also build PolyFit from the source code:

- Clone the repository or download the [source code](https://github.com/LiangliangNan/PolyFit).
    
- Dependencies
    
    - [Qt5](https://www.qt.io/) (v5.12.12, v5.10.1, v5.9.2, and v5.8.0 were tested). Qt is required by the [GUI demo](https://github.com/LiangliangNan/PolyFit/blob/main/code/PolyFit). You should still be able to build the [command-line example](https://github.com/LiangliangNan/PolyFit/blob/main/Example) without Qt.
    - [CGAL](http://www.cgal.org/index.html) (v5.5, v5.0, v4.11.1, and v4.10 were tested).
- Build PolyFit
    
    There are many options to build PolyFit. Choose one of the following (not an exhaustive list):
    
    - Option 1 (purely on the command line): Use CMake to generate Makefiles and then `make` (on Linux/macOS) or `nmake`(on Windows with Microsoft Visual Studio).
        
        - On Linux or macOS
            
            ```
            $ cd PolyFit
            $ mkdir Release
            $ cd Release
            $ cmake -DCMAKE_BUILD_TYPE=Release ..
            $ make
            ```
            

On Windows with Microsoft Visual Studio, use the `x64 Native Tools Command Prompt for VS XXXX` (don't use the x86 one), then

```
$ cd PolyFit
$ mkdir Release
$ cd Release
$ cmake -G "NMake Makefiles" -DCMAKE_BUILD_TYPE=Release ..
$ nmake
```

- - Option 2: Use any IDE that can directly handle CMakeLists files to open the `CMakeLists.txt` in the **root** directory of PolyFit. Then you should have obtained a usable project and just build it. I recommend using [CLion](https://www.jetbrains.com/clion/) or [QtCreator](https://www.qt.io/product). For Windows users: your IDE must be set for `x64`.
        
    - Option 3: Use CMake-Gui to generate project files for your favorite IDE. Then load the project to your IDE and build it. For Windows users: your IDE must be set for `x64`.
        
    
    Don't have any experience with C/C++ programming? Have a look at [How to build PolyFit step by step](https://github.com/LiangliangNan/PolyFit/blob/main/code/How_to_build.md).
    
    **News**: Since Aug. 5, 2019, PolyFit is also available in [CGAL](https://www.cgal.org/). Find more [here](https://www.cgal.org/2019/08/05/Polygonal_surface_reconstruction/).
    

---

### Run PolyFit

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#run-polyfit)

This repository includes a [command-line example](https://github.com/LiangliangNan/PolyFit/blob/main/code/Example) and a [GUI demo](https://github.com/LiangliangNan/PolyFit/blob/main/code/PolyFit).

- For the [commandline example](https://github.com/LiangliangNan/PolyFit/blob/main/code/Example), you can simply build and run it (the path to the input file is hard-coded in the [code](https://github.com/LiangliangNan/PolyFit/blob/main/code/Example/main.cpp)).
- The [GUI demo](https://github.com/LiangliangNan/PolyFit/blob/main/code/PolyFit) provides a user interface with a few buttons (with numbered icons) and screen hints corresponding to these steps. Just click the buttons following the hints.

[![](https://github.com/LiangliangNan/PolyFit/raw/main/images/gui.png)](https://github.com/LiangliangNan/PolyFit/blob/main/images/gui.png)

---

### Data

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#data)

Some test data can be downloaded from the [project page](https://3d.bk.tudelft.nl/liangliang/publications/2017/polyfit/polyfit.html).

More information about the data (e.g., data format) is described [here](https://github.com/LiangliangNan/PolyFit/blob/main/data/ReadMe-data.md).

**Plane extraction**. Incorporating plane extraction adds an unnecessary dependency to more third-party libraries (e.g., [RANSAC](http://cg.cs.uni-bonn.de/en/publications/paper-details/schnabel-2007-efficient/)). Besides, it has some randomness (due to the nature of RANSAC) and the data quality can vary a lot (it should be fine if some regions of the planes are missing). So I isolated this part from this demo version and you're expected to provide the planar segments as input.

You can use my [Mapple](https://3d.bk.tudelft.nl/liangliang/software.html) to extract planes from point clouds. After you load the point cloud, go to the menu _Partition_ -> _Extract Primitives_. To visualize the planes, change the renderer from 'Plain' to 'Group' in the Rendering panel (on the left side of Mapple). You can save the planes in bvg (**B**inary **V**ertex **G**roup) format. The ASCII format vg also works but is slow. Please note, **PolyFit assumes that the model is closed and all necessary planes are provided**.

---

### About the solvers

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#about-the-solvers)

Four solvers, namely Gurobi, SCIP, GLPK, and lp_solve, are provided (with source code) in PolyFit. The Gurobi solver is more efficient and reliable and should always be your first choice. To use Gurobi, you need to install it and also obtain a license (free for academic use) from [here](https://www.gurobi.com/downloads/end-user-license-agreement-academic/). You may also need to modify the path(s) to Gurobi in [FindGUROBI.cmake](https://github.com/LiangliangNan/PolyFit/blob/main/code/cmake/FindGUROBI.cmake), for CMake to find Gurobi. In case you want a fast but open-source solver, please try SCIP, which is slower than Gurobi but acceptable. The GLPK and lp_solve solvers only manage to solve small problems. They are too slow (and thus may not guarantee to succeed). For example the data "Fig1", Gurobi takes only 0.02 seconds, while lp_solve 15 minutes.

**Note for Linux users:** You may have to build the Gurobi library (`libgurobi_c++.a`) because the prebuilt one in the original package might NOT be compatible with your compiler. To do so, go to `src/build` and run `make`. Then replace the original `libgurobi_c++.a` (in the `lib` directory) with your generated file.

### About the timing

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#about-the-timing)

This demo implementation incorporates a progress logger in the user interface. Thus, running times should be (slightly) longer than those reported in our paper.

---

### Citation

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#citation)

If you use the code/program (or part) of PolyFit in scientific work, please cite our paper:

```bibtex
@inproceedings{nan2017polyfit,
  title={Polyfit: Polygonal surface reconstruction from point clouds},
  author={Nan, Liangliang and Wonka, Peter},
  booktitle={Proceedings of the IEEE International Conference on Computer Vision},
  pages={2353--2361},
  year={2017}
}
```

---

### License

[](https://github.com/LiangliangNan/PolyFit/blob/main/ReadMe.md#license)

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License or (at your option) any later version. The full text of the license can be found in the accompanying LICENSE file.

---

Should you have any questions, comments, or suggestions, please contact me at: [liangliang.nan@gmail.com](mailto:liangliang.nan@gmail.com)

**_Liangliang Nan_**

[https://3d.bk.tudelft.nl/liangliang/](https://3d.bk.tudelft.nl/liangliang/)

July 18, 2017

Copyright (C) 2017