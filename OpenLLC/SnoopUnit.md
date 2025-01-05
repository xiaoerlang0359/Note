# SnoopUnit
## Conflict situation
A snoop caused by replacement may be snoop with the same target address triggered by a previous Read/DataLess Snoop request.

when this conflict happen, the new request will blocked and wait for the completion(CompAck) of previous request.
## De-allocation
Once the snoop entry is issued to TXSNP Channel.
## Question
1. The snoop entry is de-allocated when issued to TXSNP Channel, not when receive the compAck of specific request. When there is a same address snoop request come, how can we detect the conflict? Or the CHI bus will deal with the conflict requests.

Answer: the conflict detected by response buffer. Even if the snoop unit is released, the address info still hold by response buffer.

