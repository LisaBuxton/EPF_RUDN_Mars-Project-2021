# Mars-Project-2021
This project developed for the Geospatial Programming class of Spring 2020, an international collaboration between two universities, EPF of France and RUDN of Russia
(https://www.epf.fr/ and http://www.rudn.ru)
This project was done by Lisa BUXTON and Romane LAGLAIVE, two students of EPF engineering  school, France, in 4th year in the areospace field. 
The professor in charge of this course is Naci Dilekli. (https://github.com/ndilekli/)



This project aims to find the best places to establish a new civilization on Mars based on the user's conditions.
Here is an explaination on what this project is for and how to use the data and the code we have uplowded. 

First of all, like said above, this project will allow the user to find the best places, based on his conditions, to establish a new civilization on Mars. This project 
combines knowledge on Python programming and ARCGIS sofware. 
The user is able to specify conditions on four input parameters we have chosen to be relevant for the purpose of this project : 
- Elevation 
- Temperature
- Ice consitency 
- Luminosity intensity 

The elavation parameter allows the user to choose wether he wants to live in an area with high altitude variations  or in an area with low altitude variations. 

The temperature parameter allows the user to choose a temperature range that is convinient for him to live on Mars. 

The ice consitency parameter allows the user to choose an area with either a high probability of ice pn the subsurface or a low probability of ice on the subsurface. 

The luminosity intensity parameter allows the user to choose a sun angle range that is convinient for him to live on Mars. The value of the sun angle is directly linked to
the luminosity intensity (the higher the value of the sun angle, the highest luminosity intensity).

Here is the maps of the input parameters : 

Elevation map : 
This map is a slope map, created within our code based on an elavation map we have found on "this website". We were not able to upload it here because of the size limit on github, so here is the link of this map : 
When you have this map, the code will create the slope map you can see just above within our code, specificly within the main fuction named "choose ???" 
The slope map has values bewteen 0 and 90 degrees and shows the elavation angle all over the surface of Mars. The user will, in the code, specify an elevation angle range that is convinient for him. For example, if the user wants to live in a globally flat area, he can choose an angle range with a maximum angle smaller than 5-10 degrees. This step will be seen a bit later in this readme file. 

Temperature map :
This map has been found on the NASA website regarding the climate data on Mars. As you can see, the values range bewteen approximately -140 Kelvin and 285 Kelvin. Unfortunately, this map represents the temperature on the surface of Mars for a specific date as the temperature map for an entire year has not been found. If any of you know how to update this map and make it better, you are pleased to send us a message via our email specified at the end of this file. This map has not been uplowded on the github repositery due to the size limit. We found it on this website : "?????" But because of a numerous operations that has been done on this map to get it right (use of the "NETCDFFILE" on ARCGIS, rescale, shift, the resolution has been upgraded), we would like you to send us a email if you need this map. We will be pleased to send you all the files you need to get this map.

Ice consistency map : 
This map has been found on the same website as for the temperature map. The values range between -1 and 1. 1 means that there is a high probability to find ice on the subsurface (bewteen 0 and 1 meter under the surface of Mars) and -1 means that there is most likely no ice at this place. This map has been uplowded on the github repositery and every thing you need for this map is in the zip file "ice_con"

Luminosity intensity :
This map shows the luinosity intensity on Mars on a specific time of the year (as the north pole is much more illuminated as for the south pole) So here as well this map could be improved. This map has been created within our code based on a grid of points covering all the surface of Mars. The function in our program that creates this map is called "?????" and the grid you need for the code to run has been uplowded in the github repositery as "mars_fishnet". The values of this map range bewteen 0 and 90 degrees and shows the value of the sun angle troughout the day across the surface of Mars. 


Now that you have seen all of the four input parameters of our program, it will be explained below how to use those datas within our code and then you will see for some specific values what will be the outputs. You will, then, get a better understanding of the whole project. 

This part will not have many pictures of the code as it is available in the repositery as "Mars2project". So check it up if you want a global visualisation of it.

