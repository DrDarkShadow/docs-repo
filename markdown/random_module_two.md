## FunctionDef count_vowels(text)
**create_config**: The function of create_config is to create a `MindFormerConfig` object from either a YAML file path or a dictionary.
**Parameters**: The parameters of this function.
· config (Union[str, dict]): A string representing the path to a YAML configuration file, or a dictionary containing configuration key-value pairs.
**Code Description**: This function serves as a flexible utility for instantiating a `MindFormerConfig` object. It inspects the type of the `config` input argument. If the argument is a string (`str`), the function treats it as a file path. It first verifies if the file at the given path exists using `os.path.exists()`. If the file is not found, it raises a `FileNotFoundError`. If the file exists, it creates a `MindFormerConfig` object by passing the file path to the class constructor. If the `config` argument is a dictionary (`dict`), the function utilizes the `MindFormerConfig.from_dict()` class method to construct the configuration object from the provided dictionary. Finally, the newly created `MindFormerConfig` object is returned.
**Note**: When providing a string as the `config` argument, ensure that the path is correct and the file exists on the filesystem. The function will raise a `FileNotFoundError` if the file cannot be found, halting execution.
**Returns**: An instance of the `MindFormerConfig` class, populated with the configuration data from the input file or dictionary.
## FunctionDef pairwise_sum(numbers)
**val_pipeline**: **Defines the sequence of data processing and transformation steps for the validation dataset.**

**Pipeline Stages**: The `val_pipeline` is a list of dictionaries, where each dictionary represents a specific transformation stage applied to the video data.
· `dict(type="DecodeVideo")`: A transformation that decodes video files into a sequence of image frames.
· `dict(type="Resize", scale=(-1, 256))`: A transformation that resizes the video frames. The `scale` parameter `(-1, 256)` indicates that the frame's height will be resized to 256 pixels, while the width will be scaled proportionally to maintain the original aspect ratio.
· `dict(type="CenterCrop", crop_size=256)`: A transformation that crops a square patch from the center of each video frame. The `crop_size` of 256 means it will extract a 256x256 pixel region.
· `dict(type="FormatShape", input_format="NCTHW")`: A transformation that rearranges the dimensions of the video data tensor. The `input_format="NCTHW"` specifies the final tensor shape to be (Number of clips, Channels, Time, Height, Width), which is a common format for video processing models.

**Code Description**: The `val_pipeline` variable is a configuration list that defines a preprocessing pipeline for video data during the validation phase. This pipeline ensures that all validation videos are processed in a consistent and deterministic manner before being fed into the model for evaluation. The process starts with decoding the video file into frames. Next, the frames are resized so that their height is 256 pixels. Following this, a 256x256 pixel crop is taken from the center of each frame. This deterministic cropping is standard for validation to ensure reproducible evaluation results. Finally, the tensor's shape is formatted to the "NCTHW" layout, which is the expected input format for the model.

**Relationship with other objects**:
· `val_dataloader`: The `val_pipeline` is assigned to the `pipeline` key within the `val_dataloader` configuration. This links the defined transformations directly to the validation data loading process.
· `train_pipeline`: This pipeline is the validation counterpart to the `train_pipeline`. Unlike the `train_pipeline`, which may include random augmentations like `RandomCrop` to improve model robustness, the `val_pipeline` uses deterministic operations like `CenterCrop` to ensure consistent and comparable evaluation metrics across different validation runs.

**Note**: This pipeline is specifically intended for validation and testing. The use of `CenterCrop` instead of a random crop is a deliberate choice to remove randomness from the evaluation process, allowing for a stable and objective assessment of the model's performance.
## FunctionDef split_into_chunks(text, size)
**WebGLUniforms**: **Manages the uniforms of a specific WebGL program, handling their retrieval, parsing, and value uploading.**

**Parameters**: The parameters of this class's constructor.
· gl: The WebGL rendering context.
· program: The WebGL program object from which to extract the uniforms.

**Code Description**: The `WebGLUniforms` class is a utility for managing uniforms in a WebGL shader program. Upon instantiation, its constructor queries the provided `WebGLProgram` to get a list of all active uniforms. It iterates through each active uniform, retrieving its name, type, size, and memory address (location) from the WebGL context.

Based on the uniform's name and type, it creates a corresponding wrapper object to manage it. This logic is handled by an internal factory that creates one of three types of objects:
· `SingleUniform`: Manages simple, non-array uniforms (e.g., `float`, `vec3`, `mat4`, `sampler2D`).
· `PureArrayUniform`: Manages arrays of simple types (e.g., `vec3[4]`, `sampler2D[8]`).
· `StructuredUniform`: Manages complex data structures, specifically arrays of structs (e.g., `struct Light { vec3 color; }; uniform Light lights[2];`). It recursively breaks down the struct into a map of `SingleUniform` or `PureArrayUniform` instances.

Each of these wrapper objects contains a highly optimized `setValue` function that is generated specifically for the uniform's data type. For example, a `vec3` uniform will get a `setValue` function that calls `gl.uniform3fv`, and a `mat4` uniform will get one that calls `gl.uniformMatrix4fv`. This pre-generation of setter functions avoids expensive type checks during the render loop.

The class also provides two static helper methods:
· `upload(gl, seq, values, textures)`: This method iterates through a sequence of uniform wrapper objects (`seq`), finds the corresponding data in the `values` object, and calls the specialized `setValue` method on each uniform to upload its data to the GPU. For texture uniforms (`sampler2D`, `samplerCube`, etc.), it uses the `textures` manager to bind the texture to a texture unit before setting the uniform value.
· `seqWithValue(seq, values)`: This method filters a sequence of uniform wrappers, returning a new array containing only those uniforms whose IDs are present as keys in the `values` object. This can be used as an optimization to only process uniforms that need updating.

**Relationship with other objects**: An instance of `WebGLUniforms` is created and owned by a `WebGLProgram` object. When a `WebGLProgram` is successfully compiled and linked, it immediately creates a `WebGLUniforms` object for itself, passing its own program identifier and the WebGL context. This ensures that every shader program has a dedicated manager that knows about its specific set of uniforms and how to update them efficiently. The renderer then uses this `WebGLUniforms` instance, retrieved via the `WebGLProgram`, to set uniform values before issuing a draw call.

**Return**: The constructor returns a new instance of `WebGLUniforms`.
