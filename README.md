# GeoShpr
## Georeferencing with Semi-automated Hierarchical Point cloud Registration

Terrestrial imagery combined with structure-from-motion (SfM) provides a relatively easy-to-implement method for monitoring cryospheric systems, even in remote and rough terrain. The collection of in-situ data and identification of control points required for orientation in SfM processing is the primary roadblock to using SfM in difficult to access locations; it is also the primary bottleneck for using SfM in a time series. Recently, other studies have presented different automated approaches to SfM processing with time lapse imagery, but most approaches still rely on control points for georeferencing. We set out to develop an approach to 4D change detection using time lapse imagery which eliminated the need for surveying and identifying control points.

This software implements a new, semi-automated approach for georeferencing terrestrial point clouds (TPC) using a reference point cloud (e.g. aerial point cloud; RPC). We utilize a Discrete Global Grid System (DGGS; Hall et al., 2020) which allows us to capitalize on easily collected information about camera deployment to coarsely register the TPC, and provides a natural correspondence between the TPC and RPC. The approach requires minimal interaction in a user-friendly interface, while allowing for user inspection of results.

Hall J, Wecker L, Ulmer B, Samavati F. Disdyakis. Triacontahedron DGGS. ISPRS Int’l J. of Geo-Information. 2020; 9(5):315.

## Features

- Load point clouds in both referenced and unreferenced frames
- Select the viewpoint of the cameras used to create the unrefereneced cloud
- Automatically optimize fit between reference data and unreferenced point cloud
- Inspect results and select the best solution for further refinement
- Apply reults to a time series of point clouds that share the same view

## Tech

GeoShpr relies a number of open source projects to work properly:

- 
- 
- 
- 

## Installation

Installation instructions

## Workflow

1. Load
Select the reference data and input camera locations in the reference coordinate frame. Then select the unreferenced point cloud an dinptu the camera loations in the relative frame of the point cloud. Data scenarios can be saved and reloaded in JSON format.

2. Orient
Select the midpoint of the unreferenced data and adjust the uncertainty of your selection. This highlights the cells searched for best fit in step 4.

3. Scale - currently the scaling is not optimized in the software

4. Optimize
Automatically optimize the best fit between the reference data and the unreferenced data. Solutions are sorted based on the fit and the user can then inspect each solution to choose the best one.

5. ICP - an internal fine-registration step is not implemented yet

6. Apply
Apply the selected solution to any set of selected point cloud files.

## Development

GeoShpr was designed and conceptualized by Eleanor Bash (Postdoctoral Fellow, University of Waterloo), Lakin Wecker (PhD Candidate, University of Calgary), and Mustafizur Rahman (Research Associate, University of Calgary).

Work was supported by the [Applied Geospatial Research Group] and [UW Glaciology].

Development of this software is ongoing, please submit feature requests and bug reports to help us improve it!

## License

??

   [Applied Geospatial Research Group]: <https://www.appliedgrg.ca/>
   [UW Glaciology]: <https://uwglaciology.ca/>
