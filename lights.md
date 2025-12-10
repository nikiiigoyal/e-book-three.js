# Lights

**AmbientLight** -Sab jagah equal brightness, koi direction nahi.
Memory Trick:
“Jahan shadow ka black-black corner hataana ho → Ambient lagao.”

_new THREE.AmbientLight(color, intensity)_

**DirectionalLight** - SURYA DEV” 
Parallel rays, ek hi direction me pura scene ko hit karti hain.
Memory Trick:
"Jahan sunlight feel chahiye → Directional.”

_const sun = new THREE.DirectionalLight(color, intensity)
sun.position.set(…)_

**HemisphereLight** - Upar sky ka color, neeche earth ka color.”
Yeh do colors ko mix karke soft environment light deta hai.

_new THREE.HemisphereLight(skyColor, groundColor, intensity)_

**This light cannot be used to cast shadows**

**PointLight** -Point light = “LED Bulb” 💡
Ek point se har direction me light jaati hai.
_new THREE.PointLight(color, intensity, distance, decay)_

_distance_
Maximum range of the light. 0 means no limit.
Default is 0.
_decay_	
The amount the light dims along the distance of the light.

Default is 2.
**This light can cast shadows**

**SpotLight** - Ek cone shape me light nikalti hai.

_new THREE.SpotLight(color, intensity, distance, angle, penumbra)_

angle = cone kitna wide
penumbra = edges kitne soft

**This light can cast shadows**

**RectAreaLight** indow light / Tube light / Softbox”
Rectangular area se soft uniform light.
_new THREE.RectAreaLight(color, intensity, width, height)_



**THREE.RectAreaLightNode.setLTC( RectAreaLightTexturesLib.init() )** 
is an initialization step required specifically when using RectAreaLight with the newer WebGPU Renderer.
RectAreaLight simulates _light accurately_, including how light gets softer as it hits different parts of a surface. This calculation is complex.

Efficiency: Instead of doing the complex math in real-time for every single frame (which would be very slow), three.js uses the LTC technique. This technique pre-calculates the heavy-duty math and stores the results in small textures (your "cheat sheet").

The Fix: The line you asked about simply tells the WebGPU renderer: "Before you start drawing anything, please load this special LTC (Linearly Transformed Cosines.	A complex mathematical technique.)data using RectAreaLightTexturesLib.init() and register it using setLTC() so you know how to draw light properly."

Important Notes:

**There is no shadow support.
Only PBR materials are supported**

You have to include RectAreaLightUniformsLib (WebGLRenderer) or RectAreaLightTexturesLib (WebGPURenderer) into your app and init the uniforms/textures.
**RectAreaLightUniformsLib.init();** //only relevant for WebGLRenderer
**THREE.RectAreaLightNode.setLTC( RectAreaLightTexturesLib.init() );** //only relevant for WebGPURenderer



