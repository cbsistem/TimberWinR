# Output: Redis

The Redis output passes on data to Redis to be consumed by the Logtash indexer.

## Parameters
The following parameters are allowed when configuring the Redis output.

| Parameter     |   Type   |  Description                                                | Details               |  Default |
| :-------------|:---------|:------------------------------------------------------------| :---------------------------  | :-- |
| *batch_count* | integer  | Sent as a single message                         | Number of messages to aggregate | 200 |
| *host*        | string | The hostname(s) of your Redis server(s) | IP or DNS name |  |
| *index*       | string   | The name of the redis list                                  | logstash index name | logstash |
| *interval*    | integer  | Interval in milliseconds to sleep during batch sends        | Interval      | 5000 |
| *max_batch_count* | integer  | Dynamically adjusted count maximum                      | Increases over time | batch_count * 10 |
| *max_queue_size* | integer  | Maximum redis queue depth       |  | 50000 |
| *port*        | integer  | Redis port number                                           | This port must be open  | 6379  |
| *queue_overflow_discard_oldest* | bool  | If true, discard oldest messages when max_queue_size reached otherwise discard newest |  | true |
| *threads*     | string   | Location of log files(s) to monitor                         | Number of worker theads to send messages | 1 |

Example Input:
```json
{
    "TimberWinR": {
        "Outputs": {
            "Redis": [
               { 
                    "threads":  1,   
                    "interval": 5000, 
                    "batch_count":  500,              
                    "host": [
                        "tstlexiceapp006.mycompany.svc"
                    ]
                }
            ]
		}
	}
}
```