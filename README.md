# aws_cli
cmd of some aws_cli to back to

## This command lists, filters, and deletes Lambda functions.
    aws lambda list-functions | jq -r '.Functions[].FunctionName' | grep "http" |xargs -I {} aws lambda delete-function --function-name {}


## This command lists, filters, and deletes dynamodb table .
    aws dynamodb list-tables | jq -r '.TableNames[]' | grep "itrm" | xargs -I {} aws dynamodb delete-table --table-name {}
    

## query api
    aws apigatewayv2 list-apis --query 'Items[*].[ApiName,ApiId]'
    
    
## alternative 
    # Get the API ID of the HTTP API
api_id=$(aws apigatewayv2 get-apis | jq -r '.Items[] | select(.Name | contains("http")) | .ApiId')

## Clean up HTTP API with AWS CLI.
    aws apigatewayv2 delete-api --api-id $api_id
