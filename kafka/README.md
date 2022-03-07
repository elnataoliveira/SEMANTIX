### kafka

#### creating kafka topics

kafka-topics --bootstrap-server localhost:9092 --create --topic msg-cli --partitions 2 --replication-factor 1

#### describe kafka topic

kafka-topics --bootstrap-server localhost:9092 --topic msg-cli --describe

#### creating kafka producers

kafka-console-producer --broker-list localhost:9092 --topic msg-cli

#### creating kafka consumers groups

kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app2-cli

#### reset off-sets

kafka-consumer-groups --bootstrap-server localhost:9092 --reset-offsets --shift-by -2 --execute --topic msg-cli --group app-cli

#### describe group

kafka-consumer-groups --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

#### consumer

kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

#### describe group

kafka-consumer-groups --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

#### reset all off-sets

kafka-consumer-groups --bootstrap-server localhost:9092 --reset-offsets --to-earliest --execute --topic msg-cli --group app-cli

#### describe group

kafka-consumer-groups --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

#### list all groups

kafka-consumer-groups --bootstrap-server localhost:9092 --list

 
 
