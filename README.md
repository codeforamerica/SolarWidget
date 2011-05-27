==========================
Solar Radiation Application for ArcGIS Viewer for Flex 2.3.1
==========================

Introduction:
-------------

The ArcGIS Spatial Analyst extension provides tools to perform solar radiation analysis. 
An overview of these tools can be found at
[http://Webhelp.esri.com/arcgisdesktop/9.3/index.cfm?TopicName=An_overview_of_the_Solar_Radiation_tools]. 
Included with this download is a geoprocessing model in which you can point to your own data. This document guides you through configuration of the Flex Web application with use of the geoprocessing service that is to be published in the above document.


Requirements:
-------------

To run the geoprocessing model through the Solar Radiation widget with your own data, you will need to first author and publish the model in ArcGIS Desktop with the Spatial Analyst extension. 
Then, to run it through the Web application, you will need ArcGIS Server with the Spatial Analyst extension. 
All tools assume ArcGIS 9.3 or higher. Please see the SolarGeoprocessingWidget.pdf for instructions on configuring the geoprocessing model against your own data.


Directions:
-----------

Configuration instructions can be found in Documents\SolarGeoprocessingModel_Configuration.pdf.

Read the SolarGeoprocessingModel_Configuration.pdf first which will allow you to set up the geoprocessing service that is needed.  

Next, follow the these instructions to configure the Solar Widget.

Step 1: Download the sample Flex viewer from the ESRI Resource Center and deploy it per the included instructions. 
The sample viewer and instructions can be found at [http://resources.arcgis.com/content/arcgis-flex-viewer-download]

Step 2: Merge the contents of the bin directory with the deployed version of the sample Flex viewer. This can be done by copying the contents of SolarRadiationWidget\bin and pasting into the contents of the sample viewer from step 1, choosing to overwrite all contents.

Step 3: Update your config.xml file to add the widget
  <widget label="Solar Radiation Widget"
	icon="assets/images/i_solar.png"
	config="widgets/SolarRadiation/SolarRadiationWidget.xml"
	url="widgets/SolarRadiation/SolarRadiationWidget.swf"/>

Step 4: Test the application in a browser by entering the URL to the index.html page. If you close the widget (clicking x in the upper right of the widget) and want it to appear again, it will be listed under the Tools menu.
Note: The Solar Radiation widget will not work at this point. You must configure the model and geoprocessing service using your
own data.

Step 5: Configure the Solar Radiation widget to use your map and geoprocessing services. 
Open the SolarRadiationWidget.xml file found in <FlexApplicationPath>\widgets. 
You will need to edit the following services: 

Rooftoplayer—This needs to point to a layer within a map service that has building footprints and the associated interval values burned into it. 

See the Preprocessing data section in the SolarGeoprocessingModel_Configuration.pdf guide on how to obtain the interval values. 

If you do not have building footprints, you can leave the tag blank, which will remove the button from the widget to select an existing building.
  <rooftoplayer> </rooftoplayer>

Gpservice — This needs to point to the geoprocessing service that gets created from publishing the geoprocessing model as mentioned in the SolarGeoprocessingModel_Configuration.pdf guide. 

The tag should look similar to the following: 
  <gpservice>http://yourservernamehere/ArcGIS/rest/services/ GPServer/RooftopSolarCalculator</gpservice>


GeometryService — Currently, this is pointing to an ArcGIS Online sample server. 
You should create your own geometry service on ArcGIS Server as discussed at [http://Webhelp.esri.com/arcgisserver/9.3/dotNet/index.htm#geometry_service.htm].


Conversionfactor — Currently, this is set to 0.092903, which represents the conversion of one square foot to one square meter. The default unit is in square meters. The default value would assume the base data is in feet (typical for a State Plane projection). If your base data unit of measurement is in meters, you can set the conversion factor to 0.


Directions to import the Solar Radiation widget in source code 
-------

Step 1: Download the sample Flex viewer from the ESRI Resource Center and create a new Flex Builder project per the included instructions. 

Step 2: Merge the contents of the src directory with the source code of the sample Flex viewer. 

Step 3: In Flex Builder, from the Project menu, select Properties. 

In the Flex Modules Properties section, add SolarRadiationWidget as a module so that it will be compiled separately as SWF.
See the Developers Guide for additional information. 

Step 4: Test the application by running the project. The Solar Radiation widget should be listed under the Tools menu with the label Solar Radiation, as specified in the configuration file.

Modifying the widget 
------

You may want to modify the source code of the widget as it applies to your city. If you click on the Chart icon for the widget, a summary of the building or polygon is shown. You may want to remove or modify some of these values, depending on your location.


================
More Information
================

Flex Viewer: http://help.arcgis.com/en/webapps/flexviewer/index.html
Flex API http://help.arcgis.com/en/webapi/flex/index.html

Flex Viewer License agreement at http://www.esri.com/legal/pdfs/mla_e204_e300/english.pdf

[![Code for America Tracker](http://stats.codeforamerica.org/codeforamerica/solarboston.png)](http://stats.codeforamerica.org/projects/solarboston)


