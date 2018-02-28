# Chaincode for Product Unit Hub Use Case
## Prerequisites
* [Install Go](https://golang.org/doc/install) on your local machine.
* We reccomend [VSCode](https://code.visualstudio.com/) as Editor for development with this Go [plugin](https://code.visualstudio.com/docs/languages/go) correctly installed.
## Compile the chaincode
* `go get -u --tags nopkcs11 github.com/hyperledger/fabric/core/chaincode/shim`
* `go build --tags nopkcs11`
## Test the chaincode (dev mode)
1. Download [Hyperledger Fabric Samples](https://hyperledger-fabric.readthedocs.io/en/latest/samples.html) 
2. `cd chaincode-docker-devmode`
3. `docker-compose -f docker-compose-simple.yaml up`
4. `docker exec -it chaincode bash`
5. `cd product-unit-hub && go build`
6. `CORE_PEER_ADDRESS=peer:7052 CORE_CHAINCODE_ID_NAME=productUnitHub:0 ./product-unit-hub`



