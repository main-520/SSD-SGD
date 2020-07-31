# SSD-SGD: Communication Sparsification for Distributed Deep Learning Training
Based on the observations that synchronous SGD obtains good convergence accuracy while asynchronous SGD has faster training speed, we present Several Steps Delay SGD (SSD-SGD), a generic algorithm for distributed training optimization via communication sparsification, to combine their merits inthe training process. Therefore, we can gain good convergence accuracy and fast training speed at the same time. The prototype of SSD-SGD is based on the popular deep learning framework [MXNet](https://github.com/apache/incubator-mxnet), and I just modify some source code files to adjust the execution sequences throughout the training process. Therefore, the file list is almost the same with [MXNet](https://github.com/apache/incubator-mxnet).

# Convergence Analysis
The pdf file (convergence-analysis.pdf) is provided to make convegence analysis of SSD-SGD algorithm. Due to the limited pages of the manuscript, we presnet the proof on this repository.

# Features
* SSD-SGD is applicable to both Parameter Server structure and Peer-to-Peer structure based deep learning frameworks.
* No modification is made to the process of parameter server, it conducts the update operation on receiving the gradients from workers, and sends back the updated parameters on receiving the Pull requests from the workers.
* The calculated gradients are sent to the servers every iteration, this is similar to the feature of Synchronous SGD; Each worker will conduct local update operations to get new local weights instead of waitting for the updated parameters from the servers, this is the feature of Asynchronous SGD. The gloabl parameters are pulled back from the servers every k iterations, where k is the delay steps.
* Users can specify the algorithm for local update through the option "--optimizer_local" when lancuhing the distributed training work. 


# Ask Questions
Please send emails to xuyemaovip@nudt.edu.cn for more details.
