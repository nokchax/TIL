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
AS는 key-value in-memory 저장소로 전통적인 RDB와 비슷한 개념으로 설계되어 있다. Aerospike 에서 사용하는 용어를 일반적인 관계형 DB와 비교하면 아래 테이블과 같다. 다만 스키마리스이므로 사전에 정의할 필요가 없다.

|Aerospike|RDBMS|
|---|---|
|namespace|database|
|sets|table|
|records|rows|
|bins|column|
 
- bin의 타입으로는 integer, string, blob, list, map을 저장가능하다.
- 배치로 READ 하는 것이 가능하며, 이 배치 작업은 직렬, 병렬로 처리가 가능하다. (Policy로 정할 수 있음)

## 커뮤니티 버전의 Aerospike 단점
- 5TB 까지 밖에 데이터를 저장할 수 없다.
- 클러스터 사이즈 5.x 버전 이상부터는 8대 까지만 가능하다. 엔터프라이즈 버전에서는 256대 까지 가능.
- [참고 known limitation](https://www.aerospike.com/docs/guide/limitations.html)
