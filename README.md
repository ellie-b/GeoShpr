# GeoShpr
## Georeferencing with Semi-automated Hierarchical Point cloud Registration

Terrestrial imagery combined with structure-from-motion (SfM) provides a relatively easy-to-implement method for monitoring cryospheric systems, even in remote and rough terrain. The collection of in-situ data and identification of control points required for orientation in SfM processing is the primary roadblock to using SfM in difficult to access locations; it is also the primary bottleneck for using SfM in a time series. Recently, other studies have presented different automated approaches to SfM processing with time lapse imagery, but most approaches still rely on control points for georeferencing. We set out to develop an approach to 4D change detection using time lapse imagery which eliminated the need for surveying and identifying control points.

This software implements a new, semi-automated approach for georeferencing terrestrial point clouds (TPC) using a reference point cloud (e.g. aerial point cloud; RPC). We utilize a Discrete Global Grid System (DGGS; Hall et al., 2020) which allows us to capitalize on easily collected information about camera deployment to coarsely register the TPC, and provides a natural correspondence between the TPC and RPC. The approach requires minimal interaction in a user-friendly interface, while allowing for user inspection of results.

Hall J, Wecker L, Ulmer B, Samavati F. [Disdyakis Triacontahedron DGGS]. ISPRS Int’l J. of Geo-Information. 2020; 9(5):315.

## Features

- Load point clouds in both referenced and unreferenced frames
- Select the viewpoint of the cameras used to create the unrefereneced cloud
- Automatically optimize fit between reference data and unreferenced point cloud
- Inspect results and select the best solution for further refinement
- Apply reults to a time series of point clouds that share the same view

## Tech

The following open source projects are either used directly within the the above source
or were used during its development.

- boost/1.76.0 - https://github.com/boostorg - https://www.boost.org/ - [Boost License](https://www.boost.org/users/license.html)
- eigen/3.3.9 - https://eigen.tuxfamily.org/index.php?title=Main_Page - [MPL2 License](https://eigen.tuxfamily.org/index.php?title=Main_Page#License)
- fmt/7.1.3 - https://github.com/fmtlib/fmt - [LICENSE](https://github.com/fmtlib/fmt/blob/master/LICENSE.rst)
- gdal/3.3.1 - https://gdal.org/ - [MIT/X license](https://gdal.org/license.html)
- glfw/3.3.3 - https://www.glfw.org/ - [zlib/libpng license](https://www.glfw.org/license.html)
- hdf5/1.12.0 - https://portal.hdfgroup.org/display/HDF5/HDF5 - [BSD-3 License](https://portal.hdfgroup.org/display/support/Licenses)
- imgui/1.81 - https://github.com/ocornut/imgui - [MIT License](https://github.com/ocornut/imgui/blob/master/LICENSE.txt)
- immer - https://github.com/arximboldi/immer - [Boost License](https://github.com/arximboldi/immer/blob/master/LICENSE)
- implot - https://github.com/epezent/implot - [MIT License](https://github.com/epezent/implot/blob/master/LICENSE)
- lager - https://github.com/arximboldi/lager.git - [MIT License](https://github.com/arximboldi/lager/blob/master/LICENSE)
- libgeotiff/1.7.0 - https://github.com/OSGeo/libgeotiff - [X-Style](https://github.com/OSGeo/libgeotiff/blob/master/libgeotiff/LICENSE)
- libigl - https://github.com/libigl/libigl - [MPL2 License](https://github.com/libigl/libigl/blob/main/LICENSE.MPL2)
- ms-gsl/3.1.0 - https://github.com/microsoft/GSL - [MIT License](https://github.com/microsoft/GSL/blob/main/LICENSE)
- nlohmann_json/3.9.1 - https://github.com/nlohmann/json - [MIT License](https://github.com/nlohmann/json/blob/develop/LICENSE.MIT)
- openssl/1.1.1k - https://github.com/openssl/openssl - [Apache 2.0 License](https://github.com/openssl/openssl/blob/master/LICENSE.txt)
- pdal/2.3.0 - https://pdal.io/ - [BSD](https://pdal.io/copyright.html)
- portable-file-dialogs - https://github.com/samhocevar/portable-file-dialogs - [WTFPL License](https://github.com/samhocevar/portable-file-dialogs/blob/master/COPYING)
- proj/8.1.1 - https://proj.org/ - [X/MIT License](https://proj.org/about.html#license)
- range-v3 - https://github.com/ericniebler/range-v3 - [Boost License](https://github.com/ericniebler/range-v3/blob/master/LICENSE.txt)
- spdlog/1.8.2 - https://github.com/gabime/spdlog - [MIT License](https://github.com/gabime/spdlog/blob/v1.x/LICENSE)
- tbb/2020.3 - https://github.com/oneapi-src/oneTBB - [Apache 2.0 License](https://github.com/oneapi-src/oneTBB/blob/master/LICENSE.txt)
- tinyply/2.3.2 - https://github.com/ddiakopoulos/tinyply - [Public Domain](https://github.com/ddiakopoulos/tinyply#license)
- vivid - https://github.com/gurki/vivid - [MIT License](https://github.com/gurki/vivid/blob/master/LICENSE.md)
- zstd/1.4.5 - https://github.com/facebook/zstd - [BSD-3 License](https://github.com/facebook/zstd/blob/dev/LICENSE)
- zug - https://github.com/arximboldi/zug - [Boost License](https://github.com/arximboldi/zug/blob/master/LICENSE)

## Installation

To install download the two zip folders into one directory and extract the contents. In the geoshpr-v1 folder, find the sandbox.ini file and open it with a text editor. Change the directory path to point to the geoshpr-data folder you just extracted.

That's it! Now open the geoshpr executable and start georeferencing!

One known issue during installation is an incompatability with some native Windows graphics cards. If the software fails to open, try changing the preferred graphics card under in the control panel.

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

Work was supported by the [Applied Geospatial Research Group], [UW Glaciology], [NSERC], and [UofC Graphics Interaction Visualization(GIV)].

Development of this software is ongoing, please submit feature requests and bug reports to help us improve it!

## License for the software itself
(c) 2018-2021 Lakin Wecker & Faramarz Samavati

Permissive Binary License

Version 1.0, September 2015

Redistribution.  Redistribution and use in binary form, without
modification, are permitted provided that the following conditions are
met:

1) Redistributions must reproduce the above copyright notice and the
   following disclaimer in the documentation and/or other materials
   provided with the distribution.

2) Unless to the extent explicitly permitted by law, no reverse
   engineering, decompilation, or disassembly of this software is
   permitted.

3) Redistribution as part of a software development kit must include the
   accompanying file named "DEPENDENCIES" and any dependencies listed in
   that file.

4) Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission. 

Limited patent license. The copyright holders (and contributors) grant a
worldwide, non-exclusive, no-charge, royalty-free patent license to
make, have made, use, offer to sell, sell, import, and otherwise
transfer this software, where such license applies only to those patent
claims licensable by the copyright holders (and contributors) that are
necessarily infringed by this software. This patent license shall not
apply to any combinations that include this software.  No hardware is
licensed hereunder.

If you institute patent litigation against any entity (including a
cross-claim or counterclaim in a lawsuit) alleging that the software
itself infringes your patent(s), then your rights granted under this
license shall terminate as of the date such litigation is filed.

DISCLAIMER. THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND
CONTRIBUTORS "AS IS." ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT
NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
HOLDERS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED
TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

   [Applied Geospatial Research Group]: <https://www.appliedgrg.ca/>
   [UW Glaciology]: <https://uwglaciology.ca/>
   [NSERC]: <https://www.nserc-crsng.gc.ca/index_eng.asp>
   [UofC Graphics Interaction Visualization(GIV)]: <https://giv.ucalgary.ca/>
   [Disdyakis Triacontahedron]: <https://www.mdpi.com/2220-9964/9/5/315>
