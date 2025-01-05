# mainPipe
## Block overview
## Interface
|signal|description|
|---|--|
|taskFromArb_s2|receive incoming task from reqArb|
|dirResp_s3| get meta response|
|dirWReq_s3| update self/client directory at stage 3|
|refillBufResp_s4| get refill data at stage 4 |
|refillTask_s4| send allocation request to RefillUnit at stage 4|
|snoopTask_s4| send Snoop request via upstream TXSNP channel|
|readTask_s4| ReadNoSnp task to MemUnit|
|writeTask_s4| WriteNoSnp task to MemUnit|
|compTask_s4| CompDBIDResp task to ResponseUnit|
|compTask_s6| CompData task to ResponseUnit|
|toDS_s4| read write data storage|
|rdataFromDS_s6| response rdata from data storage|
|pipeInfo| pipe info to reqArb hazard check|
## directory
First mainPipe category four actions:

* exclusiveReq: readUnique, readNotSharedDirty and peer cache not hit, makeUnique
* shareReq: readNotSharedDirty and peer cache hit
* releaseReq: writeBackFull, evict
* refillReq
### self
|action|old_meta|update|new_meta|
|---|---|---|---|
|exclusiveReq|hit|yes|Invalid|
|shareReq|x|no|x|
|releaseReq|x|no|x|
|refillReq|hit and dirty|yes|valid and dirty|
|refillReq and Pass Dirty|x|yes|valid and dirty|
|refillReq|except hit and dirty|yes|valid|
### client
#### requester
|action|old_meta|update|new_meta|
|---|---|---|---|
|exclusiveReq|no hit|yes|valid|
|shareReq|no hit|yes|valid|
|release|hit|yes|invalid|
#### peer cache
|action|old_meta|update|new_meta|
|---|---|---|---|
|exclusiveReq|hit|yes|invalid|
|other|x|no|x|

# question
1. release does not take action on self LLC cache line? no state change

