Interactive: 
it is hosted on this link (Takes a couple of seconds to load): https://luminous-macaron-3d8647.netlify.app


Explanation of our Project:

The development of a WebGPU-based 3D rendering workflow involves multiple interconnected components and a step-by-step process to ensure the effective rendering of 3D models. The index.html file serves as the entry point, setting up the WebGPU canvas and linking the necessary JavaScript files for rendering. It facilitates user interactions and initiates the rendering process. The gltf-demo.js script manages the higher-level logic, such as loading models, handling user inputs, and orchestrating scene updates, allowing for seamless switching between different models. Meanwhile, the tiny-gltf.js file takes care of the detailed parsing of GLTF/GLB files, extracting key elements like node hierarchies and geometry, and preparing them for GPU rendering. Finally, the tiny-webgpu-demo.js script provides a lightweight framework for rendering WebGPU scenes, handling tasks like resizing, frame updates, and camera positioning.

The workflow for importing and rendering 3D models starts with parsing the GLTF/GLB files. Using the TinyGltfWebGpu class, the structure of the model is extracted, including nodes, meshes, and attributes such as positions, normals, and indices. Parsing these files is crucial for understanding the model’s hierarchy and components before rendering begins. Once parsed, the scene graph is processed to organize objects hierarchically. World-space transformations for each node are computed based on local transformation matrices and parent relationships, ensuring proper positioning and orientation of objects within the scene.

The next step involves creating GPU buffers to hold geometry data like vertex and index information. These buffers are configured based on the attributes defined in the GLTF file, such as positions and normals, ensuring efficient rendering in WebGPU. Following this, materials and bindings are set up. Default materials and buffer bindings are prepared to give objects a basic appearance, even without textures, by defining default colors and lighting parameters. This foundational step enables objects to be rendered with simple materials, leaving room for more advanced shading and texturing enhancements later.

Finally, the models are rendered by drawing the vertex and index buffers using WebGPU commands. This step brings the models into the WebGPU scene, making them visible and ready for interaction. The workflow, summarized in five steps—parsing the GLTF file, processing the scene graph, creating GPU buffers, setting up materials, and rendering the model—ensures a structured and incremental approach to 3D rendering. Each step builds on the previous one, enabling functional rendering while allowing for future enhancements like advanced textures, materials, and shading techniques.

Shaders and materials:

The process of handling textures in WebGPU involves a series of structured steps to ensure efficient rendering and high-quality visuals. Initially, resolving texture URIs is crucial, as textures can either be embedded within the file or stored externally. To handle this, logic was implemented to resolve these URIs correctly, particularly for external files where relative paths must be handled. This ensures that the correct texture files are fetched, setting the stage for further processing.

Once the URIs are resolved, the next step is to load the texture data. Using the fetch API, the texture files are loaded into memory and converted into ImageBitmap objects, which are compatible with WebGPU. This conversion is a critical step, as raw data must be prepared in a format suitable for GPU usage. After loading, the texture data is prepared for rendering by creating GPU-compatible textures using WebGPU APIs. These textures are configured with properties like size, format, and usage to optimize them for rendering and are uploaded to the GPU for efficient processing.

For further optimization, mipmaps can be generated. Mipmaps are precomputed textures that improve quality at varying levels of detail, particularly for objects viewed from different distances. This step enhances rendering performance while reducing visual artifacts like aliasing. Once the textures are optimized, they are attached to their respective materials. This involves associating textures, such as base color or normal maps, with shaders through BindGroups. These bindings ensure that the shaders can access the textures during rendering.

The final step in the workflow is utilizing textures in the shaders. In the fragment shader, textures are sampled and applied to the model surfaces. This process brings the textures to life by mapping them onto the 3D models, creating detailed and realistic visuals. Each step, from parsing GLTF texture references to applying them in shaders, contributes to a structured approach that enhances the rendering pipeline and ensures visual fidelity.

Lighting was another critical component of the project, as it significantly impacts the realism of the scene. An initial attempt to simulate candlelight using a custom CandleRenderer class involved creating dynamic point lights that mimicked the flicker and glow of real flames. However, the implementation faced challenges, such as balancing light attenuation, dynamic flicker behavior, and integration with the broader lighting setup. The fragment shader logic also struggled with achieving consistency in ambient lighting, leading to unsatisfactory results.

As a result, alternative lighting strategies, including directional and ambient lighting, were explored to maintain realism. While the custom candlelight renderer didn’t achieve the desired effect, it offered valuable insights into the complexities of light simulation and shader-based rendering. Advanced lighting techniques, such as physically-based rendering, were also utilized to create realistic lighting effects. Properties like metallic and roughness were used to control reflectivity and surface detail, while Fresnel-Schlick approximations and GGX normal distribution added depth and accuracy to the highlights and reflections. These combined techniques resulted in dynamic and lifelike lighting effects, further enhancing the overall realism of the rendered scenes.

Skybox, interactive and post process volumes:

The loadCubeMap function loads six images to create a cube texture, handling image fetching, processing, and GPU integration. These textures represent the six faces of the skybox, ensuring realistic environmental reflections.

The createSkyboxPipeline function sets up the rendering pipeline. The vertex shader positions the cube’s vertices, while the fragment shader samples the cube map textures based on direction vectors, creating an immersive 3D environment.

The Sky function ties merges together. It initializes the pipeline, loads the cube map, and sets up a sampler for smooth transitions. A bind group links the textures and sampler to the pipeline for efficient rendering. The renderSkyboxFrame function completes the process by drawing the six faces of the cube in one call.


In our project, we wanted to create a dynamic and interactive experience by allowing users to load different 3D models into the scene using keyboard inputs. To achieve this, we set up a mapping between specific keys and model file paths. This mapping is stored in a JavaScript object called Model, where each key corresponds to a unique model. For example, pressing ‘1’ loads a barrel model, ‘2’ loads a hammer, and so on. We even included a fully assembled shed model, which can be loaded by pressing the ‘H’ key.

To handle the interaction, we added a keydown event listener to the document. This listener detects when a key is pressed and checks if it matches one of the keys defined in the Model object. If a match is found, the corresponding model is loaded into the scene.

Here’s how it works behind the scenes: when a valid key is pressed, the program retrieves the file path of the associated model and calls a function to load it into the scene. To ensure the process runs smoothly, we used asynchronous loading to handle large models efficiently.

We also included logging to provide feedback. If a model loads successfully, a message is displayed in the console, confirming the keypress and model load. If there’s an error, it logs the issue, which helps us debug and improve the user experience.








