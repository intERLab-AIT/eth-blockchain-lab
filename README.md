# Genesis for baengpun chain

## Initializing the genesis block

```bash
git clone https://github.com/padillareyj/baengpun-chain
geth init --datadir baengpun-chain baengpun-chain/genesis.json
```

## Running the node

```bash
geth --datadir baengpun-chain --networkid 123454321 --nat extip:[IP-ADDRESS] --unlock [ACCOUNT] --password [password-for-keystore]
```

For example:

```bash
geth --datadir baengpun-chain --networkid 123454321 --nat extip:203.159.31.128 --unlock 0xCb1C9E26a6B65f35AC6F953aA453187daFe02422 --password password.txt
```

## Running the node with mining (PoA)

```bash
geth --datadir baengpun-chain --networkid 123454321 --nat extip:[IP-ADDRESS] --unlock [ACCOUNT] --password [password-for-keystore] --mine --miner.etherbase [ACCOUNT]
```

For example:

```bash
geth --datadir baengpun-chain --networkid 123454321 --nat extip:203.159.31.128 --unlock 0xCb1C9E26a6B65f35AC6F953aA453187daFe02422 --password password.txt --mine --miner.etherbase 0xCb1C9E26a6B65f35AC6F953aA453187daFe02422
```

## Joining the network

1. Copy the `genesis.json` file.
2. Create an account to run the node (take note of the public address):

```bash
geth account new --datadir data
geth init --datadir data genesis.json
```

3. Save password to `password.txt`.
4. Run the node with:

```bash
geth --datadir data --networkid 123454321 --unlock [Public Address] --password password.txt --bootnodes [Bootnode enode address] --http --http.port 8552 --http.addr 203.159.31.131 --http.api eth,net,web3,debug --allow-insecure-unlock
```

For example:

```bash
geth --datadir data --networkid 123454321 --nat extip:203.159.31.131 --unlock 0x3Eb0861d4cD52048D7570EF4733936cD94Bf00Bd --password password.txt --bootnodes enode://bde83bf822316dae4d659d1380de4645747e2979745c4c9c14ffd9a9fad6b450c52eb83dc167a44c3904e59f5391bfd274b1e8496dc454d9285a2061f8946d1b@203.159.31.128:30303 --authrpc.port 8553 --http --http.port 8552 --http.addr 203.159.31.131 --http.api eth,net,web3,debug --allow-insecure-unlock
```

5. `--http` allows for the node to be accessed via HTTP (e.g., using MetaMask wallet).
