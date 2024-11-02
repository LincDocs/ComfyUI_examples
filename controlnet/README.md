# ControlNet 和 T2I-Adapter 示例

请注意，在这些示例中，原始图像直接传递到 ControlNet/T2I 适配器。

如果您想要获得良好的结果，每个 ControlNet/T2I 适配器都需要将传递给它的图像设置为特定格式，例如深度图、精明图等，具体取决于特定模型。

ControlNetApply 节点不会将常规图像转换为深度图、精明图等。您必须单独执行此操作，或使用节点对图像进行预处理，您可以在此处找到：[此处](https://github.com/Fannovel16/comfy_controlnet_preprocessors)

您可以在此处找到最新的 controlnet 模型文件：[原始版本](https://huggingface.co/lllyasviel/ControlNet-v1-1/tree/main)或[较小的 fp16 safetensors 版本](https://huggingface.co/comfyanonymous/ControlNet-v1-1_fp16_safetensors/tree/main)

对于 SDXL，stable.ai 已发布 Control Loras，您可以[在这里（排名 256）](https://huggingface.co/stabilityai/control-lora/tree/main/control-LoRAs-rank256)或[这里（排名 128）](https://huggingface.co/stabilityai/control-lora/tree/main/control-LoRAs-rank128)找到。它们的使用方式与常规 ControlNet 模型文件完全相同（将它们放在同一目录中）。

ControlNet 模型文件位于 ComfyUI/models/controlnet 目录中。

### 涂鸦 ControlNet

这是一个如何使用控制网的简单示例，此示例使用 scribble 控制网和 AnythingV3 模型。您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载此图像以获取完整的工作流程。

![Example](controlnet_example.png)

Here is the input image I used for this workflow:

<img src="./input_scribble_example.png" width="256" />

### 【比较】T2I-Adapter 和 ControlNets

T2I 适配器比 ControlNets 效率高得多，因此我强烈推荐它们。ControlNets 会显著降低生成速度，而 T2I 适配器对生成速度几乎没有任何负面影响。

在 ControlNets 中，ControlNet 模型每次迭代运行一次。对于 T2I-Adapter，该模型总共运行一次。

T2I-Adapters 的使用方式与 ComfyUI 中的 ControlNets 相同：使用 ControlNetLoader 节点。

[这是本示例源](https://commons.wikimedia.org/wiki/File:Stereogram_Tut_Shark_Depthmap.png)中将使用的输入图像：

<img src="./shark_depthmap.png" width="512" />

深度 T2I 适配器的使用方法如下：

![Example](depth_t2i_adapter.png)

以下是深度控制网的使用方法。请注意，此示例使用 DiffControlNetLoader 节点，因为所使用的控制网是差异控制网。差异控制网需要正确加载模型的权重。DiffControlNetLoader 节点还可用于加载常规控制网模型。加载常规控制网模型时，其行为与 ControlNetLoader 节点相同。

![Example](depth_controlnet.png)

您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获得完整的工作流程。

### 姿势 ControlNet

这是本示例中将使用的输入图像：

![Example](pose_worship.png)


下面是一个示例，第一次使用带有控制网的 AnythingV3，第二次使用不带控制网的 AOM3A3（深渊橙色混合 3）并使用它们的 VAE。

![Example](2_pass_pose_worship.png)

[您可以在ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载此图像以获取完整的工作流程。

### 混合 ControlNets

可以像这样应用多个 ControlNet 和 T2I 适配器并产生有趣的结果：

![Example](mixing_controlnets.png)

[您可以在ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载此图像以获取完整的工作流程。

输入图像：

<img src="./pose_present.png" width="256" /><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><img src="./house_scribble.png" width="256" />

