# Kafka-Stream
**Kafka Stream - Stock Trade**

1) To start the broker 
**$ sh kafka-server-start /usr/local/etc/kafka/server.properties**

2) Kafka Topic - to send all stock data
**$ sh kafka-console-consumer --bootstrap-server localhost:9092 --topic stock-data-topic --from-beginning**


3) Kafka Topic - to send record for the maximum traded value (TOTTRDVAL in the sample data file) for each day. 
**$ sh kafka-console-consumer --bootstrap-server localhost:9092 --topic max-TTV-stock-data-topic --from-beginning**
`{"symbol":"ICICIBANK","series":"EQ","open":"367.8","high":381.8,"low":366.6,"close":380.15,"last":379.3,"previousClose":367.7,"totalTradedQty":2.1501136E7,"totalTradedVal":8.0807185982E9,"tradeDate":"08-Jan-2019","totalTrades":180003.0,"isinCode":"INE090A01021"}
{"symbol":"INFY","series":"EQ","open":"686.2","high":689.8,"low":664.0,"close":676.1,"last":675.6,"previousClose":670.05,"totalTradedQty":1.8130292E7,"totalTradedVal":1.22997380748E10,"tradeDate":"09-Jan-2019","totalTrades":314702.0,"isinCode":"INE009A01021"}
{"symbol":"YESBANK","series":"EQ","open":"193.9","high":194.4,"low":185.8,"close":187.15,"last":186.55,"previousClose":189.65,"totalTradedQty":4.0515242E7,"totalTradedVal":7.71776961175E9,"tradeDate":"07-Jan-2019","totalTrades":215186.0,"isinCode":"INE528G01027"}
`

_Please note StockDataConsumer code will only be active for 60 seconds, and then find output to max-TTV-stock-data-topic kafka topic.__
    
`val deadline = 60.seconds.fromNow
while (deadline.hasTimeLeft) { ...`