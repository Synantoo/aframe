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

edit the last line of ../synantoo-frontend/public/dist/aframe-master-6ce36f8.min.js to point to aframe-master-6ce36f8.min.js.map
