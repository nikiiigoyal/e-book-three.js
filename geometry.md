# Geometry
## Buffer Geometry & Primitives**
The raw clay (Buffer Geometry) and the pre-made shapes (Primitives).

**BufferGeometr** is the underlying, high-performance way to store a mesh's shape (its vertices, faces, and normals). 
**Primitives** (like BoxGeometry, SphereGeometry, CylinderGeometry) are simply pre-packaged, ready-to-use forms of BufferGeometry.

***If Geometry is the object's shape, the Material is its surface properties, and the Texture is the image painted on it.***

### primitves

**SphereGeometry** -
_new SphereGeometry( radius : number, widthSegments : number, heightSegments : number, phiStart : number, phiLength : number, thetaStart : number, thetaLength : number )_

widthSegments	
The number of horizontal segments

heightSegments	
The number of vertical segments.

phiStart	
The horizontal starting angle in radians.
Default is 0.

phiLength	
The horizontal sweep angle size.
Default is Math.PI*2.

thetaStart	
The vertical starting angle in radians.
Default is 0.

thetaLength	
The vertical sweep angle size.

Default is Math.PI.
https://threejs.org/docs/scenes/geometry-browser.html#SphereGeometry


**BoxGeometry**
_new BoxGeometry( width : number, height : number, depth : number, widthSegments : number, heightSegments : number, depthSegments : number )_

const geometry = new THREE.BoxGeometry( 1, 1, 1 );
https://threejs.org/docs/scenes/geometry-browser.html#BoxGeometry


**TorusGeometry**
_new TorusGeometry( radius : number, tube : number, radialSegments : number, tubularSegments : number, arc : number )
_
https://threejs.org/docs/scenes/geometry-browser.html#TorusGeometry


**PlaneGeometry**
_new PlaneGeometry( width : number, height : number, widthSegments : number, heightSegments : number )
_
https://threejs.org/docs/scenes/geometry-browser.html#PlaneGeometry
