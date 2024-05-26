python -m venv venv
.\venv\Scripts\activate
pip install jupyter
pip install opencv-python
jupyter notebook

cd RealTimeObjectDetection-main\Tensorflow\labelImg
pip install PyQt5==5.15.4
pyrcc5 -o libs/resources.py resources.qrc
pip install pyinstaller
pyinstaller --hidden-import=pyqt5 --hidden-import=lxml -F -n "labelImg" -c labelImg.py -p ./libs -p ./
pip install lxml
python labelimg.py
cd ..
cd ..
cd ..
pip install pandas
pip install tensorflow
pip install protobuf
pip install Pillow
pip install anyio async-lru
pip install tensorflow-object-detection-api
jupyter notebook



1)Issues you will face while installing TensorFlow ---- 

The issue is due to the long path name exceeding the Windows maximum path length limit. To fix this, you have two options:

Option 1: Enable Windows Long Path support

Open the Registry Editor (Press Win + R and type regedit).
Navigate to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem.
Create a new DWORD (32-bit) Value named LongPathsEnabled and set its value to 1.
Restart your system.
Option 2: Use a shorter path for your virtual environment

Create a new virtual environment in a directory with a shorter path.
Activate the new virtual environment.
Try installing the packages again using pip.

2)To Setup CUDA
commands you need to execute to set up the environment variables for CUDA Toolkit v12.3 on Windows:

Go to Start and search for “environment variables”.

Click “Edit the system environment variables”. This should open the “System Properties” window.

In the opened window, click the “Environment Variables…” button to open the “Environment Variables” window.

Under “System variables”, find and select the Path system variable, then click “Edit…”

Add the following paths to the list of paths, then click “OK” to save the changes:

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.3\bin

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.3\libnvvp

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.3\include

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.3\extras\CUPTI\lib64

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.3\cuda\bin

3)To Fix the Gfile Issue
Open - 
C:\Affan\Affan\__CODING__\__PROJECTS__\Sign Lang To Text\RealTimeObjectDetection-main\venv\Lib\site-packages\object_detection\utils\label_map_utils.py

and then search for load_labelmap
and then change it to
with tf.io.gfile.GFile(path, 'r') as fid:
4)To Fix the generatetf record issue
change 
label_map = label_map_util.load_labelmap(args.labels_path)
label_map_dict = label_map_util.get_label_map_dict(label_map)
to
label_map_dict = label_map_util.get_label_map_dict(args.labels_path)
5) ParseError: 172:3 : Message type "object_detection.protos.TrainConfig" has no field named "fine_tune_checkpoint_version"
to fix this
Remove fine_tune_checkpoint_version line (line 172 according to what you posted) from pipeline.config


