#  prometheus2kafka

Prometheus配置：

```
[...]

remote_write:
  - url: "http://localhost:18918"

[...]
```



### Getting started

prometheus2kafka 是参照[Prometheus官方远程存储源码](https://github.com/prometheus/prometheus/blob/v2.3.2/documentation/examples/remote_storage/remote_storage_adapter/main.go)，结合 [sarama](https://github.com/Shopify/sarama)（Kafka Clients-Go）写的一个适配器。将prometheus收集到的指标数据同步到Kafka。支持生产者同步或异步，默认异步，高并发场景使用。适配器访问日志也可以写入Kafka，默认关闭。



## Build

```
$ cd prometheus2kafka
$ go get ./...
$ go build
```



## Running

```
$ ./prometheus2kafka <flags>
```



## Usage

```shell
Usage of ./prometheus2kafka:
  -accesslog
    	Accesslog writes to Kafka
  -addr string
    	The address to bind to (default ":18918")
  -async
    	Async producer mode (default true)
  -brokers string
    	The Kafka brokers to connect to, as a comma separated list
  -ca string
    	The optional certificate authority file for TLS client authentication
  -certificate string
    	The optional certificate file for client authentication
  -key string
    	The optional key file for client authentication
  -topic string
    	The Kafka topic to write to (default "prometheus")
  -verbose
    	Turn on Sarama logging
  -verify
    	Optional verify ssl certificates chain
```



