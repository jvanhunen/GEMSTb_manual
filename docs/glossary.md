# Input Keyword Glossary

This section describes the properties that can be set in the input file. Any property not set up in the input file will be read from the `config/default_params.yml` file. The format of the parameters in the Excel input file is such that only numbers, strings, space, commas (,), and square brackets (\[ \]) are allowed in the input Excel file. 2D arrays can be inputted as \[1 2\] \[3 4\] or \[\[1,2\], \[3,4\]\]. Formatting using other symbols like \[1 2 ; 3 4\] or 1 2 ; 3 4 is not allowed.

- **a** (0.5): the damping oscillation factor applied to the flow at iteration n-1.

- **ArcGIS_file_name** (no default): the path to the shapefiles to be used to generate the geometry with `step_load_GIS_geometry`. The format is `[<directoryPath>/<fileName1>.shp, <directoryPath>/<fileNameN>.shp]`.

- **b** (0.5): the damping oscillation factor applied to the flow at iteration n.

- **connections** (\[ \]): list of node ID doublets to create connecting pipes (e.g. to connect different seams)

- **Cp_f** (4186 J/K/kg) specific heat capacity of the mine water

- **Cp_r** (960 J/K/kg) specific heat capacity of the rocks

- **d_set** (2.25 m) diameter of the mine galleries

- **eps** (0.1 m): mine gallery roughness parameter

- **fixed_head_node** (\[\[2, 0.0\]\]): node nr where hydraulic head is fixed

- **flow_error_threshold** ($1.0 \times 10^{-15}$): numerical accuracy of the flow solver

- **gis_overrides** ( ): parameters to be overriden using the value found in the GIS files.

- **grid_height** (3): nr of grid points in y-direction (used for structured grids only)

- **grid_width** (3): nr of grid points in x-direction (used for structured grids only)

- **gw_darcy_velocity** (0 m/s): Darcy velocity of the regional groundwater into the mine.

- **h_pipe_length** (50 m): x-length of each gallery segment (used for structured grids only)

- **Hydraulic_conductivity** (0.03 m/s): Hydraulic conductivity of porous zones (goaf and collapsed/backfilled galleries)

- **igeom** (`step load_GIS_geometry`): specifies the geometrical function file to be used by the code. Two options are available: 1) `step load_GIS_geometry` (will read structure from GIS shapefile), and 2) `step_grid_geometry` (will generate uniform grid )

- **int_d** (1000): nr points to evaluate the thermal interference between galleries

- **k_f** (0.58 W/m,K): fluid thermal conductivity

- **k_r** (2.6 W/m,K): rock thermal conductivity

- **mat_d_prop** (\[5.0\] m: array to set different diameter to specific pipes specified with `mat pipe_ids`

- **mat_K_prop** (\[0.03\] m/s: array to set different hydraulic conductivities to specific pipes specified with `mat pipe_ids`

- **mat_pipe_ids** (\[ \]): array to pipe IDs for which non-default diameter or hydraulic conductivity values apply. See also parameters mat_d_prop and mat_K_prop.

- **mat_prop_case** (1): the switch case code used to apply the material properties to the model (currently porosity and hydraulic conductivity). 1: sets porosity to 1 for all pipes (i.e. all pipes are considered open). 2: sets all the pipes to the porosity and hydraulic conductivity specified in the **porosity** and **Hydraulic_conductivity** input keywords respectively. 3: uses a Perlin Noise map to set the porosity values of the pipes, and beyond a certain threshold (specified in **open_th** keyword) all the pipes are considered open with a porosity of 1. The value specified in the **Hydraulic_conductivity** input keyword is used as the hydraulic conductivity in all pipes. 4: like 3, but around a radius specified by the **well_exclusion_th** input keyword, where all pipes are considered open. 5: like 4 but instead of forcing open pipes around the wells, we force porous pipes.

- **max_sim_time** (20 yrs): the maximum time it should take for water to reach the end of any given pipe. Beyond which the outflow temperature of a pipe will be considered to be that of the initial rock temperature.

- **mesh_density** (100 m): The maximum mesh size the model will try to achieve in 2D porous goaf areas.

- **n_steps** (10): the number of steps it takes the water to flow through a pipe.

- **no_seams** (1): number of seams for scenario of regular structured grids (if igeom $==$ step load_GIS_geometry)

- **node_outputs** (Tn T(C), head Head(m), tt_n transit_times(yrs), wells Well_positions, n_tree_idx, Tree_pos, node_id node_id\]): specifies the desired nodal outputs to be saved in the vtk file for each run. List of valid node outputs:

  - node_id: the id of the node found in the underlying GIS files or/and ID to be used to set inflow, outflow, or fixed head nodes.

  - Tn: the nodal temperatures of the model.

  - head: the nodal hydraulic heads of the model.

  - tt_n: the time it takes water to flow from the closest net inflow point to this node.

  - wells: indicates the inflow (1), outflow (-1) and fixed head (0) nodes. All other nodes have a NaN value.

  - n_tree: the position of nodes in the tree used to sequentially solve the heat transfer.

- **nu_f** (1.2e-06 Pa s): dynamic viscosity of the mine water.

- **nyrs** (3 yrs): the number of simulation years is to be run for.

- **open_th** (0.5): threshold value of (random) porosity above which a pipe is considered ’open’. Applies to the cases where mat_prop_case $>$ 1.

- **pipe_outputs** (\[pipe_id pipe_id, vs Water_velocity(m/s), Q_real Flow_rate(m3/s), poro_e Porosity($\mathrm{m^3/m^3}$), Re Re(-), d Pipe_diameters(m), alphas Alpha, rp R_0, dT_model Heat_Model_dT(C)\]): specifies the desired pipe outputs to be saved as cell values in the vtk file for each run. List of valid pipe outputs:

  - pipe_id: the id of the pipes as held within the GEMS toolbox.

  - Re: the Reynolds number.

  - v: the water velocity inside the pipe (m/s) assumed uniform.

  - Qv: the vectorised flow rate through the pipes (m$^3$/s). Saved as a vector in VTK with an x, y and z component.

  - Q: the absolute flow rate through the pipes. Is equal to the magnitude of Qv.

  - poro: the porosity of each pipe.

  - rp: the radial distance of the thermal front inside an infinite homogeneous porous rock.

  - Tp: a vectorised value holding two components labelled x and y. x corresponding to the inflow temperature of the pipe and y to its outflow temperature.

  - pmod: indicates which case of the statement is used in the heat calculation code.

  - Qdiff: the flow difference in the pipe between the last and penultimate iteration in the flow computation.

  - K: hydraulic conductivity.

  - d: pipe diameter.

- **Porosity** (0.3): the porosity of the any backfilled or collapsed pipes.

- **q_in** (\[1\]): array of injection node ID(s).

- **q_out** (\[3\]): array of abstraction node ID(s).

- **qset** (\[0.01\] $\mathrm{m^3/s}$): the flow rate in/out of each injection and abstraction wells

- **Qth_tree** (1.0e-07): the cut-off value for the flow comparison check used when disregarding a node for the computation of the flow tree required for the sequential heat calculations. This might need adjusting if porous pipes sections of the models are not added to the tree.

- **rho_f** (1000 $\mathrm{kg/m^3}$): density of the mine water.

- **rho_r** (2400 $\mathrm{kg/m^3}$): density of the rock mass surrounding the mine.

- **rng_seed** (1): random number generatore seed used for random porosity models (when mat_prop_case $>$ 1)

- **seam_spacing** (100 m): spacing of seams in regular grid models (when igeom $==$ step_grid_geometry)

- **Tag** ( ): allows you to specify a tag that will be added to the output .vtk filename.

- **Tf_ini** (\[3\] $\mathrm{{}^o}C$): array of the same length as for parameter q_in with water injection temperature(s).

- **Tr** (\[-0.032, 8.8\] $\mathrm{{}^o}C/m$, $\mathrm{{}^o}C$): Rock temperature definition: first parameter is the vertical gradient, while the 2nd value is the rock temperature at the surface.

- **v_pipe_length** (50 m): y-length of each gallery segment (used for structured grids only)

- **well_exclusion_th** (30 m): avoid porous zones within well_exclusion_th from the injection or abstraction wells.

# Adding additional parameters

To compute some of your inputs you might want to perform intermediate calculations based on some additional parameters. To do this you can simply add another parameter, give it a name in the first column, with no spaces, and populate ALL the columns where a scenario is already defined. You can then use this parameter with Excel’s inbuilt capabilities to compute your desired parameters. This should enable you to keep track of all the parameters used to obtain your inputs in the same file. Note that, ’loose’ numbers in other parts of the spreadsheet will cause errors.
