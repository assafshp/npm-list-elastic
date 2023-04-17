Run the demo-react-app
==========
1. cd demo-react-app
2. npm start



Create elasticsearch cluster in bonsai.io
==========
1. Go to https://bonsai.io/ and login (or signup for free)
2. Create a sandbox cluster for free
3. Create new index via curl (curl --location --request PUT 'https://user:pwd@demo-591693139.us-east-1.bonsaisearch.net:443/npmls')


Run cli command to enter npm list data to elasticsearch 
==========
1. cd demo-react-app
2. to collect the npm packages version use the following command:
3. run `npm list --json`

4. to send the npm info json file as document to elastic use the following command (make sure jq is installed first):
5. run `npmlsv=$(npm list --json | jq --argjson ts $(date +%s) '. += {"timestamp":$ts}') && curl --location 'https://user:pwd@demo-591693139.us-east-1.bonsaisearch.net:443/npmls/_doc' \
--header 'Content-Type: application/json' \
--data-raw "$npmlsv"`


References
======
- https://bonsai.io
- https://stedolan.github.io/jq/