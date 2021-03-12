ARG DOCKER_NOTEBOOK_IMAGE
FROM $DOCKER_NOTEBOOK_IMAGE
ARG JUPYTERHUB_VERSION
RUN python3 -m pip install --no-cache jupyterhub==$JUPYTERHUB_VERSION

# https://github.com/takluyver/bash_kernel
RUN python3 -m pip install --no-cache bash_kernel && \
    python3 -m bash_kernel.install

# Other kernels to try out:
#     https://github.com/jupyter/jupyter/wiki/Jupyter-kernels

# https://github.com/NII-cloud-operation/sshkernel
RUN python3 -m pip install --no-cache sshkernel && \
    python3 -m sshkernel install --sys-prefix

# https://github.com/ansible/ansible-jupyter-kernel
RUN python3 -m pip install --no-cache ansible-kernel && \
    python3 -m ansible_kernel.install --sys-prefix
