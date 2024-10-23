
The concept is here to use an OTP planner as a service and use a QGIS plugin to call the OTP systematically with sources and destinations from two GIS layers.

To generalise this the user must create a variable in QGIS named OTP_adress that points to the service endpoint

![[OTP_QGIS.png]]Once this is done, the plugin uses the following code to read the address and check for a connection.

```Python

# Accessing the variable from QGIS global variables
otp_address = QgsExpressionContextUtils.globalScope().variable('OTP_adress')

# Print the value of the variable
print(otp_address)
```