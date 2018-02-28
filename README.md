# product-unit-hub-chaincode

## Compile the chaincode
go get -u --tags nopkcs11 github.com/hyperledger/fabric/core/chaincode/shim
go build --tags nopkcs11
## Test the chaincode (dev mode)
1. Download [Hyperledger Fabric Samples](https://hyperledger-fabric.readthedocs.io/en/latest/samples.html) 
2. `cd chaincode-docker-devmode`
3. `docker-compose -f docker-compose-simple.yaml up`
4. `docker exec -it chaincode bash`
5. cd product-unit-hub && go build
6. CORE_PEER_ADDRESS=peer:7052 CORE_CHAINCODE_ID_NAME=productunithub:0 ./product-unit-hub
