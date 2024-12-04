Interactive: 
it is hosted on this link (Takes a couple of seconds to load): https://luminous-macaron-3d8647.netlify.app


Explanation of our Project:

The development of a WebGPU-based 3D rendering workflow involves multiple interconnected components and a step-by-step process to ensure the effective rendering of 3D models. The index.html file serves as the entry point, setting up the WebGPU canvas and linking the necessary JavaScript files for rendering. It facilitates user interactions and initiates the rendering process. The gltf-demo.js script manages the higher-level logic, such as loading models, handling user inputs, and orchestrating scene updates, allowing for seamless switching between different models. Meanwhile, the tiny-gltf.js file takes care of the detailed parsing of GLTF/GLB files, extracting key elements like node hierarchies and geometry, and preparing them for GPU rendering. Finally, the tiny-webgpu-demo.js script provides a lightweight framework for rendering WebGPU scenes, handling tasks like resizing, frame updates, and camera positioning.

The workflow for importing and rendering 3D models starts with parsing the GLTF/GLB files. Using the TinyGltfWebGpu class, the structure of the model is extracted, including nodes, meshes, and attributes such as positions, normals, and indices. Parsing these files is crucial for understanding the model’s hierarchy and components before rendering begins. Once parsed, the scene graph is processed to organize objects hierarchically. World-space transformations for each node are computed based on local transformation matrices and parent relationships, ensuring proper positioning and orientation of objects within the scene.

The next step involves creating GPU buffers to hold geometry data like vertex and index information. These buffers are configured based on the attributes defined in the GLTF file, such as positions and normals, ensuring efficient rendering in WebGPU. Following this, materials and bindings are set up. Default materials and buffer bindings are prepared to give objects a basic appearance, even without textures, by defining default colors and lighting parameters. This foundational step enables objects to be rendered with simple materials, leaving room for more advanced shading and texturing enhancements later.

Finally, the models are rendered by drawing the vertex and index buffers using WebGPU commands. This step brings the models into the WebGPU scene, making them visible and ready for interaction. The workflow, summarized in five steps—parsing the GLTF file, processing the scene graph, creating GPU buffers, setting up materials, and rendering the model—ensures a structured and incremental approach to 3D rendering. Each step builds on the previous one, enabling functional rendering while allowing for future enhancements like advanced textures, materials, and shading techniques.

Shaders and materials:





