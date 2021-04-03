ARG DOCKER_NOTEBOOK_IMAGE
FROM $DOCKER_NOTEBOOK_IMAGE
ARG JUPYTERHUB_VERSION
ENV JUPYTER_ENABLE_LAB=1
USER root
RUN apt-get update && apt-get install -y \
  fd-find \
  fish \
  openssh-client \
  ripgrep

USER jovyan

RUN python3 -m pip install --no-cache jupyterhub==$JUPYTERHUB_VERSION

RUN pip install --upgrade --pre jupyterlab-git
RUN jupyter labextension install @jupyterlab/git

# https://github.com/takluyver/bash_kernel
RUN python3 -m pip install --no-cache bash_kernel && \
    python3 -m bash_kernel.install --sys-prefix

# https://github.com/NII-cloud-operation/sshkernel
RUN python3 -m pip install --no-cache sshkernel && \
    python3 -m sshkernel install --sys-prefix

# Other kernels to try out:
#     https://github.com/jupyter/jupyter/wiki/Jupyter-kernels

# https://github.com/ansible/ansible-jupyter-kernel
#RUN python3 -m pip install --no-cache ansible-kernel && \
#   python3 -m ansible_kernel.install --sys-prefix

#RUN jupyter lab build
