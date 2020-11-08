# Aerospike
## Overview
에어로스파이크는 확장가능한 분산형 데이터베이스로, 아키텍쳐는 3개의 핵심 목표가 있다.

- 웹 규모의 앱을 위한 유연하고 확장 가능한 플랫폼을 구축한다.
- 기존 데이터베이스에서 기대되는 견고함과 신뢰성을 제공한다.
- 사람의 개입을 최소화 하여 운영에 있어서 효율성을 제공한다.

에어로스파이크는 아래의 세 계층으로 구성된다.
- Client layer
  - 이 계층은 Aerospike API를 구현한 라이브러리가 포함되어 있으며, 노드를 추적하고, 클러스터 내 데이터가 어디에 있는지를 알고 있다.
- Clustering and Data distribution layer
  - 이 계층은 클러스터 통신을 관리하고 장애 복구(fail-over), 리플리케이션, XDR(Cross-Datacenter Replication), 리밸런싱 그리고 데이터 마이그레이션을 자동화 한다.
- Data storage layer
  - 이 계층은 빠른 검색을 위해 DRAM과 SSD에 데이터를 안정적으로 저장하는 역할을 한다.

## Client layer




## Aerospike 용어 정리
Aerospike 에서 사용하는 용어를 일반적인 관계형 DB와 비교하면 아래 테이블과 같다.

|Aerospike|RDBMS|
|---|---|
|namespace|database|
|sets|table|
|records|rows|
|bins|column|
 