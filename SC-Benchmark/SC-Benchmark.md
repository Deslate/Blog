# SC 小组 Benchmark 笔记

主要任务：测试双节点集群上的 HPL Benchmark 表现

## 安装

安装在了 `~/hpl-2.3`

```
~/hpl-2.3/bin/linux$ ls
HPL.dat  xhpl
```

## 基本知识

```
mpirun -n 4 ./xhpl
```

当求解问题规模为 N 时，浮点运算次数为（2/3 * N3－2*N2）。s因此，只要给出问题规模 N，测得系统计算时间 T，计算系统的浮点计算能力=计算量（2/3 * N3－2*N2）/计算时间 T，测试结果以浮点运算每秒（Flops）给出。

### HPL 调参 - 配置文件 `HPL.dat` 解读

```
HPLinpack benchmark input file
Innovative Computing Laboratory, University of Tennessee
HPL.out      output file name (if any)
6            device out (6=stdout,7=stderr,file)
4            # of problems sizes (N)
29 30 34 35  Ns
4            # of NBs
1 2 3 4      NBs
0            PMAP process mapping (0=Row-,1=Column-major)
3            # of process grids (P x Q)
2 1 4        Ps
2 4 1        Qs
16.0         threshold
3            # of panel fact
0 1 2        PFACTs (0=left, 1=Crout, 2=Right)
2            # of recursive stopping criterium
2 4          NBMINs (>= 1)
1            # of panels in recursion
2            NDIVs
3            # of recursive panel fact.
0 1 2        RFACTs (0=left, 1=Crout, 2=Right)
1            # of broadcast
0            BCASTs (0=1rg,1=1rM,2=2rg,3=2rM,4=Lng,5=LnM)
1            # of lookahead depth
0            DEPTHs (>=0)
2            SWAP (0=bin-exch,1=long,2=mix)
64           swapping threshold
0            L1 in (0=transposed,1=no-transposed) form
0            U  in (0=transposed,1=no-transposed) form
1            Equilibration (0=no,1=yes)
8            memory alignment in double (> 0)
```

#### 矩阵大小 N

```
4            # of problems sizes (N)
29 30 34 35  Ns
```

第五行第六行设置矩阵大小 `N`，第五行是要测试的矩阵的个数（ “`Ns`” 是 `N` 的复数 ）。第六行依次列出这几个矩阵的大小。为了找出系统的最佳性能，应致力于找出内存能接受的最大矩阵大小。

> 举个例子，我每节点有2G内存,4节点，N的算法为：N^2*64=1024*1024*1024*2*4*8，-〉N=32000~33000，再*0.8~0.9即可。按照经验，在0.9左右效果会更好。

以下几个参数也都是相通的格式，一行来声明要做几个测试，下一行列出每次测试要使用的参数值

#### 分块大小 NB

HPL使用块大小 `NB` 进行数据分发以及计算粒度，即分块的大小。

> 根据经验，对于GotoBLAS在AMD4000+上，用196，232，256效果比较好，当然其他也有一些说法

> 从数据分发的角度来看，NB越小，负载平衡越好。从计算的角度来看，NB的值太小可能会在很大程度上限制计算性能，因为在内存层次结构的最高级别中几乎没有数据重用。消息数量也会增加。高效的矩阵乘法例程通常在内部被阻塞。对于HPL，此阻塞因子的较小倍数可能是好的块大小。

#### 二维处理器网格 P 和 Q

这三行设置若干组二维处理器网格（P×Q）。二维处理器网格（P×Q）的要遵循以下几个要求：P×Q＝进程数。这是HPL的硬性规定；P×Q＝系统CPU数＝进程数。

```
3            # of process grids (P x Q)
2 1 4        Ps
2 4 1        Qs
```

## 测试记录

使用的节点有两个，

