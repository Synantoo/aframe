Get latest meshopt decoder from
https://github.com/zeux/meshoptimizer/blob/master/js/meshopt_decoder.js and put
the file in src/

version 0.16
https://github.com/zeux/meshoptimizer/blob/3f2feb6acd17e35383bbc4256d2c8baa7f061165/js/meshopt_decoder.js
at the time of the last build

How to build:

    npm run dist
    cp dist/aframe-master.js ../synantoo-frontend/public/dist/aframe-master-6ce36f8.min.js
    cp dist/aframe-master.js.map ../synantoo-frontend/public/dist/aframe-master-6ce36f8.min.js.map
    sed -i 's@aframe-master.min.js.map@aframe-master-6ce36f8.min.js.map@' ../synantoo-frontend/public/dist/aframe-master-6ce36f8.min.js


model-viewer build:

    git clone --depth=1 git@github.com:google/model-viewer.git  # e6e615616de250dbf19a9c7d3a33b9cc6d951f1f 2021-06-22 15:45 at the time of building it
    cd model-viewer

Get latest https://github.com/zeux/meshoptimizer/blob/master/js/meshopt_decoder.module.js
and https://github.com/zeux/meshoptimizer/blob/master/js/meshopt_decoder.module.d.ts
and put it in packages/model-viewer/src/

Edit packages/model-viewer/src/three-components/CachingGLTFLoader.ts add the
import:

    import {MeshoptDecoder} from '../meshopt_decoder.module';  // without .js

and in constructor below setDRACOLoader, add:

    this[$loader].setMeshoptDecoder(MeshoptDecoder);

This change will not be needed in a more recent version of model-viewer.
There is some custom changes for AvatarSDK, see this commit in the meshopt
branch: https://github.com/Synantoo/model-viewer/commit/d65347405ba1a154499c8d405bb2f06d0afa1f76

build it:

    cd packages/model-viewer
    npm run build
    cp ./dist/model-viewer.min.js ~/workspace/synantoo-frontend/public/dist/model-viewer-1.7.2.min.js
