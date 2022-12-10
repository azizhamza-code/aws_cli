# aws_cli
cmd of some aws_cli to back to

## This command lists, filters, and deletes Lambda functions.
    aws lambda list-functions | jq -r '.Functions[].FunctionName' | grep "http" |xargs -I {} aws lambda delete-function --function-name {}


#### This command lists, filters, and deletes dynamodb table .
    aws dynamodb list-tables | jq -r '.TableNames[]' | grep "itrm" | xargs -I {} aws dynamodb delete-table --table-name {}
