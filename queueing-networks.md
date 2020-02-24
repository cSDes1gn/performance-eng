# Queuing Networks and Performance Modeling

## Service Centers
---
Service Centers consist of a Queue and a Server with arriving and departing customers. Service centers have the following performance measures:

> **S**: service time is the time spent to serve a request <br>
> **$\lambda$**: arrival rate (frequency) which customers arrive at the *server* <br>
> **X**: throughput rate (frequency) at which customers pass through the full service center.<br>
> **U**: utilization is the proportion of time the server is busy <br>
> **R**: residence time (system response time) is the average time spent in the entire service center by a customer. This is done by adding the queueing time by the service time <br>
> **Q**: queue length is the average number of customers at the *service center* not just in the queue.

> ### Kendal's Notation *A/S/c/m/N*
> ---
> Kendal's notation describes the characteristics of a queueing network by the following 5 parameters:
>> **A**: arrival process and, <br>
>> **S**: service rate defined some common distributions:
>> 1. M-Markov distribution
>> 2. G-General distribution
>> 3. D-Deterministic distribution
>> 
>> **c**: number of servers available to serve customers from the queue.<br>
>> **m**: capacity of the queue ($\infty$ by default) <br>
>> **M**: total customer population size (($\infty$ by default)) <br>
>
> Finally the scheduling policy can be specified but is not included in the notation scheme.

### M/M/1 Single Service Center
---
This defines a markov distributed arrival and service process with a single server for processing the queue.

#### Saturation of M/M/1 system
- server reaches saturation at an arrival rate ($\lambda_s$) which causes the utilization to reach 100%.
- at a low workload (when the queue is small) an arriving customer meets low competition so *R* $\approx$ *S*.
- as workload raises the congestion in the queue rises exponentially causing *Q* and *R* to increase exponentially with $\lambda$
- *Q* and *R* asymptote at $\lambda_s$ and so are not defined in saturated service centers.

Some types of service center architectures:
> **Delay server (Infinite Server)**
> - Example is terminals in a closed system
> - Server available for any job
> - Queue cannot be made since all jobs can find a server which operate in parallel
> - Time spent by a job at the infinite server is always *S*'

> **Multi-Server**
> - a single queue but more than one server
> - if there are more jobs in the queue than servers, the jobs are queued.

## Network of Queues
---
**Open QN models** are models where jobs arrive with a certain rate $\lambda$, spend time in the system being served then leave the system when complete.

**Closed QN models** have a fixed number of jobs *N* and after completing a service cycle a job starts again.
>In a closed system there is an additional performance parameter *Z* (think time) which describes the time spent by a job outside the system, after completing a response and before it starts a new request.

### Bottleneck Service Center