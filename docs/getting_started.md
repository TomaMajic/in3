# Getting Started 

INCUBED can be used in different ways. For mobile or web-applications, the Type-Script implementation will be the easiest to use.

## npm

```
npm install --save in3
```

### Direct API

You can use incubed as a standalone-library:

```js

// import in3-Module
import In3Client from 'in3'

// use the In3Client as Http-Provider
const c = new In3Client({
    proof: 'standard',
    signatureCount: 1,
    requestCount : 2,
    chainId: 'mainnet'
})

// use the incubed eth api 
const block = await c.eth.getBlockByNumber('latest')
```

### As Provider in Web3

The Incubed Client also implements the Provider-Interface used in the web3-Library and can be used directly.

```js

// import in3-Module
import In3Client from 'in3'
import * as web3 from 'web3'

// use the In3Client as Http-Provider
const web3 = new Web3(new In3Client({
    proof: 'standard',
    signatureCount: 1,
    requestCount : 2,
    chainId: 'mainnet'
}))

// use the web3 
const block = await web.eth.getBlockByNumber('latest')
...
```

## As Docker-Container


In order to start the incubed-client as a standalone client (allowing others none-js-application to connect to it), you can start the container as

```
docker run -d -p 8545:8545  slockit/in3:latest --chainId=mainnet
```

The application would then accept the following arguments:

```eval_rst

.. glossary::
    --nodeLimit
        the limit of nodes to store in the client.

    --keepIn3
        if true, the in3-section of thr response will be kept. Otherwise it will be removed after validating the data. This is useful for debugging or if the proof should be used afterwards.

    --format
        the format for sending the data to the client. Default is json, but using cbor means using only 30-40% of the payload since it is using binary encoding.

    --autoConfig
        if true the config will be adjusted depending on the request
    
    --retryWithoutProof
        if true the request may be handled without proof in case of an error. (use with care!)

    --includeCode
        if true, the request should include the codes of all accounts. otherwise only the codeHash is returned. In this case the client may ask by calling eth_getCode() afterwards

    --maxCodeCache
        number of max bytes used to cache the code in memory

    --maxBlockCache
        number of number of blocks cached  in memory

    --proof
        'none' for no verification, 'standard' for verifying all important fields, 'full'  veryfying all fields even if this means a high payload.

    --signatureCount
        number of signatures requested

    --finality
        percenage of validators signed blockheaders - this is used for PoA (aura)

    --minDeposit
        min stake of the server. Only nodes owning at least this amount will be chosen.

    --replaceLatestBlock
        if specified, the blocknumber *latest* will be replaced by blockNumber- specified value

    --requestCount
        the number of request send when getting a first answer

    --timeout
        specifies the number of milliseconds before the request times out. increasing may be helpful if the device uses a slow connection.

    --chainId
        servers to filter for the given chain. The chain-id based on EIP-155.

    --chainRegistry
        main chain-registry contract

    --mainChain
        main chain-id, where the chain registry is running.

    --autoUpdateList
        if true the nodelist will be automaticly updated if the lastBlock is newer

    --loggerUrl
        a url of RES-Endpoint, the client will log all errors to. The client will post to this endpoint JSON like { id?, level, message, meta? }

```
## Chains

Currently incubed is deployed on the following chains:

### Mainnet

Registry : [0x2736D225f85740f42D17987100dc8d58e9e16252](https://eth.slock.it/#/main/0x2736D225f85740f42D17987100dc8d58e9e16252)    
ChainId : 0x1 (alias `mainnet`)    
Status : [https://in3.slock.it?n=mainnet](https://in3.slock.it?n=mainnet)    
NodeList: [https://in3.slock.it/mainnet/nd-3](https://in3.slock.it/mainnet/nd-3/api/in3_nodeList) 


### Kovan

Registry : [0x27a37a1210df14f7e058393d026e2fb53b7cf8c1](https://eth.slock.it/#/kovan/0x27a37a1210df14f7e058393d026e2fb53b7cf8c1)    
ChainId : 0x2a (alias `kovan`)    
Status : [https://in3.slock.it?n=kovan](https://in3.slock.it?n=kovan)    
NodeList: [https://in3.slock.it/kovan/nd-3](https://in3.slock.it/kovan/nd-3/api/in3_nodeList) 


### Tobalaba

Registry : [0x845E484b505443814B992Bf0319A5e8F5e407879](https://eth.slock.it/#/tobalaba/0x845E484b505443814B992Bf0319A5e8F5e407879)    
ChainId : 0x44d (alias `tobalaba`)    
Status : [https://in3.slock.it?n=tobalaba](https://in3.slock.it?n=tobalaba)    
NodeList: [https://in3.slock.it/tobalaba/nd-3](https://in3.slock.it/tobalaba/nd-3/api/in3_nodeList) 



### Evan

Registry : [0x85613723dB1Bc29f332A37EeF10b61F8a4225c7e](https://eth.slock.it/#/evan/0x85613723dB1Bc29f332A37EeF10b61F8a4225c7e)    
ChainId : 0x4b1 (alias `evan`)    
Status : [https://in3.slock.it?n=evan](https://in3.slock.it?n=evan)    
NodeList: [https://in3.slock.it/evan/nd-3](https://in3.slock.it/evan/nd-3/api/in3_nodeList) 


### Görli

Registry : [0x85613723dB1Bc29f332A37EeF10b61F8a4225c7e](https://eth.slock.it/#/goerli/0x85613723dB1Bc29f332A37EeF10b61F8a4225c7e)    
ChainId : 0x5 (alias `goerli`)    
Status : [https://in3.slock.it?n=goerli](https://in3.slock.it?n=goerli)    
NodeList: [https://in3.slock.it/goerli/nd-3](https://in3.slock.it/goerli/nd-3/api/in3_nodeList) 


### IPFS

Registry : [0xf0fb87f4757c77ea3416afe87f36acaa0496c7e9](https://eth.slock.it/#/kovan/0xf0fb87f4757c77ea3416afe87f36acaa0496c7e9)    
ChainId : 0x7d0 (alias `ipfs`)    
Status : [https://in3.slock.it?n=ipfs](https://in3.slock.it?n=ipfs)    
NodeList: [https://in3.slock.it/ipfs/nd-3](https://in3.slock.it/ipfs/nd-3/api/in3_nodeList) 


## Registering a own in3-node

If you want to participate in this network and also register a node, you need to send a transaction to the registry-contract calling `registerServer(string _url, uint _props)`.

ABI of the registry:

```js
[{"constant":true,"inputs":[],"name":"totalServers","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"_serverIndex","type":"uint256"},{"name":"_props","type":"uint256"}],"name":"updateServer","outputs":[],"payable":true,"stateMutability":"payable","type":"function"},{"constant":false,"inputs":[{"name":"_url","type":"string"},{"name":"_props","type":"uint256"}],"name":"registerServer","outputs":[],"payable":true,"stateMutability":"payable","type":"function"},{"constant":true,"inputs":[{"name":"","type":"uint256"}],"name":"servers","outputs":[{"name":"url","type":"string"},{"name":"owner","type":"address"},{"name":"deposit","type":"uint256"},{"name":"props","type":"uint256"},{"name":"unregisterTime","type":"uint128"},{"name":"unregisterDeposit","type":"uint128"},{"name":"unregisterCaller","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"_serverIndex","type":"uint256"}],"name":"cancelUnregisteringServer","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"_serverIndex","type":"uint256"},{"name":"_blockhash","type":"bytes32"},{"name":"_blocknumber","type":"uint256"},{"name":"_v","type":"uint8"},{"name":"_r","type":"bytes32"},{"name":"_s","type":"bytes32"}],"name":"convict","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"_serverIndex","type":"uint256"}],"name":"calcUnregisterDeposit","outputs":[{"name":"","type":"uint128"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"_serverIndex","type":"uint256"}],"name":"confirmUnregisteringServer","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"_serverIndex","type":"uint256"}],"name":"requestUnregisteringServer","outputs":[],"payable":true,"stateMutability":"payable","type":"function"},{"anonymous":false,"inputs":[{"indexed":false,"name":"url","type":"string"},{"indexed":false,"name":"props","type":"uint256"},{"indexed":false,"name":"owner","type":"address"},{"indexed":false,"name":"deposit","type":"uint256"}],"name":"LogServerRegistered","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"url","type":"string"},{"indexed":false,"name":"owner","type":"address"},{"indexed":false,"name":"caller","type":"address"}],"name":"LogServerUnregisterRequested","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"url","type":"string"},{"indexed":false,"name":"owner","type":"address"}],"name":"LogServerUnregisterCanceled","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"url","type":"string"},{"indexed":false,"name":"owner","type":"address"}],"name":"LogServerConvicted","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"url","type":"string"},{"indexed":false,"name":"owner","type":"address"}],"name":"LogServerRemoved","type":"event"}]
```


To run a incubed node, you simply use docker-compose:

```yaml
version: '2'
services:
  incubed-server:
    image: slockit/in3-server:latest
    volumes:
    - $PWD/keys:/secure                                     # directory where the private key is stored 
    ports:
    - 8500:8500/tcp                                         # open the port 8500 to be accessed by public
    command:
    - --privateKey=/secure/myKey.json                       # internal path to the key
    - --privateKeyPassphrase=dummy                          # passphrase to unlock the key
    - --chain=0x1                                           # chain (kovan)
    - --rpcUrl=http://incubed-parity:8545                   # url of the kovan-client
    - --registry=0xFdb0eA8AB08212A1fFfDB35aFacf37C3857083ca # url of the incubed-registry 
    - --autoRegistry-url=http://in3.server:8500             # check or register this node for this url
    - --autoRegistry-deposit=2                              # deposit to use when registering

  incubed-parity:
    image: slockit/parity-in3:v2.2                          # parity-image with the getProof-function implemented
    command:
    - --auto-update=none                                    # do not automaticly update the client
    - --pruning=archive 
    - --pruning-memory=30000                                # limit storage
```
