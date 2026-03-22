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
