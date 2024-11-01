# 2 Pass Txt2Img (高清修复) 示例

这些示例演示了如何实现“Hires Fix”功能。

您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获得完整的工作流程。

Hires 修复只是创建一个分辨率较低的图像，将其放大，然后通过 img2img 发送。请注意，在 ComfyUI 中，txt2img 和 img2img 是同一个节点。Txt2Img 是通过将空图像传递给具有最大去噪效果的采样器节点来实现的。

以下是 ComfyUI 中通过基本潜在升级执行此操作的简单工作流程：

![Example](hiresfix_latent_workflow.png)

## 非潜在升级

以下是如何使用[esrgan 升级器](https://comfyanonymous.github.io/ComfyUI_examples/upscale_models)进行升级步骤的示例。由于 ESRGAN 在像素空间中运行，因此图像在升级后必须转换为像素空间并转换回潜在空间。

![Example](hiresfix_esrgan_workflow.png)


## 更多示例

下面是一个更复杂的 2 次传递工作流程的示例，该图像首先使用 WD1.5 beta 3 幻觉模型生成，进行潜在升级，然后使用 cardosAnime_v10 进行第二遍传递：

![Example](latent_upscale_different_prompt_model.png)


