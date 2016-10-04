# Kafka related code

## simple-data-producer.py
implemented a kafka producer,fetching one piece of stock information from Yahoo finance, send to Kafka

### dependency
googlefinance   https://pypi.python.org/pypi/googlefinance

kafka-python    https://github.com/dpkp/kafka-python

schedule        https://pypi.python.org/pypi/schedule

```sh
pip install -r requirements.txt
```

### running
assuming a Kafka running in a docker-machine called bigdata,assuming virtual machine ip is 192.168.99.100
```sh
python simple-data-producer.py AAPL stock-analyzer 192.168.99.100:9092
```


## fast-data-producer.py
implemented a kafka producer, generating random stock price, send to Kafka
there will be a lot of data generated, please isolate your development environment.
### dependency
confluent-kafka https://github.com/confluentinc/confluent-kafka-python

### running
assumging you have a Kafka running in a bigdata docker-machine, and assuming the virtual ip is 192.168.99.100
```sh
python fast-data-producer.py stock-analyzer 192.168.99.100:9092
```
