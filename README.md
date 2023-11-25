# Stable Diffusion Face Dataset
Images of men and women, mainly faces, seeking to generate more realistic images (without wax skin), generated with Stable Diffusion 1.5, 2.1 and SDXL.

## About the images:

All images were generated with Stable Diffusion 1.5, 2.1, and SDXL 1.0 checkpoint.
The main objective was to generate photos that were as realistic as possible, without any specific style, focusing mainly on the face.

- Images in `512x512px` resolution were generated using SD 1.5;
- Images in `768x768px` resolution were generated using SD 2.1;
- Images in `1024x1024px` resolution were generated using SD XL 1.0;

## How the images are generated:

All images were generated using only the base checkpoints of Stable Diffusion (1.5, 2.1, and SDXL 1.0 - no LORA was used), with simple prompts such as `photo of a woman`, but including negative prompts to try to maintain a certain quality.
Some prompts were different, such as `RAW photo of a woman` or `photo of a woman without a background`, but nothing too complex.

After the images were generated, only the top 1500 images were selected, and some underwent additional editing to fix facial features (especially eyes) and other minor corrections.
Typically, the edits were done manually, which is why the number of images was reduced and the `person` class was excluded.

## Post process:

The post-processing workflow varies depending on the generated image. I selected the best images where the facial region was acceptable. If there was a possibility of improvement (using some form of image editing), I attempted to enhance it, especially the eyes and mouths (SD always introduces some issues in these areas, such as leaking eyes, crossed eyes, or triangular eyes - english is not my primary language and I don't know the correct term for these defects).

Images that had defective hands were discarded immediately.

The image editing was primarily done in Photoshop, using the **Neural Filter**, many masks and actions that I generated throughout the process.

Other images were enhanced using GFPGAN 1.3 and/or 1.4, along with other ESRGAN models in conjunction with Photoshop and additional masks.

After editing more than 5000 images manually, I ended up optimizing the workflow by generating a new YOLOv8 model (https://github.com/tobecwb/facial-features-yolo8x-seg) to segment the main areas of the face (eyebrows, eyes, nose and mouth), automatically generating masks for the rest of the images (but still required manual treatments on several images).

Some images had more than 5 different versions, and through masks, I selected different regions from each image until reaching the final result.

## Some notes:

I believe that the lowest quality images are those generated with Stable Diffusion 1.5 (512px), however, the images generated with Stable Diffusion 2.1 (768px) were the most difficult.
It is very challenging to get high quality images in version 2.1. Either the eyes are significantly off, the limbs are distorted, or something completely random is generated.
I had to generate much more than 5k images to select just 1500, and some still don't meet the desired quality.

The images generated in SDXL, in my opinion, are very similar to each other, especially the `woman` class.
Perhaps something in the negative prompt ended up influencing the images too much, however, I have no plans to generate new images (see below for the reason).
Maybe I'll leverage some other images I generated earlier while testing different workflows in ComfyUI, and commit later.

**Almost all images were generated using rented servers, so it's highly likely that I won't make significant updates to this project (due to cost and the limited hardware I have)**

## LICENSE:

All images are licensed under CC-BY-4.0 (Creative Commons Attribution 4.0 International).
Check the LICENSE.txt file for more information