# MLEnvBugs
Bugs and fixes when configuring ML environments

## Compile error
1. When using pip install -e .
   
   Error: #error -- unsupported GNU version! gcc versions later than 13 are not supported! The nvcc flag '-allow-unsupported-compiler' can be used to override this version check; however, using an unsupported host compiler may cause compilation failure or incorrect run time execution. Use at your own risk.

   Solution: check the system gcc version using `gcc --version` and downgrade it if needed, also remember to check the gcc installed using conda using `conda list | grep gcc`
