## Problem 1: Too Many Things To Do

This following is the cmd to get the expected result.

```bash
grep "TSLA" transaction-log.txt | grep "sell" | cut -d'"' -f4 | curl https://example.com/api/:order_id >> ./output.txt
```
