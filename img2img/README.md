# 图生图示例

这些是演示如何执行 img2img 的示例。

您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获得完整的工作流程。

Img2Img 的工作原理是加载一张类似此[示例图像的](https://github.com/comfyanonymous/ComfyUI/blob/master/input/example.png)图像，使用 VAE 将其转换为潜在空间，然后使用低于 1.0 的降噪对其进行采样。降噪控制添加到图像中的噪声量。降噪越低，添加的噪声越少，图像变化越小。

输入图像应放在输入文件夹中。

这是一个简单的 img2img 工作流程，它与默认的 txt2img 工作流程相同，但去噪设置为 0.87，并且将加载的图像而不是空图像传递给采样器。

![Example](img2img_workflow.png)
