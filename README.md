# chunky_aidn_training
Chunky training data for AI denoisers (WIP)

Reference: https://openimagedenoise.github.io/documentation.html#training

## Overview

We need one or more noisy scenes with one noiseless reference image. Albedo and normal maps must be rendered without postprocessing (ie Exposure=1, Postprocessing mode: None).

Examples SPPs
```
1, 2, 4, 8, 16, etc.. + ref
1, 7, 9, 100, etc. + ref
5 + ref	<-- Like... please provide more than just one data point...
```

Subdirectories do not matter so feel free to use them. As long as each filename consists of a name, the padded number of samples per pixel, the identifier (ID) of the feature (e.g. hdr, ldr, alb, nrm), and the file extension.

---

## Existing noiseless scene

If you have a noiseless scene already;

1. Load the scene and under Advanced set Output mode to TIFF (32-bit floating point) and save current frame to the following format: scene_SPP.hdr.tif (see oidn docs for allowed).
2. Make a copy of the scene and create some noisy images. Again, rename to scene_SPP.hdr.tif 
3. Finally enable the denosier plugin and render albedo and normal maps without post processing.

---

## Optional

If you can, please also duplicate and rename albedo and normal maps such that each .hdr.pfm file has an alb and nrm at the same SPP.

Convert all .tif and .pfm files to .exr (gimp can do this).

---

## Folder structure / example

Below is an example layout you can use.

```
|--scene1
	|-- view1_0001.alb.pfm
	|-- view1_0001.hdr.pfm
	|-- view1_0001.nrm.pfm
	|-- view1_0004.alb.pfm
	|-- view1_0004.hdr.pfm
	|-- view1_0004.nrm.pfm
	|-- view1_8192.alb.pfm
	|-- view1_8192.hdr.pfm
	|-- view1_8192.nrm.pfm
	|-- view2_0001.alb.pfm
	|-- view2_0001.hdr.pfm
	|-- view2_0001.nrm.pfm
	|-- view2_8192.alb.pfm
	|-- view2_8192.hdr.pfm
	|-- view2_8192.nrm.pfm
|--scene2
	|-- view1_000001.alb.pfm
	|-- view1_000001.hdr.pfm
	|-- view1_000001.nrm.pfm
	|-- view1_011111.alb.pfm
	|-- view1_011111.hdr.pfm
	|-- view1_011111.nrm.pfm
  
```

