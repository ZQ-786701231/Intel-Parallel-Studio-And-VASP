# Intel-Parallel-Studio-And-VASP
How To Install Intel Parallel Studio 2019 And VASP
# 在以下网站申请学生版，该版本免费，需edu邮箱
```
https://software.intel.com/en-us/qualify-for-free-software/student

tar –xzf parallel_studio_xe_2019_update×.tgz

cd parallel_studio_xe_2019_update×

./install.sh
```
# 设置环境变量
```
gedit ~/.bashrc

把下面这行加入其中末尾，用来自动配置Intel Parallel Studio XE的运行环境：

source /opt/intel/parallel_studio_xe_2019/psxevars.sh

source ~/.bashrc使之生效
```
# 然后进入/opt/intel/compilers_and_libraries_2019.x.xxx/linux/mkl/interfaces/fftw3xf
```
运行make libintel64
```
过一会儿当前目录下会产生libfftw3xf_intel.a库文件
重新进入终端，运行ifort -V，如果显示出了编译器的版本，说明编译器已经可以正常使用了

# 解压vasp,进入该目录
把arch/makefile.include.linux_intel拷到上一级目录下改名为makefile.include

打开此文件，把其中的OFLAG参数里加入-xhost

在OBJECTS参数里改成libfftw3xf_intel.a的路径

之后运行make all

编译完成后，在vasp.5.4.4/bin目录下出现了vasp_gam、vasp_ncl、vasp_std三个可执行文件

vasp_std改名为vasp
# 添加可执行文件的路径
```
gedit ~/.bashrc
```
在~/.bashrc末尾加入以下这行

export PATH=$PATH:/root/vasp.5.4.x/bin

之后重新进入终端，VASP就可以用了



