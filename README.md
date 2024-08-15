# MLEnvBugs
Bugs and fixes when configuring ML environments

## Compile Error
1. When using pip install -e .
   
   Error: #error -- unsupported GNU version! gcc versions later than 13 are not supported! The nvcc flag '-allow-unsupported-compiler' can be used to override this version check; however, using an unsupported host compiler may cause compilation failure or incorrect run time execution. Use at your own risk.

   Solution1: check the system gcc version using `gcc --version` and downgrade it if needed, also remember to check the gcc installed using conda using `conda list | grep gcc`

   Solution2 (from https://blog.csdn.net/mirrorboat/article/details/139418016)
   ```
   conda install -c conda-forge gcc=10 binutils=2.36.1
   conda install gcc_linux-64 gxx_linux-64
   ```

## Dependency Issue
1. When installing `transformers[dev]` using Python 3.11

   Error:
   ```
   Collecting av==9.2.0 (from transformers==4.44.0.dev0)
   Using cached av-9.2.0.tar.gz (2.4 MB)
   Installing build dependencies ... done
   Getting requirements to build wheel ... error
   ```

   Solution: av 9.2.0 doesn't support Python 3.11, so you'll need to downgrade it or modify `setup.py`.

2. Deepspeed: File "/opt/conda/envs/infercept/lib/python3.11/site-packages/deepspeed/elasticity/elastic_agent.py", line 9, in <module>
    from torch.distributed.elastic.agent.server.api import log, _get_socket_with_port
ImportError: cannot import name 'log' from 'torch.distributed.elastic.agent.server.api'

   Solution: Simply update deepspeed will work.

## Matplotlib Error
1. When using plot in Jupyter Notebook

   Error: ValueError: object __array__ method not producing an array

   Solution: Upgrade matplotlib version
