# Instructions

## Commands

```bash
ccloud login
ccloud environment use t34809
ccloud schema-registry subject list
ccloud schema-registry schema describe --subject users-value --version latest
```

## Create a topic

```bash
ccloud kafka topic create --cluster lkc-5mw18 transactions-avro
ccloud kafka topic create --cluster lkc-5mw18 transactions-proto
```

## Create schema

```bash
ccloud schema-registry schema create --subject transactions-value --schema avro/src/main/resources/avro/io/confluent/examples/clients/basicavro/Payment.avsc --type AVRO
ccloud schema-registry schema create --subject transactions-proto-value --schema person.proto --type PROTOBUF
```

## Create v2 schema

```bash
# Fails
ccloud schema-registry schema create --subject transactions-value --schema Payment2a.avsc --type AVRO
# Succeeds
ccloud schema-registry schema create --subject transactions-value --schema Payment2b.avsc --type AVRO
# Diff using vscode
code --diff avro/src/main/resources/avro/io/confluent/examples/clients/basicavro/Payment2a.avsc avro/src/main/resources/avro/io/confluent/examples/clients/basicavro/Payment2b.avsc
```
