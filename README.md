<p style="font-size:14px" align="right">
<a href="https://t.me/airdropasc" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
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
## Edit File .env
```
nano.env
```
<p align="center">
  <img height="300" height="auto" src="https://user-images.githubusercontent.com/109174478/210141136-bb9c05fd-5373-46da-9bc2-e6d91522e71b.jpg">
</p>

- QCLIENT_IMAGE = ganti dengan 1.2.2
- ADDRESS  = isi address kalian tanpa 0x 
- IP = isi IP VPS kalian 
- Dibawah BOOTNODE3 Tambahkan
```
BOOTNODE4_ADDR=enode://85d6f24920a0f552a5e0360366d18fb1234880c4370f257abc09e8ec762173fb3c4b1b14a7af9a23a8c31751b3ba2905d6a98fb436dfe3092644527a89046977@3.68.108.12:30303
BOOTNODE5_ADDR=enode://ec40af9079c53e880f7e783ae5053b18d1f8bb8cd55b2dfbbfa3b7e1f5256c724ef7e22f23f785c2f119fbb7930769540e3c01c711c6ae26c83690b941a4886c@85.215.92.83:30303
BOOTNODE6_ADDR=enode://1032c556fbbfe37761951a20c2b98b4031234a8f871cc79dd8ff612a3e0436afe3458b325d2f25617b62134cfc8a8a4885e80c9760ecb4bb7c8deaee67a098ae@95.217.169.172:30303
BOOTNODE7_ADDR=enode://e974d9354ababd356a6bfecbb03a59d14ab715ffa02d431c6accfc5de250e9c8c345817bd5687c119a04df78f1a4673e97877ea5775fa84270d311dac4a2eca7@128.199.213.70:30313
```
**Kemudian simpan CTRL+XY lalu ENTER**
## Edit File .json
```
nano config.json
```
<p align="center">
  <img height="300" height="auto" src="https://user-images.githubusercontent.com/109174478/210146288-05361ca5-7c75-4b88-95dc-7a60fe7c30c3.jpg">
</p>

- Address = Isi address kalian tanpa 0x
- Password = isi password yang dah dibuat, jika lupa pake command cek password `cat keystore/pwd.txt`

**Kemudian Simpan CTRL+XY lalu ENTER**
## Stake Contract
```
docker run --rm -v $PWD:/data -v $PWD/config.json:/build/config.json qblockchain/js-interface:testnet validators.js
```
## Daftar Validator
```
nano docker-compose.yaml
```
**Pada bagian setelah "geth" tambahkan**
```
"--ethstats=NAMA_VALIDATOR:TESTNET_ACCESS_KEY@stats.qtestnet.org",
```
**Nama_validator ganti nama kalian, Contoh Cek gambar**
<p align="center">
  <img height="300" height="auto" src="https://user-images.githubusercontent.com/109174478/210149630-76e72608-575e-41bb-b324-a22d8b26347e.jpg">
</p>

```
docker compose up -d
```
Cek Log Node
```
docker compose logs -f
```
**Jika mau stop log gunankan CTRL+Z**

Done. Cek node kalian : https://stats.qtestnet.org/
