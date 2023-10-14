# STA_ring_buffer
Small improvement of STA (Several Threads Arch) architecture (Matrix operations extention)

There is a small improvement of a Matrix multiplication can be done.

First of all, we can multiply two integers, integer to vector, vector to vectors and vectors to vectors.

If we will make our NPU/TPU with a ring buffer and will store rows/columns of a second matrix, we can get a improvement of speed (no need to wait data for columns, we can launch a data stream with almost zero latency).

Also, we can simply remove FIFO's (to save more power) and leave only folloving blocks (compared to BISMO pipeline): 
![image](https://github.com/ValeriyAndreevichPushkarev/STA_ring_buffer/assets/130975795/415b8162-8d79-47ab-bc87-123a81eaab4e)

Also, we can make several such blocks
(Note that we can spend more energy to store the results than to preform multiplications/additions)
