# RAJA Matrix Research

## Description
This is a research project for a Parallel and Distributed Systems course at James Madison University. The goal of this project was to find out the portability and applicability for the RAJA library. The RAJA library was tested against other parallelization libraries to see if it is a viable option. This was done with multiple algorithms, but the algorithm in this repository deals with matrix math including operations like guassian elimination and back substitution. The results for the testing can be found at this link: https://docs.google.com/spreadsheets/d/1XBDZMCorhAVTOxd4CGxJo1NEtBsGFzoL2hqxUYz1-LU/edit#gid=0 . 

## Languages and Utilities Used
- **C++**
- **RAJA**
- **CUDA**
- **OpenMP**
- **Pthreads**

## Environments Used
- **macOS**
- **JMU Cluster**
- **AMD**
- **ARM**

## How to Use
To install raja and setup the directory, you will run setup.sh or setup_noncluster.sh depending if you are on the cluster or not. This will clone the raja repository and get the correct folders in order. Run.sh is still included in the repository, but it was not really used in the later testing. There are other scripts that are more relevant that are written about below.

To run these programs, you have several different options. First, you can cd into /example and use the makefile to make each of the programs. You will have to use make all in order to make the cuda program. This was designed this way because some of the places we ran these programs did not have cuda.

Running timing.sh will run each implementation on various sizes with different amounts of threads (when applicable). This will usually take over an hour on the cluster mostly because of the cuda implementation. However, there is also a timing_noncluster.sh that does the exact same thing except does not run the cuda implementation. Also, we have scripts for each of the implementations to get the results individually that do not take nearly as long as timing.sh. These are called serialtiming.sh, openmptiming.sh, rajatiming.sh, etc. 

In addition to producing these timing results, there are also scripts for testing correctness. The scripts called correct.sh and correct_.sh will test each implementation over a 3x3 and 4x4 matrix so that we could make sure we maintained accuracy while trying to optimize speed. There are also noncluster versions for these scripts.

When running the cluster versions, you have to specify --gres=gpu when running the script (sbatch --gres=gpu ./correct.sh) so that the cuda version can run. You only have to do this when a script will attempt to run a cuda version.

EXAMPLES:
sbatch --gres=gpu ./timing.sh
sbatch ./timing_noncluster.sh
sbatch --gres=gpu ./correct.sh
sbatch --gres=gpu ./correct_.sh
sbatch ./openmptiming.sh
sbatch --gres=gpu ./cudatiming.sh


## Contributing
Contributions to this project are welcome! Please fork the repository and submit a pull request with your improvements.
