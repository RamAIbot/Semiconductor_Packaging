# Semiconductor_Packaging
<h1> Day 3 - Semiconductor packaging workshop from VSD </h1>
<h2> Designing a Flip Chip BGA package </h2>


<h3> Creating the package </h3>

<p> The IcePak simulator to design and test the package. We start by creating a package from Tool options Icepak -> Tookit -> Geometry -> Packages -> Flip Chip  BGA. The package size is 15mm x 15mm x 1.6mm.</p>

<img src="./package_dim.png" alt="package dim"/>

<p>Next, the die dimentsion is selected. In thi case, we have a die size which is half the size of package. 8.56mm x 8.56mm. The die thickness is negligible. The die is supposed to consume 1W power and generate heat based on the consumption. A suitable underfill material is added between the die and the BGA array of the die which is of 0.01mm in thickness.</p>

<img src="./die_dim.png" alt="die dim"/>

<p>We then select the substrate on which the die needs to be placed. The substarate is designed to have 2 intermediate routing layers and the thickness is chosen to be 0.36mm. The traces are made in pure Copper. At this point we don't have any heat dissipating via.</p>

<img src="substrate_dim.png", alt="substrate_dim"/>

<p>Finally, we design the Solder for the package. Here 14 solder balls in both X and Y dimensions are chosen. The material is Pb50_sn50. </p>

<img src="solder_dim.png" alt="solder dim"/>

<p>The created package looks as like below.</p>

<img src="package.png" alt="package"/>

<h3>Adding boundary condition to Substrate and die.</h3>

<p>The boundary conditions are added to the die using the option from the project Manager Thermal -> Flipchip_BGA1_die_source. We also add boundary conditions to the substrate by Right click on the Model's Flipchip_BGA1_substrate -> Assign Thermal -> Source -> Set Fixed temperature -> AmbientTemp. (Note : delete the pre-assigned Flipchip_BGA1_trace1 from Project to avoid Overlap warnings).</p>

<img src="boundary_cond1.png" alt="bound_cond2"/>

<img src="boundary_cond.png" alt="bound_cond1"/>

<h3> Adding Monitors </h3>

<p>Setup monitor to the substrate by right clicking on the Model's Flipchip_BGA1_substrate -> Assign Monitor -> Point -> Temperature. Setup monitor to the die by right clicking on the Model's Flipchip_BGA1_die -> Assign Monitor -> Point -> Temperature. Setup monitor to the undefill by right clicking on the Model's Flipchip_BGA1_die_underfill -> Assign Monitor -> Point -> Temperature. </p>

<img src="monitor.png" alt="monitor"/>

<h3>Adding Mesh </h3>

<p>Click on Mesh from the Project Manager -> Simulation -> Generate Mesh. It create a Mesh the package.</p>

<img src="mesh.png" alt="mesh"/>

<h3>Performing Analysis</h3>

<p> Finally, we ise a Solver from Analysis section of the projectmanager -> Add Solution setup -> Set problem types as Temperature and Flow (Keep everything defaults). To check everything's fine, click on validate in toolbar.</p>

<img src="solver.png" alt="solver"/>

<p>Note: If there is any Warning regarding Object does not mesh. Right click the Object from Model -> Assign Mesh Region. If there is an error stating "Failed to launch mesher", delete MeshRegion1 from the Project Manager. Rerun Generate Mesh followed by Analyze All.</p>

<h3>Plotting the temperature graph.</h3>

<p>Select the whole package (by dragging) and right click -> Plot fields -> temperature -> Check Specify Name and Specify folder -> Check Plot on Surface Only -> Goto Surface Smoothing and Enable Gaussing Smoothing.</p>

<img src="thermal_map1.png" alt="thermal_map1"/>

<img src="thermal_map2.png" alt="thermal_map2"/>