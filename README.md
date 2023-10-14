# STA_ring_buffer
Small improvement of STA (Several Threads Arch) architecture (Matrix operations extention)

There is a small improvement of a Matrix multiplication that can be done.

First of all, we can multiply two integers, integer to vector, vector to vectors and vectors to vectors.

If we make our NPU/TPU with a ring buffer and store rows/columns of a second matrix, we can get an improvement of speed (no need to wait for data for columns, we can launch a data stream with almost zero latency).
Also, we can add a simple cache to the ring buffer (to store some constants or so). And Have a circular buffer and a cache inside of every computing/grid cell.

Also, we can simply remove FIFO's (to save more power) and leave only folloving blocks (compared to BISMO pipeline): 
![image](https://github.com/ValeriyAndreevichPushkarev/STA_ring_buffer/assets/130975795/d16ea9e3-6ddb-4dfc-ad8e-8171d911befb)


Also, we can make several such blocks
(Note that we can spend more energy to store the results than to perform multiplications/additions)

Also, there are many solutions where execution graphs (and probably some sorts of caching) can be resolved during model "compilation" (cerebras WSE).
Checking for data presence in cache can consume a lot too (and there are no "ring buffers" in common types of accelerators).
