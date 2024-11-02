# 常见问题

## 为什么即使我使用相同的种子，也会从 a1111 UI 获得不同的图像？

在 ComfyUI 中，噪声是在 CPU 上生成的。在 CPU 上生成噪声为 ComfyUI 带来了优势，即种子在不同的硬件配置上将更具可重复性，但也意味着它们将生成与在 GPU 上生成噪声的 UI（如 a1111）完全不同的噪声。在 GPU 上生成噪声与在 CPU 上生成噪声不会以任何方式影响性能。

在 ComfyUI 中，提示强度也更加敏感，因为它们没有标准化。一个非常简短的例子是，当执行

`(masterpiece:1.2) (best:1.3) (quality:1.4) girl`

a1111 ui 实际上正在做类似的事情（但涉及所有tokens）：

`(masterpiece:0.98) (best:1.06) (quality:1.14) (girl:0.81)`

在 ComfyUI 中，强度不会像这样平均，因此它会完全按照您的提示使用强度。

还有许多其他差异，但这两个差异影响最大。

## 为什么我得到一些小于 1.9GB 的检查点的不连贯图像？

一些罕见的checkpoint（例如 ProtoGen_X3.4）不附带 CLIP 权重。ComfyUI 中的 CLIPLoader 节点可用于加载 CLIP 模型权重，例如[可在 SD1.5 上使用的 CLIP L 权重](https://huggingface.co/comfyanonymous/flux_text_encoders/blob/main/clip_l.safetensors)。

## “Load LoRA”节点中的strength_model和strength_clip有什么区别？

这些单独的值控制 LoRA 分别应用于 CLIP 模型和主模型的强度。在大多数 UI 中，调整 LoRA 强度只有一个数字，例如将 lora 强度设置为 0.8 与将 strength_model 和 strength_clip 都设置为 0.8 相同。

您可以在 ComfyUI 中同时调整两者的原因是，LoRA 的 CLIP 和 MODEL/UNET 部分很可能已经学习了不同的概念，因此分别调整它们可以为您提供更好的图像。
