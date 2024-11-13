## isolating towns

1 :  121000, 121110, 122000, 122110, 123000, 123110, 124000, 124110, 125000, 125110
2:  311000, 312000
3: 321000, 321220, 322000, 322220
4:  411000, 412000
5: 420000
all otehr values to 0
processing.run("native:rastercalc", {'LAYERS':['C:/Temp/lu_agg_2021.tif'],'EXPRESSION':'("lu_agg_2021@1" = 121000 OR "lu_agg_2021@1" = 121110 OR "lu_agg_2021@1" = 122000 OR "lu_agg_2021@1" = 122110 OR "lu_agg_2021@1" = 123000 OR "lu_agg_2021@1" = 123110 OR "lu_agg_2021@1" = 124000 OR "lu_agg_2021@1" = 124110 OR "lu_agg_2021@1" = 125000 OR "lu_agg_2021@1" = 125110) * 1 + ("lu_agg_2021@1" = 311000 OR "lu_agg_2021@1" = 312000) * 2 + ("lu_agg_2021@1" = 321000 OR "lu_agg_2021@1" = 321220 OR "lu_agg_2021@1" = 322000 OR "lu_agg_2021@1" = 322220) * 3 + ("lu_agg_2021@1" = 411000 OR "lu_agg_2021@1" = 412000) * 4 + ("lu_agg_2021@1" = 420000) * 5','EXTENT':None,'CELL_SIZE':None,'CRS':None,'OUTPUT':'TEMPORARY_OUTPUT'})
