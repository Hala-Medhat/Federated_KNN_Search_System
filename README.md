# Federated_KNN_Search_System

## To Test the system

### You have to set up redis first
```
docker build -t my_redis .
docker run -d -p 6379:6379 --name redis-server my_redis  
```
Run first command only to add authentication security to prevent spoofing

### Project Files
In this project you have 4 files

- Node file : this is reponsible for creating local knn nodes
- Aggregator File: this is reponsible for aggregating the results after sending the search query
- Query file: this is the file we you send queries to Aggregator to start sending to local nodes and aggregate the results
- Dos file: this will simulate the dos attack
- spoofing file: this will simulate spoffing attack

### Node file

- In the node file, run the first cell to for setup
- If you want to tamper results for one of nodes, run cell node3.tamper_data()
- If you want to de tamper it run cell node3.detamper_data()

### Aggregator file

- In the aggregator file, run the first cell to for setup
- If you want to set rate limit for aggregator, run cell rate_limit_bool is set to True, else run rate_limit_bool set to False
- If you want to set apply label fliping mitigation , run cell message_tampering is set to True, else run message_tampering set to False
- If you want to check if message tampered with, or send by unlegitimate user, run message_integrity set to True, else run message_integrity set to False

### Query file
- In the query file, run first cell for set up
- You will have the results of running on test dataset, using different voting and distance meterics, with tampering and with tampering and mitigation
- Go to last cell to test

### Dos file
- Run first cell to launch attack when it finishes go to query file send a request and see how long it took to respond.
- To apply rate limiting run cell rate_limit_bool is set to True in aggregator file

### Spoofing attack
- If first line when setting up redis was ran, it will not be able to join network
- If not, it will join and you can prevent it from being processed by setting message_integrity to True in aggregator file since  node can't sign message

### Tampering attack 
- run for one of nodes in node file , tamper_data = True

Don't run in aggregator and  node more than once, if done delete redis container and start over.

