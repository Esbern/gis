---
title: 
draft: true
tags:
---
**OGC's Simple Feature Access (SFA)** standard defines several key geometry types for [[Dimensions in Geospatial Data|0, 1 and 2-dimensional objects]] used to represent spatial features in geospatial databases and GIS applications. These geometry types form the building blocks for geospatial analysis and data management. Below is a list of the primary geometry types, each linked to a more detailed note:

1. **[[Point]]**: Represents a single location in space (0-dimensional).
2. **[[LineString]]**: A sequence of points connected by straight line segments (1-dimensional).
3. **[[Polygon]]**: A flat shape bounded by a closed LinearRing, which may include holes (2-dimensional).
4. **[[MultiPoint]]**: A collection of Points.
5. **[[MultiLineString]]**: A collection of LineStrings.
6. **[[MultiPolygon]]**: A collection of Polygons.
7. **[[GeometryCollection]]**: A heterogeneous collection that can include any combination of Points, LineStrings, and Polygons.

### **Hierarchy of Geometry Types in Simple Feature Access (SFA)**

The Simple Feature Access (SFA) specification organizes these geometry types into a structured hierarchy, allowing for both simple and complex spatial features to be represented in a consistent manner. Figure 1 below illustrates this hierarchy, which is based on an extended Geometry model.
![[Hierarchy of Geometry Types.png]]
#### **Hierarchy Overview**

- **Point**: The most basic geometry type, representing a single, specific location in space. Points are 0-dimensional objects.

- **Curve**: A 1-dimensional geometry that represents a continuous line, which may be straight or curved.
  - **LineString**: A common type of Curve, defined as a sequence of points connected by straight line segments.
    - **Line**: A specific case of a LineString that is exactly two points long.
    - **LinearRing**: A closed LineString, where the first and last points are the same, typically used as the boundary of a Polygon.

- **Surface**: A 2-dimensional geometry representing an area within a plane.
  - **Polygon**: The most common Surface, consisting of a closed LinearRing boundary with optional interior rings (holes).
  - **PolyhedralSurface**: A 2.5-dimensional geometry composed of multiple Polygon faces, representing a more complex surface.
    - **Triangle**: A simple PolyhedralSurface with exactly three sides.
    - **TIN (Triangulated Irregular Network)**: A surface made up of interconnected triangles used to approximate 3D surfaces.

- **GeometryCollection**: A flexible class that can contain any combination of geometries (Points, LineStrings, Polygons).
  - **MultiPoint**: A collection of Points.
  - **MultiCurve**: A collection of Curves, which can be more specifically a **MultiLineString**.
  - **MultiSurface**: A collection of Surfaces, which can be more specifically a **MultiPolygon**.



For further reading and in-depth examples of each geometry type, refer to the linked notes:
- **[[Point]]**
- **[[LineString]]**
- **[[Polygon]]**
- **[[MultiPoint]]**
- **[[MultiLineString]]**
- **[[MultiPolygon]]**
- **[[GeometryCollection]]** 
