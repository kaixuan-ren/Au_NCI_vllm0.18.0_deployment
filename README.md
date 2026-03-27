# Au_NCI_vllm0.18.0_deployment

# Setup Code
Most easy way, but it will take 3h

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
