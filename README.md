![Screenshot 2023-08-04 212706](https://github.com/Hillobar/Rope/assets/63615199/114b4073-9a25-42cc-844d-1afc3625907b)

# Rope
Rope implements the insightface inswapper_128 model with a helpful GUI.
### Discord link: ###
[Discord](https://discord.gg/5CxhgRKBdN)

### Upcoming changes for Rope - Space Worm: ###
* Updated recording to use Target Video parameters (audio/video, keep the same quality as the original file)
* Mousewheel scroll on the time bar to control frame position
* Added an occluder model (experimental, very fast)
* Greatly increased performance for larger videos/multiple faces
* CLIP crashing fixed. Add as many words as you like!
* Detachable video preview
* Fixed most bugs related to changing options while playing. Adjust setting on the fly!
* GFPGAN now renders up to 512x512

### Preview: ###
in-progress

### Disclaimer: ###
Rope is a personal project that I'm making available to the community as a thank you for all of the contributors ahead of me. I don't have time to troubleshoot or add requested features, so it is provided as-is. Don't look at this code for example of good coding practices. I am primarily focused on performance and my specific use cases. There are plenty of ways to bork the workflow. Please see how to use below.

### Features: ###
* Real-time video player
* Optimized model paths (runs >30fps with GFPGAN on 3090Ti)
* Resizeable window
* Load, view, and select Source Videos and Source Faces from specified folders
* Identify Target Faces from current frame
* Map multiple Source Faces to mutiple Target Faces
* GFPGAN with blending
* Diffing with blending
* Adjust Face boudaries to match Source and Target Faces, with blending
* Set threads
* Set face matching threshhold
* Create videos with current settings
* Created videos add audio and compress file size
  
### Install: ###
Note: It's only configured for CUDA (Nvidia)
* Set up a local venv
  * python.exe -m venv venv
* Activate your new venv
  * .\venv\Scripts\activate
* Install requirements
  * .\venv\Scripts\pip.exe install -r .\requirements.txt
* Place [GFPGANv1.4.onnx](https://github.com/Hillobar/Rope/releases/download/v1.0/GFPGANv1.4.onnx)  and [inswapper_128_fp16.onnx](https://github.com/Hillobar/Rope/releases/download/v1.0/inswapper_128.fp16.onnx) in the root directory
* Do this if you've never installed roop or Rope (or any other onnx runtimes):
  * Install CUDA Toolkit 11.8
  * Install dependencies:
  * pip uninstall onnxruntime onnxruntime-gpu
  * pip install onnxruntime-gpu==1.15.1
* Double-click on Rope.bat!

### To use: ###
* Run Rope.bat
* Set your Target Video, Source Faces, and Video Output folders
  * Buttons will be gold if they are not set
  * Only places videos or images in the respective folders. Other files my bork it
  * Rope creates a JSON file to remember your last set paths
  * I like to keep my folders <20 or so items. Helps to organize and reduces load times
* Click on the Load Models button to initialize Rope
* Select a video to load it into the player
* Find Target Faces
  * Adds all faces in the current frame to the Found Faces pane
  * If a Face is already Found and in the pane, it won't re-add it
* Click a Source Face
  * Source Face number will appear
* Select a Target Face
  * Target Faces will show assignment number to the Source Face number
  * Toggle a Target Face to unselect and reassign to currently selected Source Face
* Continue to select other Source Faces and assign them to Target Faces
* Click SWAP to enable face swapping
* Click PLAY to play
* Click REC to arm recording
  * Click PLAY to start recording using the current settings
  * Click PLAY again to stop recording, otherwise it will record to the end of the Target Video
* Toggle GFPGAN, adjust blending amount
* Toggle Diffing, adjust blending maount
* Lower the threshhold if you have multiple Source Faces assigned and they are jumping around. You can also try Clearing and Finding new Target Faces (disable SWAP first)
* Modify the Masking boudaries
* Use CLIP to identify objects to swap or not swap (e.g Pos: face, head; Neg: hair, hand), adjust the gain of the words, and set the blur amount around the items
* Change # threads to match your GPU memory (24GB ~9 threads with GFPGAN on, more threads w/o GFPGAN)
  * Start with the lowest you think will run and watch your GPU memory.
  * Once you allocate memory by increasing # threads, you can't un-allocate it by reducing # threads. You will need to restart Rope.
* In general, always stop the video before changing anything. Otherwise, it might bork. Reassigning faces is okay
* If it does bork, reload the video (reclick on it). If that doesn't work you'll need to restart
  
