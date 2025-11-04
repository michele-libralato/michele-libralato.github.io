---
title: "Dynamism: Animating Motion Traces"
date: 2025-11-05
categories: [video, art-science, python]
---
Giacomo Balla, with his Futurist works (such as _Dynamism of a Dog on a Leash_), 
sought to depict successive positions of a moving form in one image, giving a 
sense of acceleration, decomposition into phases, and dynamic continuity.
A similar effect has been obtained by Xavi Bou in his _Ornithographies_ that 
compile sequential images of birds in flight into a single overlapping, 
ghost-trail pattern; each flight path becomes a visual trace in the sky.
This description of the flight of birds have been researched also by Julia Daser
in the dynamic sculpture _Birds in Flight_ that explores how to 
compress temporal sequences spatially. Other fiction approached the theme of 
the representation of the movement in the fourth dimension using concepts as
space-time worms or space-time sausages.

We can easily reproduce an animated version of the ornithographies using a
still video of birds flying, ffmpeg and Python. 

Process:
- film a clip of birds flying with a tripod or similar.
- extract (via ffmpeg) all the frames of a video clip,
- process / remix / blend them algorithmically (via Python) to produce overlapping traces,
- reconstruct them back into a video (again via ffmpeg) so the viewer sees a “motion trace” effect.

Frame extraction requires the installation of ffmpeg, remeber to put it in the environmental variables.
create a folder, copy the mp4 in the folder and open a terminal at that folder.
Extract the frames with this line:
```
ffmpeg -i video.mp4 frame_%04d.png
```
Ffmpeg creates the frame images. Now create and run a .py file with the following script:
``` python
from skimage.io import imread, imsave
from skimage.color import rgb2gray
import numpy as np
from glob import glob
import os

# === Setup ===
input_folder = ""
output_folder = "timelapse_frames"
os.makedirs(output_folder, exist_ok=True)

frame_files = sorted(glob(os.path.join(input_folder, "*.png")))
if not frame_files:
    raise FileNotFoundError("No PNG files found in 'frames/'")

print(f"Found {len(frame_files)} frames.")

# === Initialize composite ===
composite = imread(frame_files[0]).copy()
composite_gray = rgb2gray(composite)

# Save first frame
imsave(f"{output_folder}/frame_0000.png", composite)

# === Process frames ===
for i, path in enumerate(frame_files[1:], start=1):
    frame = imread(path)
    frame_gray = rgb2gray(frame)

    # Create darker mask
    darker_mask = frame_gray < composite_gray

    # Update composite image
    if np.any(darker_mask):
        composite[darker_mask] = frame[darker_mask]
        composite_gray[darker_mask] = frame_gray[darker_mask]

    # Save current composite
    out_path = f"{output_folder}/frame_{i:04d}.png"
    imsave(out_path, composite)
    print(f"[{i+1}/{len(frame_files)}] Saved {out_path}")

print("\n All intermediate frames saved.")
```

the script creates a new folder with the frames of the new video.
To join them in a sinlge .mp4 file use the following ffmpeg command:

```
ffmpeg -framerate 30 -i timelapse_frames/frame_%04d.png -c:v libx264 -pix_fmt yuv420p output.mp4
```
