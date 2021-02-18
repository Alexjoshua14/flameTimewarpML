# flameTimewarpML
Machine Learning frame interpolation tool for Autodesk Flame.  

Based on arXiv2020-RIFE, original implementation: https://github.com/hzwer/arXiv2020-RIFE
```
@article{huang2020rife,
  title={RIFE: Real-Time Intermediate Flow Estimation for Video Frame Interpolation},
  author={Huang, Zhewei and Zhang, Tianyuan and Heng, Wen and Shi, Boxin and Zhou, Shuchang},
  journal={arXiv preprint arXiv:2011.06294},
  year={2020}
}
```
Flame's animation curve interpolation code from Julik Tarkhanov:
https://github.com/guerilla-di/flame_channel_parser

## Installation
### Single workstation

* Download latest release from [Releases](https://github.com/talosh/flameTimewarpML/releases) page
* Unpack and copy included flameTimewarpML.py to /opt/Autodesk/shared/python.
* Start Flame or refresh your python hooks if already started with FLAME->Python->Rescan Python Hooks (Ctrl+Shift+H+P). flameTimewarpML installation dialog should appear. Click 'Continue' and give it about a minute to unpack its files in background. Check progress info in console. After the job is done you'll see another dialog confirming that you can start using app. If you right-click on a clip in Desktop reels or Libraries you should see new Timewarp ML menu.

### Centralized / Manual Install

* Get the source from [Releases](https://github.com/talosh/flameTimewarpML/releases) page or directly from repo:
```
git clone https://github.com/talosh/flameTimewarpML.git
```
* Althiugh it is possible to share the code location between platforms Miniconda3 should be placed separately for Mac and Linux.
This exmaple will use /Volumes/software/flameTimewarpML for Mac and /mnt/software/flameTimewarpML for Linux as code location.
Miniconda3 location are /Volumes/software/miniconda3 for Mac and /mnt/software/miniconda3 for Linux.
* Copy the contents of 'bundle' folder to the code location.
Mac:
```
cp -a bundle/* /Volumes/software/flameTimewarpML/
```
Linux:
```
cp -a bundle/* /mnt/software/flameTimewarpML/
```

* Download Miniconda3 for Python 3.8 from https://docs.conda.io/en/latest/miniconda.html Shell installer is used for this example.

* Install Miniconda3 to centralized location:
Mac:
```
sh Miniconda3-latest-MacOSX-x86_64.sh -bu -p /Volumes/software/miniconda3/
```
Linux:
```
sh Miniconda3-linux-MacOSX-x86_64.sh -bu -p /mnt/software/flameTimewarpML/
```

* Init installed Miniconda3 environment:
Mac:
```
/Volumes/software/flameTimewarpML/init_env  /Volumes/software/miniconda3/
```
Linux:
```
/mnt/software/flameTimewarpML/init_env  /mnt/software/miniconda3/
```

there should be (base) before shell prompt. python --version should give Python 3.8.5 or greater

* From this shell prompt install dependency libraries with:
Mac:
```
pip3 install -r /Volumes/software/flameTimewarpML/requirements.txt
```
Linux:
```
pip3 install -r /mnt/software/flameTimewarpML/requirements.txt
```

* If your network is not connected to internet install Miniconda3 on the machine that is connected to internet and download dependency packages:
```
pip3 download -r bundle/requirements.txt -d packages_folder
```
then it is possible to install packages from given folder:
```
pip3 install -r /Volumes/software/flameTimewarpML/requirements.txt --no-index --find-links /Volumes/software/flameTimewarpML/packages_folder
```

* set FLAMETWML_BUNDLE_MAC, FLAMETWML_MINICONDA_MAC environment variables on Mac and 
FLAMETWML_BUNDLE_LINUX, FLAMETWML_MINICONDA_LINUX on Linux to point code and miniconda locations. 
It is also possible to edit flameTimewarpML.py file to add paths directly:

```
# Configurable settings
FLAMETWML_BUNDLE_MAC = '/Volumes/software/flameTimewarpML/'
FLAMETWML_BUNDLE_LINUX = '/mnt/software/flameTimewarpML/'
FLAMETWML_MINICONDA_MAC = '/Volumes/software/miniconda3/'
FLAMETWML_MINICONDA_LINUX = '/mnt/software/miniconda3/'
menu_group_name = 'Timewarp ML'
DEBUG = False
```

It is also possible to set FLAMETWML_BUNDLE_MAC and FLAMETWML_MINICONDA_MAC environment variables 

* Copy edited flameTimewarpML.py to your Flame python scripts folder