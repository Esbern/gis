---
title: From Reality to Geospatial Data
draft: false
tags:
  - moc
  - Application
---
 The purpose of this [[This site is a Digital Garden#Map of Contents (MOC)|MOC]] is to guide you through what can seem a rather daunting journey from "reality" to geospatial data. 
 Before starting on this journey, it is important to understand the basics of geospatial modelling of reality.
## Basic principals of geospatial modelling of Reality
 
The two basic principles for the representation of geospatial data are :
 - [[Entity-based modelling]].
 - [[Field-based modelling]].
 As we move on down the winding way to representing reality using geospatial data, it is important to remember these basic principles of modelling. It is also important to remember that although they might seem mutually excluding, it is often a design choice which principal to choose. For instance, terrain as elevation over sea level can be represented as a **continuous field** or as discrete **entities** such as hills,  plateaus and walls, each with an attribute defining the elevation over sea level.
## Defining the world of observation
Talking about reality is always scary, for what is reality? Instead of trying to define "reality" that has so many everyday meanings, we will substitute the term "reality" with the term "[[world of observation]]", thereby enabling us to focus on defining the aspects relevant to the context of geospatial data.

## Defining the world of discourse
While an individual [[GIS project]] does not define its own world of observation, which is a common abstract term, each project defines its own [[world of discourse]] that defines who and what we see in the [[world of observation]]. Defining the [[world of discourse]] or a [[GIS project]] is one of the most important elements in writing the [[Design Rationale]] of the project since it defines which information in terms of data is to be the foundation of the project. 
The [[world of discourse]] is sometimes also called the conceptual data model for the project and is typicaly defined in terms of a [[Ontology]]