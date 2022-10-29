# Installation Instructions

1. To install the dependencies, I looked at the beginning of both 228_training_aerial_imagery.py and simple_multi_unet_model.py to see what dependencies were required. Within colab, I used pip install to install each dependency. I ended up installing matplotlib, patchify, Pillow, segmentation_models, keras-metric, and sklearn. The rest, such as numpy, tensorflow, and pytorch, did not need to be installed since colab comes with them.

2. To install NNI, I first installed and unzipped the required packages and softwares such as nni and ngrok. I then cloned NNI's official repo to get examples.  
Then I registered an account on NGROK and connected to my account through colab by using my authtoken. Next, I started both an NNI example and NGROK example on port 5000. I used get_ipython() to start the NGROk example. Last, I used the curl command with "http://localhost:4040/api/tunnels" to obtain the URL for NNI's web UI.

![NNI](https://user-images.githubusercontent.com/98201516/198856716-467a7927-37f4-40fb-9f87-3f495055a03f.jpg)
