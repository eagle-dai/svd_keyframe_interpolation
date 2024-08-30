
## Environment Setup

```bash
python -m venv ./venv
source ./venv/bin/activate
# To activate venv on Windows (cmd) : .\venv\Scripts\activate
# To activate venv on Windows (bash): source ./venv/Scripts/activate

python -m pip install --upgrade pip
pip install -r requirements_my.txt --proxy http://proxy2:8081
# "--proxy" switch is optional, use it if you are behind a proxy.
```

### Verify GPU
```
> python
import torch
print(torch.__version__)
2.3.0+cu124
print(torch.cuda.is_available())
True
```

If cuda is not avaialble, refert to:
- run nvidia-smi to check driver and cuda versions. Reinstall proper vsersion of nvidia GPU driver if needed.
- run: pip uninstall torch torchvision
- reinstall: check https://pytorch.org/ to get torch install command, e.g.,
    pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cu124 --proxy http://proxy2:8081
    "--proxy" switch is optional, use it if you are behind a proxy.

## Download checkpoint
Download the finetuned checkpoint from https://drive.google.com/drive/folders/1H7vgiNVbxSeeleyJOqhoyRbJ97kGWGOK, and put it under checkpoints/.

``` bash
mkdir -p checkpoints/svd_reverse_motion_with_attnflip
cd checkpoints/svd_reverse_motion_with_attnflip
pip install gdown

export https_proxy=http://proxy2:8081 # optional
export http_proxy=http://proxy2:8081 # optional

gdown 1H7vgiNVbxSeeleyJOqhoyRbJ97kGWGOK --folder
```

## Run the code
```bash
bash keyframe_interpolation.sh
```
