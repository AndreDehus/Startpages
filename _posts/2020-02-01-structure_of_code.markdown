---
layout: post
title:  "Structure of the code"
date:   2020-04-04 17:32:15 +0100
categories: jekyll update 
permalink: /:categories/:year/:month/:day/:title
---
In the following the structure of the program code of the particle dispersion simulation is described. 
The program is started with the RunMainView.java file. This file is located in the folder path GULLIview\src. 
It starts a graphical user interface (GUI) with a simulation. After the run, the corresponding shapefiles are created within the input folder.

First of all, a public static void main method is created, which contains the entire simulation process. 
A controller coordinates all single modules and starts the user interface (L.79). 
The time step size of the particle movement can be set manually (L. 85). The MapViewer is used to set the background map of the user interface (L. 91). 
A final LoadingCoordinator is used to load the input files for the simulation. The input files are coordinated by the LoadingCoordinator (L. 98).

Prior to the simulation, a model of the surface runoff and the sewer system must be created. 
This can be done with the program HYSTEM EXTRAN, for example. In the RunMainView the folder path to the Result.idbf of the model must be entered under startFile in line 113. 
The dependent files from the Result.idbf are then searched. If no start file exists, all input files can be entered manually. 
The Loading finisher in line 143 ensures that a simulation run is started automatically after the input files have been successfully loaded (143 - 268). 
The Loading finisher contains different examined scenarios (154 - 233 (why?)). In addition, the examined area is enlarged. 
In the loading finisher the simulation is started by the command control.start(). The set data are loaded in line 271.

After the calculations, the results are written to Shapefiles (shp and geojson). The function for writing the result shapefiles is called after the simulation is finished (278 - 372). 
Afterwards the public static void main method for the simulation is completed. Also the public class RunMainView is finished.

