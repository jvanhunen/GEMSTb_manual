# Digitising mine plans with QGIS

## Preparation

To use and set up QGIS for the purpose of mine plan digitisation, the following tasks are needed:

1.  Install the latest stable version: for this, the user is referred to [the QGIS website](https://docs.qgis.org/3.34/en/docs/user_manual), Section 5.1.

2.  Start QGIS

3.  Basemaps: QGIS doesn’t start automatically with a basemap. The first time, you need to install basemaps:

    1.  Install a plugin to enable that. Choose top menu "Plugins" $\rightarrow$ "Manage and Install plugins", and find "QuickMapServices" in list on the left. Install and enable the plugin

    2.  Install the main list of standard maps: Choose top menu "Web" $\rightarrow$ QuickMapServices $\rightarrow$ Settings. Click on tab "More Services", and choose "Get contributed pack".

    3.  Once basemaps are installed, choose your basemap from top menu "Web" $\rightarrow$ QuickMapServices.

4.  Set the coordinate system to an orthogonal British National Grid system (or equivalent if working on areas outside the UK): at the bottom-right of the QGIS window, click on the CRS item ("Current CRS: ..."). In ’Filter’, type "EPSG:27700", and choose "EPSG:27700 - OSGB36 / British National Grid", then click "OK".

## Georeferencing mine plans

Now import the mine plan to be georeferenced:

1.  Top menu "Layer" $\rightarrow$ "Georeferencer". This opens a new window.

2.  Choose the map file to be imported: top menu "File" $\rightarrow$ "Open Raster …". This opens the map in this Gereferencer window.

3.  Go to top menu "Settings" $\rightarrow$ "Transformation Settings". Set the “Transformation Type” to "Polynomial 1" (default is "Linear" which does not work, since it doesn’t rotate maps).

4.  Choose the "Output file" where the georeferenced version of the file will be stored.

5.  Tick the box "Use o for Transparency when needed": this will avoid a black ‘frame’ around the map if the map needs rotation once it is overlain onto the basemap.

6.  Leave the other options as default and click "OK".

7.  Set at least 4 control points, which are points on the map and the corresponding point on the basemap:

    1.  Zoom in/out of the map in the georeferencer (without clicking!) to the location of the first control point

    2.  Click on the map to define the first control point

    3.  Now a new window "Enter Map Coordinates" appears: click on "From Map Canvas" in bottom-left to choose the corresponding point on the basemap, and this will redirect you to the basemap in the main QGIS window.

    4.  Zoom in/out (again without clicking) to the corresponding point on the basemap and click at the location. - Now the "Enter Map Coordinates" window appears in front again. Click on “OK” in there. Now your first control point is created, and the “Georeferencer” window appears in front.

    5.  Repeat these steps for the 2nd and following control points.

8.  Once you are happy with the control points, click on the green triangle button in the georeferencing window (or choose top menu "File" $\rightarrow$ "Start Georeferencing". Your georeferenced map will now appear on top of the basemap in the main QGIS window as a new layer.

9.  Change the transparancy of the map by right-clicking on the map layer, choose "properties" (which opens the “Layer properties” window), choose "transparancy" in the list on the left. At the top, move the “Global Opacity” bar to around 50%. Press "OK".

10. Now you should be able to see both the map and the basemap underneath, and you can check if the map is properly georeferenced. ’item If you want to make changes, the "georeferencer" window should still be open, so you can remove control points (right-click on the point in the table, and choose remove), or add more points, then repeat the "Start Georeferencing" again, which will create another layer. Then remove the first map layer, since you only need the new one.

Don’t forget to regularly save the project: top menu "Project" $\rightarrow$ "Save".

## Digitising a mine plan

Now that mine plan is imported and georeferenced, the next step is to digitise the mine plan. We first digitise any galleries and roadways, and then any goaf areas. If your mine plan only contains galleries/roadways or only contains goaf, then proceed with just digitising those only. Digitising x-y coordinates for any mine plan features is explained in Sections <a href="#sec:digitising_galleries" data-reference-type="ref" data-reference="sec:digitising_galleries">7.3.1</a> and <a href="#sec:digitising_goaf" data-reference-type="ref" data-reference="sec:digitising_goaf">7.3.2</a>. Section <a href="#sec:digitising_depth" data-reference-type="ref" data-reference="sec:digitising_depth">7.3.3</a> explains how to digitise the depth of a mine plan, either as a constant-depth flat plane, or as a variable-depth dipping or curving plane.

### Digitising galleries and roadways

To create a network of galleries:

1.  Choose "Layer" $\rightarrow$ "Create Layer" $\rightarrow$ "New Shapefile Layer ...". Click on the 3 dots to choose a file name and appropriate path (just typing a file name in the box left of the 3 dots puts the file in the default (and probably wrong) folder). Choose: "Geometry Type" $=$ "LineString", "Coordinate system" = "EPSG:27700 -OSGB36 / British National Grid" (or equivalent if working dealing with an area outside the UK). Leave all other parameters blank or default, and click "OK"

2.  Now a new layer is created, visible in the QGIS "Layers" window, together with the map: click on the layer to highlight it.

3.  Click on the pencil icon ("Toggle Editing") in the 2nd row, and then on the Line-with-Star icon ("Add Line Feature") to the right of it.

4.  Switch on the snapping tool: "Project" $\rightarrow$ "Snapping Options". A thin, wide window appears with all options: first box: snapping $=$ on (grey instead of white); third box: tick Vertex, Segment, Line Endpoints. Close the window.

5.  Now the mouse point should have a ’target’ shape, and you can start creating lines. Click on the start point, then on the end point of the line. Then right-click and click ‘OK’. Repeat this for next lines. Multi-segment lines should work as well.

6.  Note that long lines crossing other lines is fine: the postprocessing method will automatically split these long lines in individual segments.

7.  When finished, click on the pencil icon again, and choose the option to save the changes.

### Digitising goaf areas

To create one or more goaf areas:

1.  Choose "Layer" $\rightarrow$ "Create Layer" $\rightarrow$ "New Shapefile Layer ...". Click on the 3 dots to a choose file name and appropriate path (just typing a file name in the box left of the 3 dots puts the file in the default (and probably wrong) folder). Choose: "Geometry Type" $=$ "Polygon", "Coordinate system" = "EPSG:27700 -OSGB36 / British National Grid" (or equivalent if working dealing with area outside UK). Leave all other parameters blank or default, and click "OK"

2.  Now a new layer is created, visible in the Layer window, together with the map: click on the layer to highlight it.

3.  Click on the pencil icon ("Toggle Editing") in the 2nd row, and then on the Green-polygon-with-Star icon ("Add Polygon Feature") to the right of it.

4.  Make sure that the snapping tool is still on. Note that, for GEMSToolbox to create a viable solution, all galleries and goaf areas need to be connected, so your goaf area should have at least one point in common (i.e. snapped to) a node of the line galleries. Also note that galleries and goaf areas should not overlap. This means that any edge of the gaof zone cannot also be a gallery.

5.  Now the mouse point should again have a ’target’ shape, and you can start creating the outline of the first polygon. Click on the start point, then subsequent points. When you are ’back’ near the start point, don’t click on the start point again, as the polygon feature will automatically close the polygon. Now right-click and click ‘OK’.

6.  Repeat this for any subsequent polygons.

7.  When finished, click on the pencil icon again, and choose the option to save the changes.

### Digitising depth of mine plans

If a mine plan is modelled using a fixed depth for the entire plan, this Section <a href="#sec:digitising_depth" data-reference-type="ref" data-reference="sec:digitising_depth">7.3.3</a> can be skipped, and this depth is dealt with in Section <a href="#sec:QGIS2GEMS" data-reference-type="ref" data-reference="sec:QGIS2GEMS">7.4</a>.

If a mine plan significantly deviates from being flat, then its depth needs to be explicitly digitised. For that, we need several points on the mine plan where depth is known. The geographical spread of these points should cover the extent of the digitised mine plan in Sections <a href="#sec:digitising_galleries" data-reference-type="ref" data-reference="sec:digitising_galleries">7.3.1</a> and <a href="#sec:digitising_goaf" data-reference-type="ref" data-reference="sec:digitising_goaf">7.3.2</a>. The following digitisation method will create a smooth 3-D layer as QGIS shapefile that interpolates between the depth points (but won’t extrapolate beyond the lateral extent of those depth points). The x-y coordinates of the features digitised in Sections <a href="#sec:digitising_galleries" data-reference-type="ref" data-reference="sec:digitising_galleries">7.3.1</a> and <a href="#sec:digitising_goaf" data-reference-type="ref" data-reference="sec:digitising_goaf">7.3.2</a> will be ’draped’ onto this 3-D layer to provide a z-coordinate for every x-y coordinate.

The following QGIS procedure should be used:

1.  Create a QGIS layer with depth points:

    1.  Choose "Layer" $\rightarrow$ "Create Layer" $\rightarrow$ "New Shapefile Layer"

    2.  Choose a file name for the 3-D layer (make sure to choose the correct folder!)

    3.  Choose Geometry type = Point

    4.  "New Field:"

        1.  "Name" = "Elevation" (suggested: any name is fine, in this manual "Elevation" is assumed further down)

        2.  "Type" = "Decimal (double)"

        3.  Click "Add to Fields List"

    5.  Click "ID" in Fields List and then click on "Remove Field" below the list

    6.  Click "OK"

2.  Highlight the new layer in the "Layers" panel

    1.  Click the ’pencil’ icon ("Toggle Editing")

    2.  Click the ’star-and-three-dots’ icon ("Add Point Feature")

    3.  Click at a point where depth is known; When asked for "Elevation", enter a depth value in meters and click "OK"

    4.  Repeat this for all points you want to include for interpolation of the 3D depth layer.

3.  Open the "Processing Toolbox" if not already open ("Processing" $\rightarrow$ "Toolbox")

    1.  Type "IDW interpolation" in the Search box

    2.  Choose "Interpolation $\rightarrow$ "IDW Interpolation". This will open a new window. N.B. this will use IDW $=$ Inverse-Distance-Weighting", which creates a smooth layer. If you prefer linear interpolation, there is another interpolation type called "TIN Interpolation". This option is not discussed here, but works very similar to IDW interpolation.

    3.  Choose "Vector Layer" $=$ your point layer that you’ve just created

    4.  This should now show "Elevation" as attribute. Click the green "+" button

    5.  Scroll down in the window to set "Extent" $=$ "Calculate from Layer", and choose your point layer. Other extent options might be worth trying if you are interested.

    6.  Click "Run" and it should produce a new later with smooth depths between your set points. This file will be stored under the same name with a .tif extention, indicating that is a ’geotiff’ file type. This file name will be needed in the next section. You may want to move this new layer to below your other layers so that it is plotted ’behind’ those other layers.

## Convert line and polygon features into GEMSToolbox shapefiles

Now some processing of those line and goaf features is needed to make them suitable for the GEMSToolbox calculation: multi-segment lines need to be split into individual lines, crossing lines need splitting up, lines and polygon features need to be merged, nodes need a unique numbering, and those nodes need attributes to store additional information (such as which line of polygon each node belongs to). This can all be done automatically using a Python script that can run inside QGIS. Here are the steps to enable this:

1.  Copy the script ${\tt QGIS2GEMSTb.py}$ from the GEMSToolbox folder ${\tt src/external\_functions}$ to the QGIS project folder.

2.  Open the `QGIS2GEMSTb.py` file using any text editor. Scroll to the main code at the end of the file, and modify the following two lines:

               line_file   = "pipes.shp"
               goaf_file   = "goaf.shp"

    by inserting the name you created for the shapefiles for the galleries and goaf features. If you only have digitised roadways, just leave the ${\tt goaf\_file}$ empty:

               goaf_file   = ""

    or provide a non-existent filename: if the script cannot find a file, it will assume no digitised goaf area is present. Similarly, if you only have digitised one or more goaf zones, provide an empty or non-existent ${\tt line\_file}$ :

               line_file   = ""

    By default, the output of the script will be written to a shapefile defined in the line:

               GEMSTb_file = "QGIS_digitised_map.shp"

    This can be modified if needed/desired, e.g. when dealing with multiple worked seams (see below).

    If you want a fixed depth of your mine plan, set the parameter to the right value, e.g. 100 m depth:

               height = -100.

    Note that a negative value of ${\tt height}$ represents the depth of the mine workings. If you have created a variable depth layer in Section <a href="#sec:digitising_depth" data-reference-type="ref" data-reference="sec:digitising_depth">7.3.3</a>, enter that for the variable ${\tt z\_layer\_file}$, e.g.:

               z_layer_file = "slope_raster_IDW.tif"

    As for the other file names, if the file name is empty or the file does not exist, then the script will assume that no variable depth is required, and the value of the parameter ${\tt height}$ will be used instead.

    Save the changes when ready.

3.  In QGIS, Open the Python Console in "Plugins" $\rightarrow$ "Python console". This should open the console below your map.

4.  Inside the console, click the "Show Editor" icon (lined paper-with-pencil icon).

5.  Inside the newly opened editor, click the "Open Script ..." icon (folder icon) to open the ${\tt QGIS2GEMSTb.py}$ script.

6.  Run the script by pressing the "Run" button (green triangle).

7.  If all went well, it should produce some output ending with "STEP 6: Adding GEMSTb attributes COMPLETED". It will have created a set of files starting with `QGIS_digitised_map.*`.

8.  In the GEMSToolbox folder system, go to the folder ${\tt data/maps}$ and create a new folder for the digitised mine plans. Copy all the `QGIS_digitised_map.*` files from the QGIS project folder to this new folder.

The process of creating lines and polygons can be repeated if multiple mine workings are modelled together. Each worked seam then gets its own GEMSToolbox shapefile. But keep in mind that, if you create those different mine workings in the same QGIS folder, the files `QGIS_digitised_map.*` will need different names for the different seams.

# Running GEMSToolbox with the newly created digitised map

## Creating a custom input file

1.  Using the MacOS Finder or Windows Explorer navigate to `<homeGEMSTb>/data` then make a copy of the `Grid_demo.xlsx` or any of the templates provided.

2.  Rename the copy to anything you want, but keep the Excel `.xlsx` extension. For now we will call this `CustomScenario.xlsx`

3.  Open your `CustomScenario` file in a spreadsheet editor. You can now customise any of the parameters as you wish using the information provided in the keyword glossary (Section <a href="#sec:glossary" data-reference-type="ref" data-reference="sec:glossary">10</a>) below. Note that if a parameter is not listed in the input file, the code will use its default value, as listed in Section <a href="#sec:glossary" data-reference-type="ref" data-reference="sec:glossary">10</a>.

4.  On the command line, move to the `<homeGEMSTb>` folder, and run the following command to start the calculation:  
    `python GEMSTb.py data/CustomScenario.xlsx`

5.  If your input file contains multiple models (i.e. multiple columns), you can run the code in parallel:  
    `python GEMSTb.py data/CustomScenario.xlsx –num_workers N`  
    where `N` is the numbers of parallel threads you would like to use.
