<p style="font-size:14px" align="right">
<a href="https://t.me/autosultan_group" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>
<p align="center">
  <img height="300" height="auto" src="https://user-images.githubusercontent.com/109174478/209359981-dc19b4bf-854d-4a2a-b803-2547a7fa43f2.jpg">
</p>

# Q-Blockchain Node Tutorial

## Install Node
```
wget -O q-blockchain.sh https://raw.githubusercontent.com/sipalingnode/Q-Blockchain/main/q-blockchain.sh && chmod +x q-blockchain.sh && ./q-blockchain.sh
```
## Create Password Wallet (usahakan yang mudah di ingat)
```
cd ~/testnet-public-tools/testnet-validator
nano keystore/pwd.txt
```
**Kemudian CTRL+X+Y Enter**
## Create Wallet
```
docker run --entrypoint="" --rm -v $PWD:/data -it qblockchain/q-client:testnet geth account new --datadir=/data --password=/data/keystore/pwd.txt
```
## Claim Faucet : https://faucet.qtestnet.org/
