# Au NCI vllm0.18.0 Enviornment Setup

The system of NCI is too old, and VLLM has not provide wheel for it. (Only avaliable is 0.11.0 and it not support for newest model)

Below is the most easy way, but it will take 3h

Launch a gpuhopper + Jobfs size: 200GB and run below code in terminal:

```bash
cd /scratch/xxx/xxx/

module purge
module load python3/3.12.1
module load cuda/12.8.0
module load gcc/12.2.0
export CC=$(which gcc)
export CXX=$(which g++)
export TORCH_CUDA_ARCH_LIST="9.0"

pip install uv
uv venv vllm_venv
source vllm_venv/bin/activate

uv pip install vllm==0.18.0
```

You can use the prebuild wheel file from [Releases](../../releases). (Chatgpt how to use it~)

Or follow the [nci_vllm0_18_0_setup.py](./nci_vllm0_18_0_setup.py) for a faster way by yourself.
