# dynamoDB
Experiments on DynamoDb
#
aws dynamodb create-table \
    --table-name Arrangements \
    --attribute-definitions \
        AttributeName=ArrangementId,AttributeType=S \
        AttributeName=EventName,AttributeType=S \
        AttributeName=Date,AttributeType=S \
    --key-schema \
        AttributeName=ArrangementId,KeyType=HASH \
    --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5 \
    --global-secondary-indexes \
        "[
            {
                \"IndexName\": \"EventNameDateIndex\",
                \"KeySchema\": [
                    {\"AttributeName\":\"EventName\",\"KeyType\":\"HASH\"},
                    {\"AttributeName\":\"Date\",\"KeyType\":\"RANGE\"}
                ],
                \"Projection\":{
                    \"ProjectionType\":\"ALL\"
                },
                \"ProvisionedThroughput\": {
                    \"ReadCapacityUnits\": 5,
                    \"WriteCapacityUnits\": 5
                }
            }
        ]"
#


{'ArrangementId': 'arrangement-id-1',
 'Life-cycle-events': [{'CurrentData': '{"UserId": "user2", "Name": "Bob", "Age": 25}',
                        'Date': '2024-01-02',
                        'EventName': 'Card Block',
                        'SequenceNumber': 20,
                        'PreviousData': '{"UserId": "user2", "Name": "Bob", "Age": 26}'}]}
{'ArrangementId': 'arrangement-id-2',
 'Life-cycle-events': [{'CurrentData': '{"UserId": "user3", "Name": "Alice", "Age": 30}',
                        'Date': '2024-01-03',
                        'EventName': 'Card Activation',
                        'SequenceNumber': 21,
                        'PreviousData': '{"UserId": "user3", "Name": "Alice", "Age": 31}'}]}

This output confirms th
