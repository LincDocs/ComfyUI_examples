# 修复示例 (局部重绘示例)

![Example](inpaint_example.png)

在此示例中，我们将使用此图像。下载它并将其放在您的输入文件夹中。

![Example](yosemite_inpaint_example.png)

此图像的一部分已使用 gimp 擦除为 alpha，alpha 通道是我们将用作修复的蒙版。如果使用 GIMP，请确保保存透明像素的值以获得最佳效果。

ComfyUI 还具有一个掩码编辑器，可以通过右键单击 LoadImage 节点中的图像并“在 MaskEditor 中打开”来访问。

[可以在ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载以下图像以获取完整的工作流程。

使用 v2 修复模型修复一只猫：

![Example](inpain_model_cat.png)

使用 v2 修复模型修复女性图像：

![Example](inpain_model_woman.png)

它也适用于非修复模型。以下是使用 anythingV3 模型的示例：

![Example](inpaint_anythingv3_woman.png)

### Outpainting (外绘)

您还可以使用类似的工作流程进行外绘。外绘与内绘是一回事。有一个“Pad Image for Outpainting”节点，可以在创建适当的蒙版时自动填充图像以进行外绘。在此示例中，此图像将被外绘：

![Example](yosemite_outpaint_example.png)

使用 v2 修复模型和“Pad Image for Outpainting”节点（在 ComfyUI 中加载它以查看工作流程）：

![Example](inpain_model_outpainting.png)

