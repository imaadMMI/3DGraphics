### Submission Files: 
1. Project Folder :[https://heriotwatt-my.sharepoint.com/:v:/g/personal/aa2149_hw_ac_uk/EV1hLoP0NvNCrwqYmcf9G1MB0dXzIfBd__Dm_NmNFXe-3g?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=mjvx0u]
2. Project Code : [https://heriotwatt-my.sharepoint.com/:f:/g/personal/aa2149_hw_ac_uk/EsFJ3hd1ayZIn8GZoxMH7P8Ba0hJGsb3pFTaorzr8GmR3A?e=4iGXmW]
3. Screen Cast Video of Interaction Demo : [https://heriotwatt-my.sharepoint.com/:v:/g/personal/aa2149_hw_ac_uk/EV1hLoP0NvNCrwqYmcf9G1MB0dXzIfBd__Dm_NmNFXe-3g?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=H7ySwW]
4. Group Video presentation: [https://heriotwatt-my.sharepoint.com/:v:/g/personal/aa2149_hw_ac_uk/EV1hLoP0NvNCrwqYmcf9G1MB0dXzIfBd__Dm_NmNFXe-3g?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=LEOfiw]
### Interactive: 
it is hosted on this link (Takes a couple of seconds to load): https://roaring-sprinkles-66487c.netlify.app/



### Explanation of our Project:

The development of a WebGPU-based 3D rendering workflow involves multiple interconnected components and a step-by-step process to ensure the effective rendering of 3D models. The index.html file serves as the entry point, setting up the WebGPU canvas and linking the necessary JavaScript files for rendering. It facilitates user interactions and initiates the rendering process. The gltf-demo.js script manages the higher-level logic, such as loading models, handling user inputs, and orchestrating scene updates, allowing for seamless switching between different models. Meanwhile, the tiny-gltf.js file takes care of the detailed parsing of GLTF/GLB files, extracting key elements like node hierarchies and geometry, and preparing them for GPU rendering. Finally, the tiny-webgpu-demo.js script provides a lightweight framework for rendering WebGPU scenes, handling tasks like resizing, frame updates, and camera positioning.

The workflow for importing and rendering 3D models starts with parsing the GLTF/GLB files. Using the TinyGltfWebGpu class, the structure of the model is extracted, including nodes, meshes, and attributes such as positions, normals, and indices. Parsing these files is crucial for understanding the model’s hierarchy and components before rendering begins. Once parsed, the scene graph is processed to organize objects hierarchically. World-space transformations for each node are computed based on local transformation matrices and parent relationships, ensuring proper positioning and orientation of objects within the scene.

The next step involves creating GPU buffers to hold geometry data like vertex and index information. These buffers are configured based on the attributes defined in the GLTF file, such as positions and normals, ensuring efficient rendering in WebGPU. Following this, materials and bindings are set up. Default materials and buffer bindings are prepared to give objects a basic appearance, even without textures, by defining default colors and lighting parameters. This foundational step enables objects to be rendered with simple materials, leaving room for more advanced shading and texturing enhancements later.

Finally, the models are rendered by drawing the vertex and index buffers using WebGPU commands. This step brings the models into the WebGPU scene, making them visible and ready for interaction. The workflow, summarized in five steps—parsing the GLTF file, processing the scene graph, creating GPU buffers, setting up materials, and rendering the model—ensures a structured and incremental approach to 3D rendering. Each step builds on the previous one, enabling functional rendering while allowing for future enhancements like advanced textures, materials, and shading techniques.

Shaders and materials:

The process of handling textures in WebGPU involves a series of structured steps to ensure efficient rendering and high-quality visuals. Initially, resolving texture URIs is crucial, as textures can either be embedded within the file or stored externally. To handle this, logic was implemented to resolve these URIs correctly, particularly for external files where relative paths must be handled. This ensures that the correct texture files are fetched, setting the stage for further processing.

Once the URIs are resolved, the nex# **Interactive**
It is hosted on this link (Takes a couple of seconds to load):  
**[https://roaring-sprinkles-66487c.netlify.app/](https://roaring-sprinkles-66487c.netlify.app/)**

---

## **Explanation of Our Project**

The development of a **WebGPU-based 3D rendering workflow** involves multiple interconnected components and a step-by-step process to ensure the effective rendering of 3D models:

- **`index.html`**: Serves as the entry point, setting up the WebGPU canvas and linking the necessary JavaScript files for rendering. It facilitates user interactions and initiates the rendering process.
- **`gltf-demo.js`**: Manages higher-level logic like loading models, handling user inputs, and orchestrating scene updates, enabling seamless model switching.
- **`tiny-gltf.js`**: Handles the detailed parsing of GLTF/GLB files, extracting key elements like node hierarchies and geometry, preparing them for GPU rendering.
- **`tiny-webgpu-demo.js`**: Provides a lightweight framework for WebGPU scene rendering, managing resizing, frame updates, and camera positioning.

### **Rendering Workflow**

1. **Parsing the GLTF/GLB File**:  
   Extracts the structure of the model, including nodes, meshes, and attributes like positions and normals.
2. **Processing the Scene Graph**:  
   Organizes objects hierarchically, computing world-space transformations based on local matrices and parent relationships.
3. **Creating GPU Buffers**:  
   Configures buffers to hold geometry data like vertex and index information, ensuring efficient WebGPU rendering.
4. **Setting Up Materials and Bindings**:  
   Prepares default materials and bindings for objects, defining colors and lighting parameters.
5. **Rendering the Model**:  
   Draws vertex and index buffers using WebGPU commands to bring models into the scene.

---

## **Shaders and Materials**

The texture workflow in **WebGPU** involves the following steps:

1. **Resolving Texture URIs**:  
   Handles embedded or external file paths, ensuring proper fetching and relative path resolution.
2. **Loading Texture Data**:  
   Uses the `fetch` API to load textures into `ImageBitmap` objects, preparing them for GPU use.
3. **Creating GPU-Compatible Textures**:  
   Configures textures with optimized properties like size, format, and usage.
4. **Mipmapping**:  
   Generates precomputed textures for enhanced rendering at varying levels of detail.
5. **Shader Integration**:  
   Textures are bound to shaders, sampled in fragment shaders, and applied to model surfaces for realistic visuals.

---

## **Lighting**

Lighting is pivotal for realism.

- **Candlelight Simulation**:  
   A custom `CandleRenderer` class created dynamic point lights mimicking flicker and glow. Challenges included balancing light attenuation and integrating with ambient lighting, which led to unsatisfactory results.
- **Alternative Strategies**:  
   Directional and ambient lighting were adopted, complemented by **Physically-Based Rendering (PBR)** techniques like metallic and roughness properties, Fresnel-Schlick approximations, and GGX normal distribution for realistic highlights and reflections.

---

## **Skybox, Interactivity, and Post-Processing**

1. **Skybox**:
   - **`loadCubeMap`** loads six images to form a cube texture for environmental reflections.
   - **`createSkyboxPipeline`** defines the rendering pipeline, positioning cube vertices and sampling cube textures for an immersive environment.
   - **`Sky`** integrates these, setting up a pipeline, sampler, and bind group, culminating in efficient rendering via **`renderSkyboxFrame`**.

2. **Interactivity**:
   - A **JavaScript object (`Model`)** maps keys to 3D model paths, enabling users to load models dynamically by pressing keys (e.g., '1' for a barrel, 'H' for a shed).
   - A `keydown` event listener detects inputs, asynchronously loads corresponding models, and provides logging feedback for successful or failed actions.

3. **Post-Processing**:
   - Uses shaders to apply effects like tone mapping for enhanced visual quality.

---
## Hosting 

### **Firebase**
- Firebase hosting offers a generous free limit of 5GB.
- Initial attempts to use Firebase failed due to persistent build issues during deployment.
- While powerful, it required additional setup beyond the scope of our project timeline.

### **Vercel**
- We configured a Vercel x GitHub workflow for seamless deployment.
- However, Vercel imposes a file size limit of 100MB, which made it unsuitable for hosting our larger models and assets.

### **Netlify**
- Finally, we opted for **Netlify**, which successfully hosted our application.
- Deployment was simple, with a drag-and-drop feature or direct GitHub integration.
- Our project is live and accessible at:
  **[https://roaring-sprinkles-66487c.netlify.app/](https://roaring-sprinkles-66487c.netlify.app/)**

Each of these platforms has unique strengths, but Netlify's flexibility and ease of use made it the ideal choice for this project.







