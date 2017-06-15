Singularity Container with Tensorflow and Jupyter Notebook
===

- Intent is to run Tensorflow on GPU compute nodes through JupyterHub
    - If you would like this built for another driver, submit an issue
- Borrowed `links.sh` from https://github.com/drorlab/tf-singularity
- I extracted CuDNN here because the download link expires
- Building the image
```
$ sudo singularity create -s 3072 tensorflow-jupyterhub.img
$ sudo singularity bootstrap tensorflow-jupyterhub.img Singularity
```
- Running jupyter
```
$ singularity run tensorflow-jupyterhub.img
[I 21:58:36.327 NotebookApp] Serving notebooks from local directory: <some directory>
[I 21:58:36.327 NotebookApp] 0 active kernels 
[I 21:58:36.327 NotebookApp] The Jupyter Notebook is running at: http://localhost:8888/?token=<some token>
[I 21:58:36.327 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 21:58:36.329 NotebookApp] 
    
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=<some token>
```
- If you want to just run a script:
```
$ singularity exec tensorflow-jupyterhub.img python hello-world.py
```
- Me and @mcburton are working on JupyterHub plugins to handle Singularity Hub
  images cleanly.

To Do
---

1. Possibly indicate any bloat in the image and clear it out, if possible
    - Tensorflow DockerHub Compressed Image with GPU is 2 GB, mine is 3 GB
2. Working on JupyterHub plugin to deploy images from Singularity Hub
