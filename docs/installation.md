# Installing and running the GEMSToolbox software

The GEMSToolbox is designed to import a custom digitised map and test the feasibility of this mine system for mine water geothermal energy purposes. This is all described further down in this manual. This section describes how to install the GEMSToolbox software and test that it runs normally on your computer.

## Installation of GEMSToolbox

1.  Downloading GEMSToolbox You should have received a `.zip` file of the code. Please contact jeroen.van-hunen@durham.ac.uk if this is not the case. Unzip the GEMSToolbox zip file into a suitable folder on your computer. We’ll call this folder `<homeGEMSTb>` from now on.

2.  Install GEMSToolbox Python environment

    - By conda:

      - Navigate to the GEMS directory. Then run:

        - `conda env create -f config/GEMS.base.yml`

      - Activate GEMS enviroment:

        - `conda activate GEMS`

    - By python venv:

      - In terminal or Windows CMD, to create GEMS venv, run:

        - `python -m venv GEMS `

      - Activate GEMS venv:

        - On Windows: `GEMS`$\backslash$`Scripts`$\backslash$`activate`

        - On MacOS and Linux: `source GEMS/bin/activate`

      - Install required packages:

        - Check if `pip` is installed on your machine:  
          `pip –version` should return info on pip. If not, install it using  
          `python get-pip.py`

        - `pip install –upgrade pip`

        - `pip install pytest pandas geopandas meshio scipy openpyxl tqdm numba pyyaml gmsh `

## Running a test model

To check if the code is installed and running properly, you can run one of the pre-installed models:

1.  Navigate to `<homeGEMSTb>`, which is the root directory of GEMSToolbox codebase.

2.  On the command line, run the following line: `python GEMSTb.py <model>.xlsx`  
    where `<model>.xlsx` is one of the model xlsx input files located in the `<homeGEMSTb>/data` folder. For example, if the input file is `testmineplan.xlsx`, located in the `data` folder, then run the following command:  
    `python GEMSTb.py data/testmineplan.xlsx` (MacOS or Linux) or  
    `python GEMSTb.py data\testmineplan.xlsx` (Windows)

3.  If the code is correctly installed, this model should run in less than a minute, ending with the message: `GEMSToolbox completed successfully in X minutes.`

4.  To view the results of this calculation, please refer to Section <a href="#sec:view outputs" data-reference-type="ref" data-reference="sec:view outputs">9</a>.
