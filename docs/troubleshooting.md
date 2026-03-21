# Troubleshooting

## ArcGIS common problems

## GEMSToolbox common problems and errors

- **Gmsh configuration:** GEMSToolbox makes use of a meshing software Gmsh by calling Gmsh Python API. However, incorrect Gmsh configurations can occasionally result in errors. To ensure proper functionality, install Gmsh using the pip package manager command “**`pip install gmsh`**” rather than the Conda command `conda install gmsh`. If the problem persists, you can download the standalone Gmsh executable directly from the official website: <https://gmsh.info/#Download>. Then run “`python GEMSTb.py <model>.xlsx <gmsh-path>`”, where refers to the path of the Gmsh executable. For example on Windows: **`python GEMSTb.py .\data\testmineplan.xlsx D:\gmsh-4.13.1-Windows64\gmsh`**. GEMSToolbox will call the external Gmsh excutable.

- GEMSToolbox versions from May 2025 or older were using an input file with a different format (using a horizontal rather than vertical layout). If you have ’old’ input files that you would like to run with the latest version of GEMSToolbox, you can convert the input file to the new format using the Python script `convert_input_xlsx.py`. To run the script:  
  `python convert_input_xlsx.py <old_scenario_file>`  
  This will create a new input file in the folder where this script is run with `_transposed` in its file name. If needed, you can then rename this new parameter file and/or move it to the desired folder.

## Paraview common problems

- **Line width of cell attributes:** On MacOS systems, lines don’t render correctly if the Line Width is larger than $1.0$. The problem is discussed in [this forum post](https://discourse.paraview.org/t/cell-values-partly-disappear-when-editing-width-on-mac/11666). A partial work-around is to convert the lines (i.e. cell data) into interpolated points (i.e. point data). To do this, click on the data set in the Pipeline Browser’ which contains the line data. Then choose the ’Filters’ tab, then ’Alphabetically’, and then ’Cell Data to Point Data’. Choose your line data to plot, and you should be able to use larger Line Widths now. The difference is that the original line data has uniform line values, whereas the derived ’Cell Data to Point Data’ dataset interpolates between the points on either end of the line. So for rapidly changing values, it might not be what you want.
