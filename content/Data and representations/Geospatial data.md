---
title: Geospatial data
draft: false
tags:
---
 
According to the [ISO standard 19109:2015](https://www.iso.org/obp/ui/en/#iso:std:iso:19109:ed-2:v1:en), Geographic (geospatial) data is defined as data with **implicit** or **explicit** reference to a location relative to the Earth.
In this context, we can think of the "data" as the **"what"** and the reference to a location relative to the Earth as the **where**. The **when** is also generally considered to be part of the data.

## Implicit Reference to a Location Relative to the Earth.
While this formulation seems strange, it is rather simple. Implicit reference means that the data refers to a location on Earth using some name or code that refers to a location that is explicitly defined somewhere else.
For instance, on the website of the Danish Statistical Office, we can find data describing the number of Contacts with a doctor covered by public health insurance by sex, region and time.  In this data set, the location relative to the Earth is given **implicitly** by the name of the municipality while the data is the columns Male, female and Year.

| Minicipality  | Male    | female  | Year |
| ------------- | ------- | ------- | ---- |
| Compehagen    | 2236743 | 3693462 | 2023 |
| Frederiksberg | 393603  | 681149  | 2023 |
| ....          |         |         |      |

For implicit referencing to work, there must be some standards for how different typical geometries, such as countries, municipalities, etc., are referenced. This is done through national and international  [[spatial coding standards]]. 

### Explicit Reference to a Location Relative to the Earth
The following text is a geojson specification of the location of my office at the campus. 

{ 
	"type": "Feature", "properties": { "What": "Office" }, "geometry": { "type": "Point", "coordinates": [ 12.1413, 55.652] } 
}`

In this geojson text, the location relative to the Earth is given **explicitly** by the coordinates (Longitude and Latitude ). To ensure a correct reference relative to the Earth the coordinates alone, we also need to specify the coordinate system used for the coordinates. In the context of geospatial data, such a coordinate system is named a [[Coordinate Reference System (CRS)]].

In the above example, the coordinates represent a point in 2D, but more complex geometry types (lines and polygons) and higher dimensions can be used. With geospatial data, it is common to talk about [[2D geometries|2D]], [[2.5D geometries|2.5D]], and [[3D geometries]]. If you are new to these concepts, it might be interesting to read about the [[Difference between 2.5 and 3D geometries]].
When it comes to working with more than 2D geometries, there are especially three use cases to take note of, namely:
- [[Representing of terrain]],
- [[Representation of buildings]]
- [[Representing bridges and tunnels]]