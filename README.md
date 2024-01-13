# README
## txjg

- 软件依赖
  Intel Compiler（代码在 Intel CPU 上进行了优化）
  OpenMP（安装英特尔编译器后，无需单独安装）
  MKL（16.0.0 或更高版本）
  MPI 库，支持多线程（仅限分布式 word2vec 的 Intel MPI、MPICH2 或 MVAPICH2）
  HyperWords（用于模型精度评估）
  Numactl 封装（用于多插槽 NUMA 系统）

- 环境配置
  安装Intel C++开发环境(Intel Compiler, OpenMP, MKL, iMPI)
  启动Intel C++开发环境
  ```
  source /opt/intel/compilers_and_libraries/linux/bin/compilervars.sh intel64 (注意使用自己的安装路径)
  source /opt/intel/impi/latest/compilers_and_libraries/linux/bin/compilervars.sh intel64 (注意使用自己的安装路径)
  ```
- 安装numactl软件包
  ```
  sudo apt-get install numactl
  ```
- 运行
  下载代码：`git clone https://github.com/IntelLabs/pWord2Vec`
  
  运行 `.\install.sh` 来构建包 此安装尝试生成两个二进制文件：pWord2Vec 和 pWord2Vec_mpi。若不设置 mpi，编译当然会在构建pWord2Vec_mpi时失败。非 mpi 二进制文件仍可用
  
  下载数据：`cd data; .\getText8.sh or .\getBillion.sh`
  
  运行演示脚本：`cd sandbox; ./run_single_text8.sh (for single machine demo) or ./run_mpi_text8.sh (for distributed w2v demo)`
  
  在 1 亿字基准上运行代码：`cd billion; ./run_single.sh (for single machine w2v) or ./run_mpi.sh (for distributed w2v) (please set ncores=number of logical cores of your machine)`
  
  评估模型：`cd sandbox; ./eval.sh or cd billion; ./eval.sh`
