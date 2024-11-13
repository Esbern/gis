---
title: 
draft: true
tags:
---
 
he aim of the 3D City Database is to provide a high-performance and scalable datastore for virtual 3D City Models also known as Digital (Geo-)Twins. The database schema implements and is fully compliant with the conceptual data model of the OGC standard CityGML 2.0. This allows you to store, manage, analyze and even visualize your 3D geodata based on an open and interoperable standard rather than to seal it in proprietary data silos.
Starting from release 3.3.0, the 3DCityDB software bundle contains the **CesiumJS-based 3D viewer called “3DCityDB-Web-Map-Client”** which facilitates the interactive visualization and exploration of 3D city models over the internet within web browsers on desktop and mobile computers. **The most significant new functionality in release 4.0.0 is the support of CityGML Application Domain Extensions (ADEs)**. ADEs extend the CityGML data model by domain specific object types, attributes, and relations.

Semantic 3D city models are employed for many different applications from diverse domains like energetic, environmental, driving, and traffic simulations, as-built building information modeling (as-built BIM), asset management, and urban information fusion. In order to store and exchange application specific data aligned and integrated with the 3D city objects, the CityGML data model can be extended by new feature types, attributes, and relations using the CityGML ADE mechanism. ADEs are specified as (partial) GML application schemas using the modeling language XML Schema. Starting from release 4.0.0 the 3DCityDB database schema can be dynamically extended by arbitrary ADEs like the Energy ADE, UtilityNetwork ADE, Dynamizer ADE, or national CityGML extensions like IMGeo3D (from The Netherlands).