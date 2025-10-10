# Resources

VIDEO: **"https://www.youtube.com/watch?v=KM64t3pA4fs&t=1s*"**
DOc: **https://threejs.org/manual/**


## Notes

**WebGl** : js Api for rendering 3d graphics in web browser using GPU.
**GPU** : special type of hardware that can run simple calculations in parallel.
**3.js?** :- Three.js is a JavaScript library that uses WebGL to render 3D graphics in a web browser.
**Components of 3.js**
*Scene, Camera, and Renderer:*
**Scene**: The container where everything lives (models, lights, cameras).
**Renderer**: The engine that calculates and draws the final image onto the screen using WebGL.
**Camera**: Your viewport into the 3D world (what the user sees).
That's a great next step! Understanding the two main camera types is absolutely key to making your scene look right.
The two main camera types in Three.js are:
PerspectiveCamera 🌎 - (fov,aspectratio,near,far)
OrthographicCamera 📐 - (left,right,top,bottom,near,far)
**The PerspectiveCamera** : It works just like your eye or a real camera: objects look smaller the further away they are. It gives your scene depth and realism.

**FOv** - vertical angle of your viewing cone. (How wide the view is.)	
(Set between 50 and 75). A smaller number "zooms in" (telephoto); a larger number "zooms out" (wide-angle).
**Aspect Ratio** - The shape of your screen. 
Must be calculated as window.innerWidth / window.innerHeight to match your canvas.
**Near** - The closest an object can be before it vanishes.	Set a small number like 0.1. 
**Far** - The farthest an object can be before it vanishes.	Set a large number like 1000. 
**The OrthographicCamera** : is used for technical drawings, 2D games, or UI elements. It treats every object as if it's the same distance away, so a cube far away looks the exact same size as the same cube up close.



**OrbitControls** 
The OrbitControls is a utility that allows the user (you) to interactively move the camera around a central point in the scene using a mouse or touch input. It handles all the complex math for rotation, panning, and zooming so you don't have to write it yourself.

*properties:*
new OrbitControls(camera, canvas) = Initializes the controls.	Links the camera (what's moving) to the canvas (where the input is detected).
controls.enableDamping = true;	Enables a slight friction/momentum.	Makes camera movement feel smoother.
controls.autoRotate = true;	Sets the camera to spin automatically.	Makes the object slowly turn when the user isn't interacting with the scene.
controls.update() = Calculates new positions.	Must be called in the render loop to apply the effects of damping and auto-rotate every frame.

**RenderLoop**
the Render Loop is the continuous function that runs to update your scene 60 times per second
*window.requestAnimationFrame(renderLoop)*	- The function call that powers the loop.	Asks the browser to call renderLoop again before the next screen refresh. This is efficient and keeps the frame rate smooth.
*renderer.render(scene, camera)*

**Resizing**
when a user changes the size or shape of the browser window, the 3D scene doesn't look stretched or squished.
*camera.aspect = W / H;*- Updates the camera's shape
*renderer.setSize(W, H);* -	Updates the drawing area.
*camera.updateProjectionMatrix();*	- Forces the camera to recalculate its view

**Antialiaisng**
**Aliasing**: When a computer draws a diagonal or curved line on a square grid of pixels, it can't perfectly represent the curve. This results in stair-step edges that look rough and unnatural, especially noticeable on objects in 3D environments
**Antialiasing**: Anti-aliasing is the technique used to solve this. Instead of drawing a harsh, jagged edge, it intelligently blends the color of the edge pixels with the background color.

pass in renderer
 <!-- antialias: true // <-- This enables the smoothing! -->

or this way
<!-- const maxPixelRatio = Math.min(window.devicePixelRatio, 2);
renderer.setPixelRatio(maxPixelRatio); -->

**Transormation properties**
**Vector 3**: All transformation properties (position, rotation, scale) use the Vector3 structure, which stores three numbers: 
X (Left/Right), 
Y (Up/Down), and 
Z (Forward/Backward/Depth).

**Position** (0,0,0) (Origin)	
mesh.position.set(x, y, z)	
positive X values go right
positive Y values go up
Positive Z moves the object backward (away from the user).

**Scale** (1,1,1)(Original size) 
mesh.scale.set(x, y, z)	
Values <1 shrink; values >1 enlarge.

**Rotation** (0,0,0)	
mesh.rotation.y =
 value	Uses Radians. π radians = 180
 to turn 180 = Math.Pi
 90 = Math.pi / 2
 360 = Math.pi * 2

**Scene Hierarchy**
A folder or container.

*THREE.Group.*
A Group is an invisible container that holds multiple meshes. If you transform (position, rotate, or scale) the Group, all the meshes inside it move together. This is essential for building complex objects (like a car made of separate wheels and a body).

**Geometry**
**Buffer Geometry & Primitives**
The raw clay (Buffer Geometry) and the pre-made shapes (Primitives).

**BufferGeometr**y is the underlying, high-performance way to store a mesh's shape (its vertices, faces, and normals). 
**Primitives** (like BoxGeometry, SphereGeometry, CylinderGeometry) are simply pre-packaged, ready-to-use forms of BufferGeometry.

***If Geometry is the object's shape, the Material is its surface properties, and the Texture is the image painted on it.***

**Materials**
Defines how the surface reacts to light (is it shiny, matte, rough, or does it ignore light?).

**Types of Materials**

**MeshBasicMaterial**
Ignores all light. 
It always renders in its set color, regardless of the scene's lighting. 
Best for simple 2D or debugging.

**MeshLambertMaterial**
Reacts to light but does not have shiny reflections (specular highlights). Good for soft, non-reflective surfaces.

**MeshPhongMaterial**	
Reacts to light and supports specular highlights (the sharp, bright spot of reflected light). Looks glossy.

**MeshStandardMaterial**	
Uses Physically Based Rendering (PBR). 
Requires roughness (how matte or shiny it is) and metalness (how metallic it is) maps. 
Highly realistic shading.

**MeshPhysicalMaterial**	
 Paint An advanced extension of StandardMaterial. Used for complex surfaces like clear coats, glass, transparency, and advanced refractions.