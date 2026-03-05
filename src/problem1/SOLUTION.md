grep "TSLA" transaction-log.txt | grep "sell" | cut -d'"' -f4 | curl https://example.com/api/:order_id >> ./output.txt
