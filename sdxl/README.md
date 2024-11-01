# SDXL 示例

[SDXL 基本检查点可以像ComfyUI](https://github.com/comfyanonymous/ComfyUI)中的任何常规检查点一样使用。唯一重要的是，为了获得最佳性能，分辨率应设置为 1024x1024 或具有相同像素数量但不同纵横比的其他分辨率。例如：896x1152 或 1536x640 是不错的分辨率。

要将基础与精炼器结合使用，您可以使用此工作流程。您可以下载此图像并加载它或将其拖到 ComfyUI 上以获取它。

![Example](sdxl_simple_example.png)

您还可以像在此工作流程中一样为基础和精炼者提供不同的提示。

![Example](sdxl_refiner_prompt_example.png)


### 修订

[ReVision 与unCLIP](https://comfyanonymous.github.io/ComfyUI_examples/unclip)非常相似，但行为更偏向概念层面。你可以将一张或多张图片传递给它，它会从这些图片中获取概念，并以此为灵感创建新的图片。

首先下载[CLIP-G Vision](https://huggingface.co/comfyanonymous/clip_vision_g/blob/main/clip_vision_g.safetensors)并将其放入您的 ComfyUI/models/clip_vision/ 目录中。

以下是可以拖动或加载到 ComfyUI 的示例工作流程。在此示例中，正文本提示被归零，以便最终输出更紧密地遵循输入图像。

![Example](sdxl_revision_zero_positive.png)


如果您想使用文本提示，您可以使用此示例：

![Example](sdxl_revision_text_prompts.png)

请注意，强度选项可用于增加每个输入图像对最终输出的影响。它还可以处理任意数量的图像，方法是使用单个 unCLIPConditioning 或将多个图像链接在一起，如上例所示。

如果您需要的话，以下是上述工作流程的输入图像：

<img src="../unclip/mountains.png" width="256" /><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><img src="../unclip/sunset.png" width="256" />
