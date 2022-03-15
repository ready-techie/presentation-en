# Apache Kafka - Message Queuing

Created: March 9, 2022
Created by: Anne Lee
Tags: Software Tool

# What is Kafka?

> *Apache Kafka is an open-source distributed event streaming platform used by thousands of companies for high-performance data pipelines, streaming analytics, data integration, and mission-critical applications.*
> 
- Event Streaming: the practice of capturing data in real-time event sources like databases or software applications in the form of streams of event.

# Why we use Kafka?

In the official reference,

1. To process payments and financial transactions in real-time, such as in stock exchanges, banks, and insurances
2. To track and monitor cars, trucks, fleets, and shipments in real-time, such as in logistics and the automotive industry
3. To continuously capture and analyze sensor data from IoT devices or other equipment, such as in factories and wind parks
4. To collect and immediately react to customer interactions and orders, such as in retail, the hotel and travel industry, and mobile applications
5. To monitor patients in hospital care and predict changes in condition to ensure timely treatment in emergencies
6. To connect, store, and make available data produced by different divisions of a company
7. To serve as the foundation for data platforms, event-driven architectures, and microservices

In my side project,

- Why use Message Queue?

![sago_online_auction_architecture drawio](https://user-images.githubusercontent.com/15176192/158314385-0c39e1e2-c16c-47f3-a414-3c13d2a7b00f.png)

- Which one is the best fit? RabbitMQ vs Apache Kafka

# Pros & Cons

- Pros:
    - High throughput(High TPS) → efficient regarding huge traffic in real-time system
- Cons:
    - Not supported various features like conventional Message Queuing platform

# Reference

[Apache Official Reference](https://kafka.apache.org/documentation/#intro_usage)

[Kakao Tech Blog](https://tech.kakao.com/2020/06/08/websocket-part1/)
