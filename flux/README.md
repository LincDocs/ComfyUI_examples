# Flux 示例

[Flux 是黑森林实验室](https://blackforestlabs.ai/announcing-black-forest-labs/)的扩散模型系列

[有关您可以在ComfyUI](https://github.com/comfyanonymous/ComfyUI)中轻松使用的易于使用的单文件版本，请参见下文：[FP8 检查点版本](https://comfyanonymous.github.io/ComfyUI_examples/flux/#simple-to-use-fp8-checkpoint-version)
## ## 普通完整版

### 常规版本需要下载的文件

如果您的 ComfyUI/models/clip/ 目录中还没有 t5xxl_fp16.safetensors 或 clip_l.safetensors，您可以在[此链接上找到它们。](https://huggingface.co/comfyanonymous/flux_text_encoders/tree/main)您可以使用 t5xxl_fp8_e4m3fn.safetensors 来降低内存使用率，但如果您的 RAM 超过 32GB，则建议使用 fp16。

[VAE 可在这里](https://huggingface.co/black-forest-labs/FLUX.1-schnell/blob/main/ae.safetensors)找到，并且应该放在您的 ComfyUI/models/vae/ 文件夹中。

### 内存不足时的提示：

使用单个文件 fp8 版本，您可以通过查看[以下内容找到](https://comfyanonymous.github.io/ComfyUI_examples/flux/#simple-to-use-fp8-checkpoint-version)

您可以将“加载扩散模型”节点中的 weight_dtype 设置为 fp8，这将使内存使用量降低一半，但可能会稍微降低质量。您也可以下载示例。
### Flux 开发

[您可以在此处](https://huggingface.co/black-forest-labs/FLUX.1-dev)找到 Flux Dev 扩散模型权重。将 flux1-dev.safetensors 文件放在：ComfyUI/models/unet/ 文件夹中。

然后，您可以在 ComfyUI 中加载或拖动以下图像以获取工作流程：

![Example](flux_dev_example.png)

### Flux Schnell

Flux Schnell 是一个精简的 4 步骤模型。

[您可以在此处](https://huggingface.co/black-forest-labs/FLUX.1-schnell/blob/main/flux1-schnell.safetensors)找到 Flux Schnell 扩散模型权重，该文件应放在：ComfyUI/models/unet/ 文件夹中。

然后，您可以在 ComfyUI 中加载或拖动以下图像以获取工作流程：

![Example](flux_schnell_example.png)

## 简单易用的 FP8 Checkpoint 版本

### Flux 开发

[您可以在此处](https://huggingface.co/Comfy-Org/flux1-dev/blob/main/flux1-dev-fp8.safetensors)找到一个易于使用的 Flux dev 检查点，将其放在：ComfyUI/models/checkpoints/ 目录中。

该文件可以通过常规“Load Checkpoint”节点加载。使用时请确保将 CFG 设置为 1.0。

请注意，fp8 会稍微降低质量，因此如果您有资源，建议使用官方完整的 16 位版本。

然后，您可以在 ComfyUI 中加载或拖动以下图像以获取工作流程：

![Example](flux_dev_checkpoint_example.png)

### Flux Schnell

[对于 Flux schnell，您可以在此处](https://huggingface.co/Comfy-Org/flux1-schnell/blob/main/flux1-schnell-fp8.safetensors)获取检查点，并将其放入：ComfyUI/models/checkpoints/ 目录中。

然后，您可以在 ComfyUI 中加载或拖动以下图像以获取工作流程：

![Example](flux_schnell_checkpoint_example.png)

### Flux Controlnets

[XLab 和 InstantX + Shakker Labs 已发布用于 Flux 的控制网。您可以在此处](https://huggingface.co/InstantX/FLUX.1-dev-Controlnet-Canny/blob/main/diffusion_pytorch_model.safetensors)找到 InstantX Canny 模型文件（在下面的示例中重命名为 instantx_flux_canny.safetensors），[在此处找到深度控制网，](https://huggingface.co/Shakker-Labs/FLUX.1-dev-ControlNet-Depth/blob/main/diffusion_pytorch_model.safetensors)[在此处找到](https://huggingface.co/Shakker-Labs/FLUX.1-dev-ControlNet-Union-Pro/blob/main/diffusion_pytorch_model.safetensors)Union 控制网。

[XLab 控制网可以在这里](https://huggingface.co/XLabs-AI/flux-controlnet-collections)找到。

将这些文件放在`ComfyUI/models/controlnet`目录下。

将此图像拖入 ComfyUI，尝试示例 Canny Controlnet 工作流程。

![Example](flux_controlnet_example.png)

如果你需要为 canny 提供一个示例输入图像，请使用[这个](https://comfyanonymous.github.io/ComfyUI_examples/flux/girl_in_field.png)。将其放在下面`ComfyUI/input`。
