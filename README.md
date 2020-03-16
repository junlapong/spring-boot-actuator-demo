# Spring Boot Actuator Demo

## Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/2.2.5.RELEASE/reference/htmlsingle/#production-ready)
* [1. Spring Boot Actuator: Health check, Auditing, Metrics gathering and Monitoring](https://www.callicoder.com/spring-boot-actuator/)
* [2. Spring Boot Actuator metrics monitoring with Prometheus and Grafana](https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service with Spring Boot Actuator](https://spring.io/guides/gs/actuator-service/)

## Notes

- [Spring Boot 2 - Actuator Metrics Endpoint not working](https://stackoverflow.com/questions/48503571/spring-boot-2-actuator-metrics-endpoint-not-working)


## Prometheus

Setup `HOST_IP` at 'prometheus/prometheus.yml`

```yml
    static_configs:
      - targets: ['HOST_IP:8080']
#      - targets: ['192.168.0.155:8080'] # example
```

Run Prometheus using Docker

```
docker run --rm -it --name=prometheus -p 9090:9090 \
       -v ${PWD}/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml \
       prom/prometheus --config.file=/etc/prometheus/prometheus.yml
```

Or run Prometheus using Docker Compose

```
docker-compose run prometheus
```

Visualizing Spring Boot Metrics from Prometheus dashboard
That’s it! You can now navigate to http://localhost:9090

## Grafana

```
docker run -d --name=grafana -p 3000:3000 grafana/grafana
```

See [Configuring Grafana to import metrics data from Prometheus](https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/#configuring-grafana-to-import-metrics-data-from-prometheus)
