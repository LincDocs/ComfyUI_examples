# Lora 示例

这些是演示如何使用 Loras 的示例。所有 LoRA 类型：Lycoris、loha、lokr、locon 等……都以这种方式使用。

您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获得完整的工作流程。

Loras 是在主 MODEL 和 CLIP 模型之上应用的补丁，因此要使用它们，请将它们放在 models/loras 目录中，然后像这样使用 LoraLoader 节点：

![Example](lora.png)

您可以通过链接多个 LoraLoader 节点来应用多个 Loras，如下所示：

![Example](lora_multiple.png)
