# Chaincode for Product Unit Hub Use Case
## Prerequisites
* [Install Go](https://golang.org/doc/install) on your local machine.
* We reccomend [VSCode](https://code.visualstudio.com/) as Editor for development with this Go [plugin](https://code.visualstudio.com/docs/languages/go) correctly installed.
## Compile the chaincode
* `go get -u --tags nopkcs11 github.com/hyperledger/fabric/core/chaincode/shim`
* `go build --tags nopkcs11`
## Test the chaincode (Hyperledger Fabric Peer dev mode)
Download [Hyperledger Fabric Samples](https://hyperledger-fabric.readthedocs.io/en/latest/samples.html) <br/>
Open a Terminal in your machine:
1. `cd fabric-samples`
2. `cd chaincode && git clone https://github.com/ascatox/product-unit-hub-chaincode.git`
3. `cd ../chaincode-docker-devmode && chmod +x script.sh`
4. `docker-compose -f docker-compose-simple.yaml up -d` (Stop the network using: `docker-compose -f docker-compose-simple.yaml down`)
5. `docker exec -it chaincode bash` (from now you are inside the container)
6. `cd product-unit-hub-chaincode && go build`
7. `CORE_PEER_ADDRESS=peer:7051 CORE_CHAINCODE_ID_NAME=productUnitHub:0 ./product-unit-hub-chaincode`

Open a new Terminal in your machine: 
1. `docker exec -it cli bash`
2. `peer chaincode install -p chaincodedev/chaincode/product-unit-hub-chaincode -n productUnitHub -v 0`
3. `peer chaincode instantiate -n productUnitHub -v 0 -c '{"Args":["a","10"]}' -C mychannel`
4. `peer chaincode invoke -n productUnitHub -c '{"Args":["set", "a", "20"]}' -C mychannel` or `peer chaincode query -n mycc -c '{"Args":["query","a"]}' -C mychannel` (Beware change 'set' and parameters and 'query' and parameters with the functions inside your Go code)



