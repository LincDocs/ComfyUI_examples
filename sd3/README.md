# SD3 示例

## SD3.5

如果您还没有从 SD3、Flux 或其他模型下载文本编码器文件，请先下载它们：（[clip_l.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/text_encoders/clip_l.safetensors)、[clip_g.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/text_encoders/clip_g.safetensors)和 t5xxl）（如果您的 ComfyUI/models/clip/ 文件夹中还没有这些文件）。对于 t5xxl，如果您的 RAM 超过 32GB，我建议您使用[t5xxl_fp16.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/text_encoders/t5xxl_fp16.safetensors) ，如果没有，我建议您使用[t5xxl_fp8_e4m3fn_scaled.safetensors 。](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/text_encoders/t5xxl_fp8_e4m3fn_scaled.safetensors)

SD3.5 模型系列包含一个大型 8B 模型和一个中型 2.5B 模型。中型模型速度更快，占用的内存更少，但对某些概念的理解可能不太复杂。我建议下载这两个模型，并试验它们各自如何响应您的提示。

sd3.5_large.safetensors和[sd3.5_medium.safetensors](https://huggingface.co/stabilityai/stable-diffusion-3.5-large/tree/main)文件（选择您想要的文件并将其放在 ComfyUI/models/checkpoints/ 目录中）不包含文本编码器/CLIP 权重，因此您必须单独加载它们才能使用该文件，就像以下示例一样[：](https://huggingface.co/stabilityai/stable-diffusion-3.5-medium/tree/main)

![Example](sd3.5_text_encoders_example.png)

要使用[sd3.5_large_turbo.safetensors](https://huggingface.co/stabilityai/stable-diffusion-3.5-large-turbo/tree/main)文件（将其放在您的 ComfyUI/models/checkpoints/ 目录中），您可以使用上述示例并将步骤设置为 4 并将 cfg 设置为 1.2。

为方便起见，有一个易于使用的一体化检查点文件[sd3.5_large_fp8_scaled.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/sd3.5_large_fp8_scaled.safetensors)（将其放在 ComfyUI/models/checkpoints/ 目录中），可像任何其他检查点文件一样在默认工作流程中使用。还有一个适用于 SD3.5 中型的文件：[sd3.5_medium_incl_clips_t5xxlfp8scaled.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/sd3.5_medium_incl_clips_t5xxlfp8scaled.safetensors)

请参阅此工作流程作为示例。

![Example](sd3.5_simple_example.png)

提醒一下，您可以保存这些图像文件并将其拖动或加载到 ComfyUI 中以获取工作流程。

[旧 SD3 介质示例](https://comfyanonymous.github.io/ComfyUI_examples/sd3/README_old.html)


