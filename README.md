# Mars-Project-2021
This project was developed for the Geospatial Programming class of Spring 2020, an international collaboration between two universities, EPF of France and RUDN of Russia
(https://www.epf.fr/ and http://www.rudn.ru)
This project was done by Lisa BUXTON and Romane LAGLAIVE, two students of EPF engineering  school, France, in 4th year in the areospace field. 
The professor in charge of this course is Naci Dilekli. (https://github.com/ndilekli/)



This project aims to find the best places to establish a new civilization on Mars based on the user's conditions.
Here is an explaination on what this project is for and how to use the data and the code we have uploaded. 

First of all, like said above, this project will allow the user to find the best places, based on his conditions, to establish a new civilization on Mars. This project 
combines knowledge on Python programming and ARCGIS sofware. We wrote all of the program in the jupyter notebook.

The user is able to specify conditions on four input parameters we have chosen to be relevant for the purpose of this project : 
- Elevation 
- Temperature
- Ice consitency 
- Luminosity intensity 

The elevation parameter allows the user to choose wether he wants to live in an area with high altitude variations  or in an area with low altitude variations. 

The temperature parameter allows the user to choose a temperature range that is convinient for him to live on Mars. 

The ice consitency parameter allows the user to choose an area with either a high probability of ice on the subsurface or a low probability of ice on the subsurface. 

The luminosity intensity parameter allows the user to choose a sun angle range that is convinient for him to live on Mars. The value of the sun angle is directly linked to
the luminosity intensity (the higher the value of the sun angle, the highest luminosity intensity).

Here is the maps of the input parameters : 

Elevation map : 

![image](https://user-images.githubusercontent.com/80962680/112129372-a650d480-8bc7-11eb-92dd-93c6a1f9eefa.png)

![image](https://user-images.githubusercontent.com/80962680/112119774-f9be2500-8bbd-11eb-9294-9634b80e4f47.png)

This map is an elevation map we have found on https://planetarymaps.usgs.gov, from which we extracted the slope map created within our code. We were not able to upload it here because of the size limit on github, so here is the link of this map : https://planetarymaps.usgs.gov/mosaic/Mars_MGS_MOLA_DEM_mosaic_global_463m.tif

When you have this map, the code will create the slope map you can see just below, specificly within the main fuction named “choose_where_to_live_on_mars”.  
The slope map has values bewteen 0 (light areas) and 90 degrees (darker areas) and shows the elavation angle all over the surface of Mars. The user will, in the code, specify an elevation angle range that is convinient for him. For example, if the user wants to live in a globally flat area, he can choose an angle range with a maximum angle smaller than 5-10 degrees. This step will be seen a bit later in this readme file. 

![image](https://user-images.githubusercontent.com/80962680/112129445-b668b400-8bc7-11eb-94fa-ff2136661e49.png)

![image](https://user-images.githubusercontent.com/80962680/112120209-4e61a000-8bbe-11eb-8c8a-b211a7e5d823.png)

Temperature map :

![image](https://user-images.githubusercontent.com/80962680/112129470-bd8fc200-8bc7-11eb-84da-4538e9ee738c.png)

![image](https://user-images.githubusercontent.com/80962680/112120333-646f6080-8bbe-11eb-8d81-6a702969f249.png)

This map has been found on the NASA website regarding the climate data on Mars. As you can see, the values range bewteen approximately -140 Kelvin (blue areas) and 285 Kelvin (red areas). Unfortunately, this map represents the temperature on the surface of Mars for a specific date as the temperature map for an entire year has not been found. If any of you know how to update this map and make it better, you are pleased to send us a message via our email specified at the end of this file. This map has not been uploaded on the github repositery due to the size limit. We found it on this website : https://data.nas.nasa.gov/mcmc/data_legacygcm.php But because of a numerous operations that has been done on this map to get it right (use of the "NETCDFFILE" on ARCGIS, rescale, shift, the resolution has been upgraded), we would like you to send us a email if you need this map. We will be pleased to send you all the files you need to get this map.


Ice consistency map : 

![image](https://user-images.githubusercontent.com/80962680/112129496-c2ed0c80-8bc7-11eb-9692-06affc6ea936.png)

![image](https://user-images.githubusercontent.com/80962680/112121604-b5338900-8bbf-11eb-8f3e-b3d8b2f70577.png)

This map has been found on https://swim.psi.edu/PilotStudyProducts.php. The values range between -1 and 1. 1 means that there is a high probability to find ice on the subsurface (bewteen 0 and 1 meter under the surface of Mars) and -1 means that there is most likely no ice at this place. This map has been uploaded on the github repositery and every thing you need for this map is in the zip file "ice_con"


Luminosity intensity :

![image](https://user-images.githubusercontent.com/80962680/112129519-c7192a00-8bc7-11eb-93a0-128168b98635.png)

![image](https://user-images.githubusercontent.com/80962680/112121878-03e12300-8bc0-11eb-81a5-a00dba3ff93c.png)

This map shows the luminosity intensity on Mars on a specific time of the year (as the north pole is much more illuminated than the south pole) So here as well this map could be improved. This map has been created within our code based on a grid of points covering all the surface of Mars. The function in our program that creates this map is called "create_maxsolarangle" and the grid you need for the code to run has been uploaded in the github repositery as "mars_fishnet". The values of this map range bewteen 0 (dark areas) and 90 degrees (light areas) and shows the value of the sun angle troughout the day across the surface of Mars. 


For a better visualisation, we also added another map showing the surface of Mars. This map has no data and its only purpose is to get a better visualisation of the final areas selected by the program at the end. We were not able to upload it due to the size limit on github but here is the link of the map if you want to dowload it : https://astrogeology.usgs.gov/search/map/Mars/Viking/MDIM21/Mars_Viking_MDIM21_ClrMosaic_global_232m

![image](https://user-images.githubusercontent.com/80962680/112121942-12c7d580-8bc0-11eb-9081-7dab90b26c84.png)

Now that you have seen all of the four input parameters of our program, it will be explained below how to use those datas within our code and then you will see for some specific values what will be the outputs. You will, then, get a better understanding of the whole project. 

This part will not have many pictures of the code as it is available in the repositery as "Mars2project". So check it up if you want a global visualisation of it.

First of all, we had to import the arcpy library in order to use the ARCGIS tools in python. 
We also created a geodatabase output to store the analysis created within the program. If you want to run the code, it's up to you to keep it, delete it, change the name or the location of it. 
We also specified the workspace location in our code, and we have put all the input data we needed in that workspace location.

The code that creates the luminosity intensity map is called "create_maxsolarangle"
The main function that provides all the analysis and the final output is called "choose_where_to_live_on_Mars"
As an example, here is some conditions related to the input parameters we have specified in the main function : 
![image](https://user-images.githubusercontent.com/80962680/112122269-64706000-8bc0-11eb-816e-3d0b505801bc.png)

From left to right, the user has to specify the maximum and minimum slope angle, the maximum and minimum temperature, maximum and minimum ice consistency and the maximum and minimum sun angle based on what he wants.

Here is the analysis we obtained by running the code with these specific conditions showed above : 

Slope map customized and normalized between [0,100]. For this map the normalization is inversed, so you have as 0 the highest angle (here 10) and as 100 the lowest one (here 0) with the conditions specified regarding the slope angle: 

![image](https://user-images.githubusercontent.com/80962680/112122865-fc6e4980-8bc0-11eb-9fd6-4271f67fa552.png)

![image](https://user-images.githubusercontent.com/80962680/112122837-f6786880-8bc0-11eb-96a0-eb7f0b494d5c.png)

If you zoom on the map, you can see that there are blank areas. Those areas are considered as NO DATA, because it is out of the specified user's range. 

Temperature map customized and normalized between [0,100] with the conditions regarding the temperature: 

![image](https://user-images.githubusercontent.com/80962680/112123091-3b040400-8bc1-11eb-9eef-3c4d40d1fab3.png)

![image](https://user-images.githubusercontent.com/80962680/112123072-35a6b980-8bc1-11eb-80e5-8022ec161e5c.png)

In red you can see the areas with the greatest temperature (here 20°C) and in light blue the ones with the minimum one (here -40°C). It is important to notice that basically on Mars the maximum reached temperature is in average 12°C. So if the user want a maximum temperature greater than 12°C, the result won’t, in any case, be greater than than this value.

Ice consistency map customized and normalized between [0,100] with the conditions regarding the ice consitency:

![image](https://user-images.githubusercontent.com/80962680/112123692-c5e4fe80-8bc1-11eb-800e-dcfe087148f3.png)

![image](https://user-images.githubusercontent.com/80962680/112123635-b796e280-8bc1-11eb-8b51-6dbc2830e578.png)

The dark blue areas show the places where water is the most abundant within the range [0; -1] meter underground whereas the light blue areas illustrate places where water (ice) can be found but in a smaller quantity.

 Luminosity intensity map customized and normalized between [0,100] with the conditions regarding the sun angle:
 
![image](https://user-images.githubusercontent.com/80962680/112124028-32f89400-8bc2-11eb-92a9-249d66b61b40.png)

![image](https://user-images.githubusercontent.com/80962680/112124003-2b38ef80-8bc2-11eb-93f8-b7ac9aae0422.png)

For each map above, the places where there are no areas selected and the background is only the visualization map (or white areas for the slope map) are pixels referred as NO DATA. This way, only the data selected by the user appear on the resulting raster layer and we do not get confused.

With all these outputs, we have been able to create the final output, by adding all of the datas together to create one single map that shows the areas where every condition of the user is fulfilled. 
Here is the map we obtained: 

![image](https://user-images.githubusercontent.com/80962680/112124066-3db32900-8bc2-11eb-9eaa-cda1aa5b9817.png)

At the end, it's up to the user to select the final area among the proposed areas to establish a new civilisation on Mars. 

We hope you enjoy the program and the whole project ! If you need any further information, do not hesitate to contact us either at: romane.laglaive@epfedu.fr or  lisa.buxton@epfedu.fr

Let's explore Mars !
