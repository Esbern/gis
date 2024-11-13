This note describes the database structure of the GEOIlUM query database. While it might be desirable to implement the database in something like a GeoPackage file this is not possible since the model relies heavily on the use of queries and user asses rights. For performance reasons all GEOILUM data must reside in the same database container where different users and organizations can have there own schemas.
As a minimum the database must have two schemas/users  one named GEOILUM that represents the "Official data and queries" and a user that can read but not write from this schema. In a multi user enviorment it is recomended to have at least one thired user representing the organisation that may containg data and queryes availabul to all users within the organisation. 
GeoILUM
	Region_sj
		Natur_miljø
	Danske_Vandværker
	Kommune XXX
		

The base geometry table (Geotopes in the GeoILUM schema) only includes the Geotopes, and a id.
A organization can for efficiency reasons chose to have there own spatially subsites base geometry table.
All base geometry table have the following metadata in ther description :
{"project" : **"GeoILUM"**,
"role" : **"Base geometry table"**,
"spatial_subset" : "Region_sj",
"purpose" : "General geotope delineation"
"designd_by": "GeoILIM",
"version": "0.1",
"creation_parameters" :{}
}


All attributes are stores as "attribute collections"
A attribute collection can be a table or a  (martialized) view
A "attribute collections" contains a geotope_id and one or more descriptive attributes of the  geotope. A "attribute collections" does not have to include the id of all geotopes and in this way can function as a spatial subset.
All "attribute collections" have the following metadata stored in their description
{project : **"GeoILUM"**,
role : **"Attribute collection"**,
spatial_subset : "Region_sj",
purpose : "General attribute description",
Designd_by: GeoILIM,
Version: 0.1,
Creation_parameters:{}
}
All attributes in these tables have the following JSON description

{"project": "GeoILUM",
"role" : "Attribute",
"description" : "General attribute description",
"link" : "https://ruc.dk",
"Designd_by": "GeoILIM",
"Version": "0.1",
"Creation_parameters":{}
}

if it is a key for joining to the spatial data then
"role" : "Key",

"description" : "beskrive tilgængelig vand i rodzonen",

{"project": "GeoILUM",
"role" : "Attribute collection",
"spatial_subset" : "Region_sj",
"purpose" : "Vand i rodzones  som delpotientiale for hvede",
"Designd_by": "Jens",
"Version": "0.1",
"Creation_parameters":{"function":"Piecewise linear", "parameters" : {"property":"winter_predict_mean","array":[[0, 0], [90, 10], [100, 80], [400, 100], [780, 0]]}}
}