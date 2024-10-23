The concept is that the plugin starts by searching all Postgres database connections for connections named GEOILUM_XXX for instance GEOILUM_Jens. The user can then choose from a dropdown which connection to use.

This is the code for finding the GEOILUM connections

```Python

from qgis.core import QgsProviderRegistry, QgsDataSourceUri

# Get a list of all database connections known to QGIS
connections = QgsProviderRegistry.instance().providerMetadata('postgres').connections()

# Loop through all the connections and print their details
for conn_name, conn_info in connections.items():
    uri = QgsDataSourceUri(conn_info.uri())
    
    # Check if the connection name starts with GEOILUM_
    if conn_name.startswith('GEOILUM_'):
        print(f"Connection Name: {conn_name}")
        print(f"Host: {uri.host()}")
        print(f"Database: {uri.database()}")
        print(f"User: {uri.username()}")
        print(f"Port: {uri.port()}")
        print(f"SSL Mode: {uri.sslMode()}")
        print("---")

```