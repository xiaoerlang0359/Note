# RefillUnit
## Allocation
refill task includes three situations:

1. Shared Request. Because the LLC allocation policy is EXCLUSIVE for single-core, INCLUSIVE for multi-core. A SharedReq means there will be multi-core share the cache copy. The LLC local cache need refill a copy from snpData, if there is no hit copy for the cache line.
2. WriteBackFull. When a clients wants to write back a cache copy, the cache copy will hold by LLC local cache.
3. replace_snoop_s4. when clients directory is full valid for the requests set, and no way hit. LLC would replace a clients' cache line by snoop. When the snoop data write back, it will allocate to LLC local cache. 

## Update
When response data or response comeback. Refill entry will clear specific snp vector bit. When get all data, refill entry will set ready bit.

## Issue refill task
When a snoop entry encounter follow requirements:
1. receive all data
2. have not sent refill task yet
3. need snoop response and get all snoop response/ do not need snoop response
4. valid entry

An arbiter will get final refill task.

## De-allocation
1. cancel ?
2. refill data has been read out by main pipe.

## Question
1. What does signal inv_CBWrData means? Does it mean write back a invalidate cache copy? And what does rspData channel resp field means?
2. Situation for de-allocation cancel?
