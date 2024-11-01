# 模型合并示例

这些工作流程背后的想法是，您可以使用多个模型合并来执行复杂的工作流程，测试它们，然后在对结果满意后通过取消静音 CheckpointSave 节点来保存检查点。默认情况下，CheckpointSave 节点将检查点保存到 output/checkpoints/ 文件夹。

您可以在以下位置找到这些节点：advanced->model_merging

第一个例子是两个不同检查点之间简单合并的基本示例。

您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获得完整的工作流程。

![Example](model_merging_basic.png)

在 ComfyUI 中，保存的检查点包含用于生成它们的完整工作流程，因此它们可以像图像一样加载到 UI 中以获取用于创建它们的完整工作流程。

此示例是使用简单块合并来合并 3 个不同检查点的示例，其中 unet 的输入、中间和输出块可以具有不同的比率：

![Example](model_merging_3_checkpoints.png)

由于 Loras 是模型权重的补丁，因此它们也可以合并到模型中：

![Example](model_merging_lora.png)

您还可以减去模型权重并添加它们，就像在本例中一样，使用以下公式从非修复模型创建修复模型：`(inpaint_model - base_model) * 1.0 + other_model` 如果您熟悉其他 UI 中的“添加差异”选项，这就是在 ComfyUI 中执行的操作。

![Example](model_merging_inpaint.png)

您应该注意的一件重要事情是，模型会以硬件推理所用的精度进行合并和保存，因此通常为 16 位浮点数。如果您希望以 32 位浮点数进行合并，请使用以下方法启动 ComfyUI：–force-fp32

### 高级合并

#### CosXL

以下是如何使用合并功能从常规 SDXL 模型创建 CosXL 模型的示例。要求是[CosXL 基础模型](https://huggingface.co/stabilityai/cosxl)、[SDXL 基础模型](https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/blob/main/sd_xl_base_1.0_0.9vae.safetensors)和要转换的 SDXL 模型。在此示例中，我使用了[albedobase-xl](https://civitai.com/models/140737/albedobase-xl)。

![Example](model_merging_cosxl.png)


