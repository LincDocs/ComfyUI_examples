# 视频示例

## 图像转视频

截至撰写本文时，有两个图像到视频检查点。以下是针对[生成 14 帧视频](https://huggingface.co/stabilityai/stable-video-diffusion-img2vid/blob/main/svd.safetensors)和[25 帧视频](https://huggingface.co/stabilityai/stable-video-diffusion-img2vid-xt/blob/main/svd_xt.safetensors)的官方检查点。将它们放在 ComfyUI/models/checkpoints 文件夹中。

使用图像转视频模型的最基本方法是给它一个初始图像，就像下面使用 14 帧模型的工作流程一样。您可以下载此 webp 动画图像并加载它或将其拖到[ComfyUI](https://github.com/comfyanonymous/ComfyUI)上以获取工作流程。

![Example](image_to_video.webp)
[Json 格式的工作流](https://comfyanonymous.github.io/ComfyUI_examples/video/workflow_image_to_video.json)

如果你想要精确的输入图像，你可以在[unCLIP 示例页面上找到它](https://comfyanonymous.github.io/ComfyUI_examples/unclip)

您还可以像在此工作流程中使用它们，该工作流程使用 SDXL 生成初始图像，然后将其传递给 25 帧模型：

![Example](txt_to_image_to_video.webp)
[Json 格式的工作流](https://comfyanonymous.github.io/ComfyUI_examples/video/workflow_txt_to_img_to_video.json)

#### 一些参数的解释：

- video_frames：要生成的视频帧的数量。
- motion_bucket_id：数字越高，视频中的动作越多。
- fps：fps 越高，视频的不流畅程度越低。
- 增强级别：添加到初始图像的噪声量，噪声级别越高，视频看起来就越不像初始图像。增加噪声级别可获得更多动感。
- VideoLinearCFGGuidance：此节点稍微改进了这些视频模型的采样，它所做的是线性缩放不同帧之间的 cfg。在上面的示例中，第一帧的 cfg 为 1.0（节点中的 min_cfg），中间帧为 1.75，最后一帧为 2.5。（采样器中设置的 cfg）。这样，距离初始帧较远的帧会获得逐渐更高的 cfg。
