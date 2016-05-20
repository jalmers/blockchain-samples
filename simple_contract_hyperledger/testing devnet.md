For devnet
——————

FORWARD_DOCKER_PORTS='true' vagrant up

vagrant ssh

docker run -p 5000:5000 --rm -it -e CORE_VM_ENDPOINT=http://172.17.0.1:2375 -e CORE_PEER_ID=vp0 -e CORE_PEER_ADDRESSAUTODETECT=true hyperledger-peer peer node start

CORE_PEER_ADDRESS=172.17.0.2:30303 ./peer chaincode deploy -p github.com/hyperledger/fabric/examples/chaincode/go/simple_contract_hyperledger -c '{"Function":"Init", "Args": ["{\"version\":\"1.0\"}"]}'

