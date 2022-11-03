# Parallel for
This class works as simply as possible. All you have to do is create it. 
After that, using the () operator, you can parallelize the task. 
The operator accepts start, end, number of threads and lambda function.  

The function works quite simply. Its work can be represented as a large queue and n cash registers. 
People from the queue will approach the checkout, be processed there, and then leave. 
At this time, the others are waiting for their turn.  

It is important that the function is not engaged in synchronization, i.e. 
if you change one element from different streams without using synchronization, you cannot