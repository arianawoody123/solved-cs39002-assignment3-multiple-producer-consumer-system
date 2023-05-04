Download Link: https://assignmentchef.com/product/solved-cs39002-assignment3-multiple-producer-consumer-system
<br>
Implement a producer / consumer system using shared memory, with the following specifications:

<ol>

 <li>Your program will first read the values of NP (number of producers) and NC (number of consumers), and create the required number of producer and consumer processes. It will also take the number of total jobs to run as an input.</li>

 <li>Create a shared memory segment SHM, which is shared among all the producer and consumer processes spawned by your code. The shared memory segment will contain a priority queue of finite size (say, can hold 8 elements). It will also create a <em>job_created</em> counter (integer) and a <em>job_completed</em> counter (integer) in the shared memory.</li>

 <li>Each producer process should generate a computing job, waits for a</li>

</ol>

random interval of time between 0 and 3 seconds, and inserts the computing job in shared memory queue. After insertion, the producer will repeat the process. Each computing job is represented by a structure which contains the following elements at a minimum:

<ol>

 <li>process id for the producer</li>

 <li>producer number</li>

</ol>

<ul>

 <li>priority of the process iv. compute time</li>

</ul>

<ol>

 <li>job id.</li>

</ol>

The priority of the process is a number between 1 and 10 and for each job, job id is a random integer between 1 and 100000, compute time is an integer between 1 and 4. The producer generates each of these three numbers randomly while creating a job.

<ol>

 <li>While insertion, if the queue is full, the producer waits until space becomes available. It will also print the producer number, pid and details of the job generated (e.g. producer: 3, producer pid: 37, priority: ***, compute time: ***). Then the producer will increase the <em>job_created</em> counter by 1.</li>

 <li>Each consumer process waits for a random interval of time between 0 and 3 seconds, retrieves the job with highest priority in the shared memory priority queue, removed the job and prints the job details on the screen mentioning the consumer number, consumer pid, producer number, producer pid, priority, and compute time (e.g. consumer: 2, consumer pid: 53, producer: 3, producer pid: 37, priority: ***, compute time: ***). Then the consumer will increase the job_completed counter and will sleep for “compute time” seconds. If the priority queue is empty the consumer process will wait till a job is inserted in the buffer.</li>

 <li>The parent process (i.e., your code) will wait till both <em>job_created</em> counter and <em>job_completed</em> counter reaches a specified number of jobs (e.g., 10), output the time taken to run those specified number of jobs and then kill the process.</li>

 <li>[BONUS]: use mutex locks to prevent concurrent updation to shared variables leading to possible race conditions.</li>

</ol>