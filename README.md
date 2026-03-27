# Au_NCI_vllm0.18.0_deployment

# Enviornment location 
# or cd /g/xxx/xxx/ or home
cd /scratch/xxx/xxx/   

module purge
module load python3/3.12.1
module load cuda/12.8.0
module load gcc/12.2.0
export CC=$(which gcc)
export CXX=$(which g++)
export TORCH_CUDA_ARCH_LIST="9.0"

# set up cache 
export MY_CACHE_DIR="$PBS_JOBFS/cache"
mkdir -p $MY_CACHE_DIR
export TMPDIR=$PBS_JOBFS
export PIP_CACHE_DIR="$MY_CACHE_DIR/pip"
export UV_CACHE_DIR="$MY_CACHE_DIR/uv"
export HF_HOME="$MY_CACHE_DIR/huggingface"
export TORCH_EXTENSIONS_DIR="$MY_CACHE_DIR/torch_extensions"
export CUDA_CACHE_PATH="$MY_CACHE_DIR/nv_compute_cache"
export CMAKE_BUILD_CACHE="$MY_CACHE_DIR/cmake"
export MAX_JOBS=90

# Setup Enviornment
pip install uv
uv venv vllm_venv
source vllm_venv/bin/activate

uv pip install vllm==0.18.0
