# System Updates

## 2019-10-04

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Update | Univa Grid Engine | 8.6.6 | 8.6.3 |
| Update | DDN GRIDScaler | 4.2.3.17 | 4.2.3.15 |
| Update | BeeOND | 7.1.3 | 7.1.2 |
| Add | CUDA | 10.1.243 | |
| Add | cuDNN | 7.6.3, 7.6.4 | |
| Add | NCCL | 2.4.8-1 | |
| Add | MVAPICH2-GDR | 2.3.2 | |
| Add | MVAPICH2 | 2.3.2 | |
| Add | fuse-sshfs | 2.10 | |

Other fixes are as follows:

* Add CUDA 10.1 support to cuDNN 7.5.0, 7.5.1, 7.6.0, 7.6.1, 7.6.2
* Add CUDA 10.1 support to NCCL 2.4.2-1, 2.4.7-1
* Add CUDA 10.0 and 10.1 support to GDRCopy 1.2
* Add CUDA 10.1 support to Open MPI 2.1.6
* Add process monitoring and process cancellation mechanism on the interactive node

### Start process monitoring on the interactive nodes

Process monitoring started on the interactive nodes.
High load or lengthy tasks on the interactive nodes will be killed by the
process monitoring system, so use the compute nodes with the `qrsh/qsub` 
command.

### Change the job submission and execution limits

We changed the job submission and execution limits as follows.

| Limitations                                                     | Current limits | Previous limits |
| :--                                                             | :--            | :--             |
| The maximum number of tasks within an array job                 | 75000          | 1000            |
| The maximum number of any user's running jobs at the same time  | 200            | 0(unlimited)    |

### About known issues

The status of following known issues were changed to close.

* A comupte node can execute only up to 2 jobs each resource type "rt_G.small"
  and "rt_C.small" (normally up to 4 jobs ).

## 2019-08-01

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Add | cuDNN | 7.6.2 | |
| Add | NCCL | 2.4.7-1 | |
| Add | s3fs-fuse | 1.85 | |

Other fixes are as follows:

* Add CUDA 10.0 support to Open MPI 1.10.7, 2.1.5, 2.1.6

## 2019-07-10

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Add | CUDA | 10.0.130.1 | |
| Add | cuDNN | 7.5.1, 7.6.0, 7.6.1 | |
| Add | aws-cli | 1.16.194 | |

## 2019-04-05

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Update | CentOS | 7.5 | 7.4 |
| Update | Univa Grid Engine | 8.6.3 | 8.5.4 |
| Update | Java | 1.7.0\_171 | 1.7.0\_141|
| Update | Java | 1.8.0\_161 | 1.8.0\_131|
| Add | DDN Lustre | 2.10.5\_ddn7-1 | |
| Add | CUDA | 10.0.130 | |
| Add | Intel Compiler | 2019.3 | |
| Add | PGI | 18.10, 19.3 | |

Other fixes are as follows:

* Migrate HOME area from GPFS to DDN Lustre

## 2019-03-14

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Add | Intel Compiler | 2017.8, 2018.3 | |
| Add | PGI | 17.10 | |
| Add | Open MPI | 2.1.6 | |
| Add | cuDNN | 7.5.0 | |
| Add | NCCL | 2.4.2-1 | |
| Add | Intel MKL | 2017.8, 2018.3 | |

Other fixes are as follows:

* Add PGI 17.10 support to MVAPICH2-GDR 2.3
* Add PGI support to Open MPI 2.1.5, 2.1.6, 3.1.3
* Change the default version of Open MPI to 2.1.6
* Fix typo in MVAPICH2 modules, wrong top directory

## 2019-01-31

### User/Group/Job names are now masked when displaying the result of 'qstat'

We changed the job scheduler configuration, so that User/Group/Job names are masked from the result of `qstat` command. These columns are shown only for your own jobs, otherwise these columns are masked by '*'. An example follows:

```
[username@es1 ~]$ qstat -u '*' | head
job-ID     prior   name       user         state submit/start at     queue                          jclass                         slots ja-task-ID
------------------------------------------------------------------------------------------------------------------------------------------------
    123456 0.28027 run.sh     username     r     01/31/2019 12:34:56 gpu@g0001                                                        80
    123457 0.28027 ********** **********   r     01/31/2019 12:34:56 gpu@g0002                                                        80
    123458 0.28027 ********** **********   r     01/31/2019 12:34:56 gpu@g0003                                                        80
    123450 0.28027 ********** **********   r     01/31/2019 12:34:56 gpu@g0004                                                        80
```

## 2018-12-18

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Add | NCCL | 2.3.7-1 | |
| Add | cuDNN | 7.4.2 | |
| Add | Open MPI | 3.0.3, 3.1.3 | |
| Add | MVAPICH2-GDR | 2.3 | |
| Add | Hadoop | 2.9.2 | |
| Add | Spark | 2.3.2, 2.4.0 | |
| Add | Go | 1.11.2 | |
| Add | Intel MKL | 2018.2.199 | |

### NCCL 2.3.7-1

The NVIDIA Collective Communications Library (NCCL) 2.3.7-1 was installed.

The relase note will be found: [NCCL Release 2.3.7](https://docs.nvidia.com/deeplearning/sdk/nccl-release-notes/index.html)

To set up user environment:

```
$ module load cuda/9.2/9.2.148.1
$ module load nccl/2.3/2.3.7-1
```

### cuDNN 7.4.2

The NVIDIA CUDA Deep Neural Network library (cuDNN) 7.4.2 was installed.

The release note will found: [cuDNN Release Notes v7.4.2](https://docs.nvidia.com/deeplearning/sdk/cudnn-release-notes/rel_742.html)

To set up user environment:

```
$ module load cuda/9.2/9.2.148.1
$ module load cudnn/7.4/7.4.2
```

### Open MPI 3.0.3, 3.1.3

Open MPI (without --cuda option) 3.0.3, 3.1.3 were installed.

To set up user environment:

```
$ module load openmpi/3.1.3
```

### MVAPICH2-GDR 2.3

MVAPICH2-GDR 2.3 was installed.

To set up user environment:

```
$ module load cuda/9.2/9.2.148.1
$ module load mvapich/mvapich2-gdr/2.3
```

### Hadoop 2.9.2

Apache Hadoop 2.9.2 was installed.

To set up user environment:

```
$ module load openjdk/1.8.0.131
$ module load hadoop/2.9.1
```

### Spark 2.3.2, 2.4.0

Apache Spark 2.3.2, 2.4.0 were installed.

To set up user environment:

```
$ module load spark/2.4.0
```

### Go 1.11.2

Go Programming Language 1.11.2 was installed.

To set up user environment:

```
$ module load go/1.11.2
```

### Intel MKL 2018.2.199

Intel Math Kernel Library (MKL) 2018.2.199 was installed.

To set up user environment:

```
$ module load intel-mkl/2018.2.199
```

## 2018-12-14

| Add / Update / Delete | Software | Version | Previous version |
|:--|:--|:--|:--|
| Update | Singularity | 2.6.1 | 2.6.0 |
| Delete | Singularity | 2.5.2 | |

Singularity 2.6.1 was installed. The usage is as follows:

```
$ module load singularity/2.6.1
$ singularity run image_path
```

The release note will be found:

[Singularity 2.6.1](https://github.com/sylabs/singularity/releases/tag/2.6.1)

And, we uninstalled version 2.5.2 and 2.6.0 because severe security issues ([CVE-2018-19295](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2018-19295)) were reported. If you are using Singularity with specifying version number, such as `singularity/2.5.0` or `singularity/2.6.0`, please modify your job scripts to specify `singularity/2.6.1`.

```
ex) module load singularity/2.5.2 -> module load singularity/2.6.1
```
