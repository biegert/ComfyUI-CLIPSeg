# Custom Nodes for [ComfyUI](https://github.com/comfyanonymous/ComfyUI): CLIPSeg and CombineSegMasks
## This repository contains two custom nodes for ComfyUI that utilize the [CLIPSeg model](https://huggingface.co/docs/transformers/main/en/model_doc/clipseg) to generate masks for image inpainting tasks based on text prompts.


### 1. CLIPSeg
The CLIPSeg node generates a binary mask for a given input image and text prompt.

**Inputs:**

- image: A torch.Tensor representing the input image.
- text: A string representing the text prompt.
- blur: A float value to control the amount of Gaussian blur applied to the mask.
- threshold: A float value to control the threshold for creating the binary mask.
- dilation_factor: A float value to control the dilation of the binary mask.

**Outputs:**

- tensor_bw: A torch.Tensor representing the binary mask.
- image_out_hm: A torch.Tensor representing the heatmap overlay on the input image.
- image_out_bw: A torch.Tensor representing the binary mask overlay on the input image.

### 2. CombineSegMasks
The CombineSegMasks node combines two or optionally three masks into a single mask to improve masking of different areas.

**Inputs:**

- image: A torch.Tensor representing the input image.
- mask1: A torch.Tensor representing the first mask.
- mask2: A torch.Tensor representing the second mask.
- mask3 (optional): A torch.Tensor representing the third mask. Defaults to None.

**Outputs:**

- combined_mask: A torch.Tensor representing the combined mask.
- image_out_hm: A torch.Tensor representing the heatmap overlay of the combined mask on the input image.
- image_out_bw: A torch.Tensor representing the binary mask overlay of the combined mask on the input image.


## Installation
To use these custom nodes in your ComfyUI project, follow these steps:

1. Clone this repository or download the source code.
2. Put the clipseg.py file into your custom_nodes directory
3. ???
4. Profit


## Usage
Below is an example for the intended workflow. The [json file](https://github.com/biegert/ComfyUI-CLIPSeg/blob/main/workflow/inpaint_CLIPSeg.json) for the example can be found inside the 'workflow' directory 
![](https://github.com/biegert/ComfyUI-CLIPSeg/blob/main/workflow/workflow_0.png?raw=true)
![](https://github.com/biegert/ComfyUI-CLIPSeg/blob/main/workflow/workflow_1.png?raw=true)
![](https://github.com/biegert/ComfyUI-CLIPSeg/blob/main/workflow/workflow_2.png?raw=true)

## Requirements
- PyTorch
- CLIPSeg
- OpenCV
- numpy
- matplotlib

Make sure that you have the required libraries installed to the venv of ComfyUI.
