# ReqArb
## Block overview
Arbiter receive requests from:

* Upstream CHI bus
* Refill Task

Refill Task has higher priority. After arbitration, unit sends request to *main pipe* and *refill unit*, also send read request to directory.

Another function for this unit is check hazard and stall request in this unit. Any detail will be presented in chapter *hazard detect*.

## Interface
|name | description|
|---|---|
|busTask_s1|requests from CHI bus, include address, transaction id, src id , etc.|
|refillTask_s1| requests form refill unit, except the above information, also include refill buffer id|
|dirRead_s1| read local/clients directory, this is meta read requests from CHI bus or refill unit|
|TaskToPipe_s2| send task to main pipe|
|refillBufRead_s2| send refillBuf read request|
|pipeInfo| this and below signals are used for handling set conflict, capacity conflict and coherency conflict|
|refillInfo||
|respInfo||
|snpInfo||
memInfo||

## Hazard detect
If a hazard detect between new task and inflight Tasks, new task would be blocked.

| Inflight Tasks| hazard situation|
|---|---|
| main Pipe S2| same set, for directory RAW|
| main Pipe S3| same set, for directory RAW|
| main pipe S4| same set, snoop task caused by replacement may be issued at S4|
| main pipe S5| same cache line, requests order|
| main pipe S6| same cache line, requests order|
| refill tasks| only upstream CHI bus new task. same cache line, same reqID or refill buffer will overflow|
| Response Tasks| only upstream CHI bus new task. same cache line, same reqID or response buffer will overflow|
| snoop Tasks| only upstream CHI bus new task. same ReqID or snoop buffer will overflow|
| mem unit tasks| for CHI bus task: same reqID or mem unit overflow. for refill task: only  overflow|

## Question
1. snp only check ReqID hazard, no address hazard?
2. ReqID meaning?
3. same line block behavior has problem with performance?


