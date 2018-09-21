# GPU
NVIDIA GPU

## Prerequistes:

Please visit Docker tutorial - https://github.comcast.com/ebi-modeling/Docker


## Why GPU ?

  * Graphics Processing unit (GPU) makes a computer work and process large scale computations/deep learning algorithms much faster than a normal computer which we also call as accelerated computing. GPU processes the visuals as it's the graphics card primarily.
  
  * The GPU's capabilities were initally used for 3D games but now they are leveraged more broadly to accelerate computational workloads such as financial modeling, image recognition and other deep learning use cases.
  
  * Architecturally, the CPU is composed of just few cores with lots of cache memory that can handle a few software threads at a time. In contrast, a GPU is composed of hundreds of cores that can handle thousands of threads simultaneously. 
  
  * The ability of a GPU with 100+ cores to process thousands of threads can accelerate some software by 100x over a CPU alone. What’s more, the GPU achieves this acceleration while being more power- and cost-efficient than a CPU

* The reason for the wide and mainstream acceptance is that the GPU is a computational powerhouse, and its capabilities are growing faster than those of the x86 CPU

## NVIDIA GPU

   NVIDIA GDX Station delivers on average 100X faster deep learning training than a dual CPU server. The NVIDIA System Management Interface( nvidia-smi) is a command line utility to manage and monitor NVIDIA GPU devices.
    
   This nvidia-smi utility allows administrators to query GPU device state and with the appropriate privileges, permits administrators to modify GPU device state
   
   We have a total of 4 NVIDIA TESTLA GPU's in our DGX station
   
## How do I log into DGX station for using GPU's ?

   We can log in by the following ssh from terminal:
   
            ssh datascience@ebidgx1.cable.comcast.com
            
   It will prompt for password which most of us in the team know already, if not, reach out to Josh.


## Once logged in , here is how you can see a list of GPU's
   
             datascience@ebidgx1:~$ nvidia-smi --list-gpus
             GPU 0: Tesla V100-DGXS-16GB (UUID: GPU-5a3ba1c6-c310-d1bd-2e51-d4d619ae5a98)
             GPU 1: Tesla V100-DGXS-16GB (UUID: GPU-1c154e37-2b53-dc8b-36f2-24529c9c3de8)
             GPU 2: Tesla V100-DGXS-16GB (UUID: GPU-f494942d-b51e-b6dc-1d84-967fa8ed8bcb)
             GPU 3: Tesla V100-DGXS-16GB (UUID: GPU-caca592f-2a2c-963a-19aa-0e44beff4f6f)

 ## To live watch the utilization and RAM of the GPU's:
 
             datascience@ebidgx1:~$ watch -n 0.1 nvidia-smi
             
## Total disk space:
     
             datascience@ebidgx1:~$ df -h --total
             
## To view entire configuration of the GPU's
 
             datascience@ebidgx1:~$ nvidia-smi -q
             
## Please create a seperate folder for all your files,data,etc.. under the following path 

             datascience@ebidgx1:~/projects$ 
             
  This is to make sure our files are organized properly and so you can push your files to run on a docker container as described in the docker tutorial link at the top of this page.
      
  Please DONOT install any software/libraries/packages or run code on the gpu drive EXCEPT for pull or creating new docker images . Use ONLY launch docker container and transfer your files to run your processes. This is to ensure that we accumulate our mess on the drive.


## Performance of CPU vs GPU

 DGX Station brings the incredible performance of an AI supercomputer in a workstation form factor that takes advantage of innovative engineering and a water-cooled system that runs whisper-quiet.The NVIDIA DGX Station packs 500 teraFLOPS of performance, with the first and only workstation built on four NVIDIA Tesla V100 accelerators, including innovations like next generation NVLink™ and new Tensor Core architecture. This groundbreaking solution offers:
 
         * 72X the performance for deep learning training, compared with CPU-based servers
         * 100X in speed-up on large data set analysis, compared with a 20 node Spark server cluster
         * maximized versatility with deep learning training and over 30,000 images/second inferencing

## Our Case study using on performance LSTM for Malware Detection using the GPU

 In short, Long short-term memory (LSTM) network using keras was used to predict DGAs(domain generated algorithms). On local machine, it took ~4.27 hours compute time for one epoch:
 
         9119931/9119931 [==============================] - 15370s 2ms/step - loss: 0.0354
         
  wheras running using the docker container on the GPU reduced compute time to ~6 mins per epoch with ofcourse increasing the batch size to parallelize utilizing all the 4 GPU's.
  
         9119931/9119931 [==============================] - 357s 39us/step - loss: 0.0317
         
 For further details, please refer - https://github.comcast.com/ebi-modeling/LSTM-for-Malware-detection-using-GPU
