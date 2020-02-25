# Queuing Networks and Performance Modeling

## Service Centers
Service Centers consist of a Queue and a Server with arriving and departing customers. Service centers have the following performance measures:

> **S**: service time is the time spent to serve a request <br>
> **λ**: arrival rate (frequency) which customers arrive at the *server* <br>
> **X**: throughput rate (frequency) at which customers pass through the full service center.<br>
> **U**: utilization is the proportion of time the server is busy <br>
> **R**: residence time (system response time) is the average time spent in the entire service center by a customer. This is done by adding the queueing time by the service time <br>
> **Q**: queue length is the average number of customers at the *service center* not just in the queue.

> ### Kendal's Notation *A/S/c/m/N*
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
This defines a markov distributed arrival and service process with a single server for processing the queue.

#### Saturation of M/M/1 system
- server reaches saturation at an arrival rate (λs) which causes the utilization to reach 100%.
- at a low workload (when the queue is small) an arriving customer meets low competition so *R* $\approx$ *S*.
- as workload raises the congestion in the queue rises exponentially causing *Q* and *R* to increase exponentially with λ
- *Q* and *R* asymptote at λ and so are not defined in saturated service centers.
  
#### Exact M/M/1 Solutions:
Additional notation:
> **µ**: rate of exponentially distributed service time.<br>
> **1/µ**: service time. <br>
> **λ**: rate of arrival Poisson process.<br>
> **ρ = λ/µ**: server utilization. Only stable when λ < µ<br>

Some steady state formulas:

> `N = ρ / (1 - ρ)` describes the mean jobs in system:<br>
> `N = ρ^2 / (1 - ρ)` describes mean jobs in queue: <br>
> `Rs = 1 / (µ - λ` is system residence time: <br>
> `Rq = ρ/(μ − λ)` is queue residence time: 

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
**Open QN models** are models where jobs arrive with a certain rate λ, spend time in the system being served then leave the system when complete.

**Closed QN models** have a fixed number of jobs *N* and after completing a service cycle a job starts again.
>In a closed system there is an additional performance parameter *Z* (think time) which describes the time spent by a job outside the system, after completing a response and before it starts a new request.

### Bottleneck Service Center
The bottleneck of a queuing network is the service center that saturates first with an increase in the arrival rate. This service center will have the highest utilization **U**, highest demand and longest queue **Q**.

## Operational Laws

Operational laws are simple relationships relating to queueing network performance independant of the service time and arrival time distributions.

The following quantities are directly measured during a finite observation time for a service center.

> **T**: observation time <br>
> **A**: number of job arrivals <br>
> **C**: number of job completions<br>
> **B**: total busy time of the server<br>

In steady-state (equilibrium) all jobs that arrive are served *A = C*

The following service center performance metrics can be written in terms of observable operational quantities in a fintie time window:

> *λ = A/T*, Arrival rate is the number of arrivals <br>
> *X = C/T*, Throughput is the number of completions over the observed time.<br>
> *U = B/T*, Utilization is the server time busy over the observed time.
> *S = B/C*, Service time is the time the server is busy for each job completion.

In steady state we can observe since *A = C* then *λ = X* because of job flow balance.

### Utilization Law

`U = X * S`

Relates utilization, throughput and service time which is derived from the service center performance metric relationships.

### Forced Flow Law

`Xi = X * Vi`

Relates system throughput *X* with the throughput of device *i* in a queueing network model. *Vi* describes the number of visits a job makes to deviced *i*. With this we also have the completions at device *i*: `Ci = C * Vi`. 

The difference between system throughput and device throughput is the completions at device *i* which is derived from the visits at device *i*:

System throughput: `X = C / T`<br>
Device throughput: `Xi = Ci / T = (C * Vi) / T`

If we combine utilization and forced flow law we get that `Ui = X * Di`. Where *Di* is the demand at device *i*. rearranging we also have: `Di = Vi * Si`.

### Little's Law

`Q = X * R`

Relates number of jobs in a system with its throughput and the time spent by a job in the system (residence time). This law assumes the system is in steady state.

#### Response Time Law

For a closed system we can say that *N* the number of jobs in the system is *Q* or the queue length. Furthermore we distinguish the system residence time with the think time of the infinite servers (outside the system). So *R = Z + R<sub>sys</sub>*. 

Therefore using **Little's Law** we get: 

`N = X * (Rs + Z)` 

Rearranging for the system residence time yields **Response Time Law**:

`Rs = N / X - Z`

For a service center we measure the jobs in the queue and server, and the queueing and service time:

`N = X * (Qt + S)`

For a server without a queue the residence time is simply the service time so we would actually be calculating the utilization of the server:

`Ui = X * Si`

## Performance Bounds

The bounds on performance is defined by upper and lower bounds on system throughput and residence time as function of workload intensity or arrival rate λ. Works by deriving formulas for lightest and heaviest system workload conditions.

Assumptions:
1. System is in steady-state so that *λ = X*
2. The service demand *D<sub>i</sub>* at a service center *i* is independant of other jobs in the system and where they are situated

### Open Systems

Bottleneck service center is the service center with the highest demand *D<sub>max</sub>* where *max* is the index of the bottleneck service center.

**Throughput Upper Bound** occurs when the bottleneck center reaches saturation: *U<sub>max</sub>(λ) = λ * D<sub>max</sub> <= 1*. Recall at saturation *U<sub>max</sub> = 1* therefore *λ<sub>max</sub> = 1 / D<sub>max</sub>*.

**Response Time Lower Bound** occurs when the system is at a very low load. The total service received by a job without any queueing: *R (λ) >= D* 

### Closed Systems

For closed system our system throughput and residence time is a function of *N* the jobs in the system rather than the arrival rate of jobs *λ*.

**Throughput Bounds** given by:

>*N / (N * D + Z) ≤ X(N) ≤ min(1 / D<sub>max</sub>, N / (D + Z))*

**Residence Time Bounds** given by:

>*max(N * D<sub>max</sub> - Z, D) ≤ R(N) ≤ N * D*

For both throughput and residence time bound analysis cases, the crossover point where the upper throughput and lower residence time bounds cross over is: *N<sup> * </sup> = (D + Z) / D<sub>max</sub>*. This crossover point represents the number of users in the system that causes the bottleneck system to saturate.
