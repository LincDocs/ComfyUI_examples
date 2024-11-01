# 区域构成示例

这些是演示 ConditioningSetArea 节点的示例。您可以在[ComfyUI](https://github.com/comfyanonymous/ComfyUI)中加载这些图像以获取完整的工作流程。

### 使用 Anything-V3 进行区域合成 + 然后使用 AbyssOrangeMix2_hard

这张图片包含 4 个不同的区域：夜晚、傍晚、白天、早晨

![Example](night_evening_day_morning.png)

ComfyUI 中的工作流程如下：

![Example](workflow_night_evening_day_morning.png)

该图像包含与上一个图像相同的区域，但顺序相反。

![Example](morning_day_evening_night.png)

通过添加另一个区域提示将主题添加到图像的底部中心。

![Example](night_evening_day_morning_subject.png)

## 通过区域构图提高图像的一致性

稳定扩散在生成分辨率接近 512x512 的方形图像时，可以创建最一致的图像。但是，如果我们想生成宽高比为 16:9 的图像，该怎么办？让我们生成一张坐着的主体的 16:9 图像。如果以正常方式生成，成功率会很低，因为四肢会不自然地延伸到图像上，并存在其他一致性问题。

通过使用区域构图并以方形区域作为主体，一致性将更高，并且由于它与图像的其余部分同时生成，因此整体图像的一致性将非常出色。

此工作流程使用 Anything-V3，这是一个 2 遍工作流程，其中第一遍使用区域合成来对图像左侧的主体进行合成。第二遍的原因只是为了提高分辨率，如果您对 1280x704 图像满意，则可以跳过第二遍。

![Example](square_area_for_subject.png)

在图像右侧添加一个红头发的主体，并带有区域提示。

第一遍输出 (1280x704):

![Example](square_area_for_2_subjects_first_pass.png)

第二遍输出 (1920x1088):

![Example](square_area_for_2_subjects.png)

第二遍输出图像说明了稳定扩散的行为之一。第二遍没有区域提示。您会注意到，对象 1 的头发是金色，带有粉红色高光，而对象 2 的头发是粉红色，而不是红色，这与第一遍输出中的情况不同。这是因为稳定扩散试图使整体图像与自身保持一致，而这样做的副作用之一是将头发颜色融合在一起。

