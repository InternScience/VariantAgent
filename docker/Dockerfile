FROM interndiscoveryscp/scp-code:v2

LABEL maintainer="canton-env" \
      description="Canton GWAS environment based on scp-code:v2"

# 切换到 root 用户以执行安装操作
USER root

# 配置 apt 使用清华镜像源（兼容 Debian 12 的 DEB822 格式和旧版 sources.list）
# 并安装必要工具及 kaleido/Chromium 所需系统依赖
RUN sed -i 's|http://deb.debian.org|https://mirrors.tuna.tsinghua.edu.cn|g' \
        /etc/apt/sources.list 2>/dev/null || true && \
    sed -i 's|http://deb.debian.org|https://mirrors.tuna.tsinghua.edu.cn|g' \
        /etc/apt/sources.list.d/debian.sources 2>/dev/null || true && \
    apt-get update && apt-get install -y --no-install-recommends \
    bzip2 \
    ca-certificates \
    chromium \
    libnss3 \
    libgbm1 \
    libasound2 \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libcups2 \
    libdrm2 \
    libxkbcommon0 \
    libxcomposite1 \
    libxdamage1 \
    libxrandr2 \
    && rm -rf /var/lib/apt/lists/*

# 安装 Miniforge（内置 mamba，基于 conda-forge，无需接受 Anaconda TOS）
ENV CONDA_DIR=/opt/conda
RUN wget -q https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh \
        -O /tmp/miniforge.sh && \
    bash /tmp/miniforge.sh -b -p ${CONDA_DIR} && \
    rm /tmp/miniforge.sh && \
    ${CONDA_DIR}/bin/conda clean -afy

# 将 conda/mamba 加入 PATH
ENV PATH="${CONDA_DIR}/bin:${PATH}"

# HuggingFace 镜像（容器内访问 huggingface.co 不可达时使用）
ENV HF_ENDPOINT=https://hf-mirror.com

# 配置 conda 使用清华镜像源，增大超时和重试次数
RUN conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/ && \
    conda config --set show_channel_urls yes && \
    conda config --set remote_connect_timeout_secs 60 && \
    conda config --set remote_read_timeout_secs 300 && \
    conda config --set remote_max_retries 10

# 第一步：用 mamba 安装所有 conda 包（不含 pip 部分）
COPY config/canton_environment_conda_only.yml /tmp/canton_environment_conda_only.yml
RUN mamba env create --yes -f /tmp/canton_environment_conda_only.yml && \
    conda clean -afy && \
    rm -f /tmp/canton_environment_conda_only.yml

# 第二步：用 pip 安装剩余 pip 包，锁定版本，--no-deps 跳过依赖冲突检查
COPY config/canton_pip_requirements.txt /tmp/canton_pip_requirements.txt
RUN /opt/conda/envs/canton/bin/pip install \
    --no-deps \
    --index-url https://pypi.tuna.tsinghua.edu.cn/simple \
    --extra-index-url https://download.pytorch.org/whl/cpu \
    -r /tmp/canton_pip_requirements.txt && \
    rm -f /tmp/canton_pip_requirements.txt

# 第三步：安装 canton R 包（CRAN + GitHub）
# 使用 conda run 而非直接调用 Rscript，确保 conda 编译器环境变量（CC/CXX 等）完整激活
# 否则含 C++ 代码的包（如 SeuratObject）编译时会报 x86_64-conda-linux-gnu-c++: not found
ARG GITHUB_PAT=""
COPY config/canton_r_packages.R /tmp/canton_r_packages.R
RUN conda run --no-capture-output -n canton \
    bash -c "GITHUB_PAT=${GITHUB_PAT} Rscript /tmp/canton_r_packages.R && rm -f /tmp/canton_r_packages.R"

# ── biopathnet 环境 ──────────────────────────────────────────────────────────
COPY config/biopathnet_environment_conda_only.yml /tmp/biopathnet_environment_conda_only.yml
RUN mamba env create --yes -f /tmp/biopathnet_environment_conda_only.yml && \
    conda clean -afy && \
    rm -f /tmp/biopathnet_environment_conda_only.yml
COPY config/biopathnet_pip_requirements.txt /tmp/biopathnet_pip_requirements.txt
# 第1步：先安装 setuptools/wheel（提供 pkg_resources）和 torch 本体
RUN /opt/conda/envs/biopathnet/bin/pip install \
    --index-url https://pypi.tuna.tsinghua.edu.cn/simple \
    --extra-index-url https://download.pytorch.org/whl/cpu \
    "setuptools==80.9.0" \
    "torch==2.0.1+cpu" "torchaudio==2.0.2+cpu" "torchvision==0.15.2+cpu"
# 第2步：用 --no-build-isolation 安装 torch-cluster 等（构建时直接使用已有 torch）
RUN /opt/conda/envs/biopathnet/bin/pip install \
    --no-build-isolation \
    --index-url https://pypi.tuna.tsinghua.edu.cn/simple \
    "torch-cluster==1.6.3" "torch-scatter==2.1.2" \
    "torch-sparse==0.6.18" "torch-spline-conv==1.2.2"
# 第2步：安装其余所有 pip 包（--no-deps 锁定版本）
RUN /opt/conda/envs/biopathnet/bin/pip install \
    --no-deps \
    -r /tmp/biopathnet_pip_requirements.txt && \
    rm -f /tmp/biopathnet_pip_requirements.txt

# ── clean 环境 ───────────────────────────────────────────────────────────────
COPY config/clean_environment_conda_only.yml /tmp/clean_environment_conda_only.yml
RUN mamba env create --yes -f /tmp/clean_environment_conda_only.yml && \
    conda clean -afy && \
    rm -f /tmp/clean_environment_conda_only.yml
COPY config/clean_pip_requirements.txt /tmp/clean_pip_requirements.txt
RUN /opt/conda/envs/clean/bin/pip install \
    --no-deps \
    -r /tmp/clean_pip_requirements.txt && \
    rm -f /tmp/clean_pip_requirements.txt

# 安装 CLEAN enzyme function predictor Python 包
# build.py 等效于 setup.py（包在 src/CLEAN/），重命名后用 pip 安装
COPY CLEAN/app/build.py /tmp/clean_pkg/setup.py
COPY CLEAN/app/src /tmp/clean_pkg/src
RUN /opt/conda/envs/clean/bin/pip install /tmp/clean_pkg && \
    rm -rf /tmp/clean_pkg

# ── enrich 环境 ──────────────────────────────────────────────────────────────
COPY config/enrich_environment_conda_only.yml /tmp/enrich_environment_conda_only.yml
RUN mamba env create --yes -f /tmp/enrich_environment_conda_only.yml && \
    conda clean -afy && \
    rm -f /tmp/enrich_environment_conda_only.yml
COPY config/enrich_pip_requirements.txt /tmp/enrich_pip_requirements.txt
RUN /opt/conda/envs/enrich/bin/pip install \
    --no-deps \
    -r /tmp/enrich_pip_requirements.txt && \
    rm -f /tmp/enrich_pip_requirements.txt

# ── gsmap_env 环境 ───────────────────────────────────────────────────────────
COPY config/gsmap_env_environment_conda_only.yml /tmp/gsmap_env_environment_conda_only.yml
RUN mamba env create --yes -f /tmp/gsmap_env_environment_conda_only.yml && \
    conda clean -afy && \
    rm -f /tmp/gsmap_env_environment_conda_only.yml
COPY config/gsmap_env_pip_requirements.txt /tmp/gsmap_env_pip_requirements.txt
RUN /opt/conda/envs/gsmap_env/bin/pip install \
    --no-deps \
    -r /tmp/gsmap_env_pip_requirements.txt && \
    rm -f /tmp/gsmap_env_pip_requirements.txt

# ── vep115 环境（含 bioconda 通道）──────────────────────────────────────────
COPY config/vep115_environment.yml /tmp/vep115_environment.yml
RUN mamba env create --yes -f /tmp/vep115_environment.yml && \
    conda clean -afy && \
    rm -f /tmp/vep115_environment.yml

# 初始化 conda，使进入容器后可直接使用 conda activate <env>
RUN conda init bash && \
    echo "source /opt/conda/etc/profile.d/conda.sh" >> /root/.bashrc

# 各环境使用方式：
#   docker exec -it <容器名> bash
#   conda activate canton / biopathnet / clean / enrich / gsmap_env / vep115

# 保持容器运行
CMD ["tail", "-f", "/dev/null"]