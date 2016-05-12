Note: These steps are only provided in case there are challenges with the Bluemix environment or if you are making code changes and want to quickly test in the local environemnt. The recommended approach is to use the IoT Platoform and Monitoring UI to run the contract


1. Copy the simple_contract_hyperledger folder to the Examples folder in your Sandbox hyperledger fabric.

2. Start Vagrant and the Vagrant shell (vagrant ssh) 

3. go build in the simple_contract_hyperledger folder

4. In the peer folder, start peer: ./peer peer --peer-chaincodedev

5. Register to the shim in the sandbox, inside the contract folder: CORE_CHAINCODE_ID_NAME=simhyp CORE_PEER_ADDRESS=0.0.0.0:30303 ./simple_contract_hyperledger

6. Run the tests (from  /opt/gopath/src/github.com/hyperledger/fabric/peer)

a. deploy:

./peer chaincode deploy -n simhyp -c '{"Function":"Init", "Args": ["{\"version\":\"1.0\"}"]}'

b. query schema: 

./peer chaincode query -l golang -n simhyp  -c '{"Function":"readAssetSchemas", "Args":[]}'

c. create / update and read (invoke and query calls)

create:
./peer chaincode invoke -l golang -n simhyp -c '{"Function":"createAsset", "Args":["{\"assetID\":\"CON123\", \"location\":{\"latitude\":34, \"longitude\":23},  \"carrier\":\"ABCCARRIER\"}"]}'

read:
./peer chaincode query -l golang -n simhyp -c '{"Function":"readAsset", "Args":["{\"assetID\":\"CON123\"}"]}'

update:
./peer chaincode invoke -l golang -n simhyp -c '{"Function":"updateAsset", "Args":["{\"assetID\":\"CON123\", \"location\":{\"latitude\":34, \"longitude\":25}},\"temperature\":14,  \"carrier\":\"ABCCARRIER\"}"]}'

A new call to 'read' should give you the updated asset record.

delete:
./peer chaincode invoke -l golang -n simhyp -c '{"Function":"deleteAsset" , "Args":["{\"assetID\":\"CON123\"}"]}' 





