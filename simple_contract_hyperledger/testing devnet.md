For devnet
——————

FORWARD_DOCKER_PORTS='true' vagrant up

vagrant ssh

docker run -p 5000:5000 --rm -it -e CORE_VM_ENDPOINT=http://172.17.0.1:2375 -e CORE_PEER_ID=vp0 -e CORE_PEER_ADDRESSAUTODETECT=true hyperledger-peer peer node start

CORE_PEER_ADDRESS=172.17.0.2:30303 ./peer chaincode deploy -p github.com/hyperledger/fabric/examples/chaincode/go/simple_contract_hyperledger -c '{"Function":"Init", "Args": ["{\"version\":\"1.0\"}"]}'

use -n as we do in sandbox, with name returned on deploy, for example
202f9dc6c8a2c098cb0372128b7b0a1bf02712b8f4c2b14772dd0fec6a53e5179d322b81827c8b39a914e13e207ba1f73bf918d717fd753f10e70e97407cf30d

You can use postman / ARC or other rest clients too. Example scripts are at https://github.com/ibm-watson-iot/blockchain-samples/blob/master/trade_lane_contract_hyperledger/postman_tests/Hyperledger_Rest_Postman_Collection.json and can be adapted easily
