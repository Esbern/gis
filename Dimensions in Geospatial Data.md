---
title: Dimensions in Geospatial Data
draft: false
tags:
---
### **Note: Dimensions in Geospatial Data**

In geospatial data, understanding dimensions is critical to accurately modeling, analyzing, and visualizing spatial features. A key distinction to make is between the **dimensionality of the geometric object** and the **dimensionality of the space** in which these objects are defined. This distinction is essential for correctly interpreting geospatial data, particularly when working with advanced 3D models.

### **Dimensionality of Geometric Objects**

1. **0-Dimensional Objects (Points)**:
   - **Definition**: A point is a 0-dimensional geometric object representing a single, specific location in space without any extension in any direction.
   - **Examples**: Points can represent locations such as cities, trees, or sensor stations.
   - **Dimensionality vs. Space**: A point remains a 0-dimensional object whether it's defined in 2D space (X, Y) or 3D space (X, Y, Z).

2. **1-Dimensional Objects (Lines and Curves)**:
   - **Definition**: LineStrings and curves are 1-dimensional objects that have length but no area or volume.
   - **Examples**: Roads, rivers, or pipelines are typically represented as LineStrings.
   - **Dimensionality vs. Space**: A LineString is 1D regardless of whether it's defined in 2D or 3D space. The Z value, if present, adds elevation data but does not change the dimensionality of the object itself.

3. **2-Dimensional Objects (Polygons and Surfaces)**:
   - **Definition**: Polygons are 2-dimensional objects that represent area without volume. Surfaces like TINs (Triangulated Irregular Networks) or PolyhedralSurfaces extend this concept into representing surfaces in 3D space.
   - **Examples**: Land parcels, building footprints, or lake surfaces are typically represented as Polygons. TINs represent terrain or other continuous surfaces in 3D.
   - **Dimensionality vs. Space**: Polygons and surfaces are inherently 2-dimensional, even when embedded in 3D space. They describe an area on a plane, with TINs and PolyhedralSurfaces specifically used to model surfaces that extend through 3D space.

4. **2.5D Objects (TINs and PolyhedralSurfaces)**:
   - **Definition**: The term "2.5D" is used informally to describe objects that are 2-dimensional but are embedded in 3D space, often used to model surfaces like terrain. These objects have length and area but do not represent full volumetric data.
   - **Examples**: **TINs** (Triangulated Irregular Networks) and **PolyhedralSurfaces** are typical examples of 2.5D objects. A TIN, for instance, is used to model the Earth's surface, representing elevation in 3D space while still being a 2D object in terms of its structure.
   - **Dimensionality vs. Space**: While these objects exist in 3D space (X, Y, Z), they only represent surfaces (2D). This makes them useful for applications like terrain modeling or surface analysis, where elevation or depth is important but full 3D volumetric representation is not required.

5. **3-Dimensional Objects (Solids and Complex 3D Structures)**:
   - **Definition**: 3-dimensional objects, such as **Solids** in GML and CityGML, represent volumetric data, meaning they have length, area, and volume. These objects are fully 3D and are used to model real-world features with depth.
   - **Examples**: Buildings modeled as **Solids** in CityGML, where every element of the structure, including interior and exterior spaces, is represented in 3D. Additionally, **MultiSurface** objects can be used to model complex surfaces that define the boundaries of 3D volumes.
   - **Dimensionality vs. Space**: Solids and 3D objects extend in all three dimensions (X, Y, Z), making them true representations of volumetric features.

### **Dimensionality of Space**

The dimensionality of space refers to the number of coordinates required to define the position of a point within that space:

- **2D Space (X, Y)**: In 2D space, every point is defined by two coordinates—X (horizontal) and Y (vertical). This space is typically used for flat maps and is the default for most geospatial operations.
- **3D Space (X, Y, Z)**: In 3D space, every point is defined by three coordinates—X (horizontal), Y (vertical), and Z (elevation or depth). This space is used for modeling real-world features that have height or depth.

### **Overlay Analysis and Dimensionality**

In geospatial analysis, the dimensionality of objects affects how spatial operations like overlay analysis are performed:

- **2D Overlay Analysis**: Traditionally, overlay operations like intersection and union are performed in 2D space, where only the X and Y coordinates are considered. Z values (elevation) are ignored, making these operations suitable for flat or "2.5D" surfaces but inadequate for full 3D analyses.

- **3D Overlay Analysis**: With advancements in GIS technology, some platforms now support 3D spatial operations. For example, ArcGIS Pro offers a 3D intersection tool that considers the Z dimension, allowing for true 3D spatial analysis. This is essential for applications like urban planning, where different features may overlap in X and Y but exist at different elevations (e.g., tunnels and bridges).

### **3D Geometries in Geospatial Data**

While traditional GIS has largely focused on 2D and 2.5D (e.g., surfaces in 3D space like TINs), modern geospatial applications increasingly require full 3D representations. Standards like GML, CityGML, and 3D Tiles provide robust frameworks for handling these complex geometries:

1. **GML and CityGML**:
   - **Solids**: In CityGML, a Solid is a 3D geometry representing a fully enclosed volume. These are used to model buildings, tunnels, and other infrastructure elements in detail, including their interior spaces.
   - **MultiSurface**: A MultiSurface in GML and CityGML is a collection of surfaces that together form the boundary of a solid object, such as the walls, roof, and floor of a building.
   
   CityGML is specifically tailored to represent the 3D built environment, supporting detailed urban models that include both the exteriors and interiors of buildings.

2. **3D Tiles**:
   - **Definition**: 3D Tiles is an OGC standard designed for streaming and rendering large-scale 3D geospatial datasets, such as city models, terrain, and point clouds.
   - **Application**: 3D Tiles are used in web-based platforms like **CesiumJS** to visualise complex 3D environments. This format is optimised for performance, enabling the efficient display of massive 3D datasets in real-time applications.

### **Conclusion**

Understanding the distinction between the dimensionality of geometric objects and the dimensionality of space is crucial for working with geospatial data, especially as the field increasingly embraces 3D modelling. While a point remains a 0-dimensional object regardless of whether it's placed in 2D or 3D space, the space in which it exists dictates how it can be analysed and visualised. The development of standards like GML, CityGML, and 3D Tiles reflects the growing need for robust, standardised approaches to handling complex 3D geometries in geospatial contexts, enabling more accurate and meaningful analyses across various applications.

