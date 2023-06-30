# Credit Coin

<div id="header" align="center">
  <img src="https://media.giphy.com/media/aXE4aGVPDs1pGcm0y4/giphy.gif" height="338" width="600"/>
</div>

#

## Official Links
- [Docs](https://gluwa.gitbook.io/creditcoin-pos-testnet-documentation/validator-guides?ref=creditcoin.org)
- [Discord](https://discord.gg/creditcoin)
- [Twitter](https://twitter.com/gluwa)
- [Website](https://gluwa.com)

#


### Install Docker (Jika belum) & Ope Port
Port

```yml
ufw allow ssh; ufw allow 30333; ufw enable
```
Docker

```yml
sudo apt update; sudo apt upgrade
```

```yml
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```

### Buat folder untuk menampung data

```yml
cd
mkdir credit
```

### RUN!
>> Ganti `namaValidator` dengan nama mu dan `IP.VPS.MU` dengan IP VPS mu.

```yml
docker run -d \
 --name creditcoin-validator \
 -p 30333:30333 \
 -v credit:/creditcoin-node/data  \
 gluwa/creditcoin:2.222.2-testnet \
 --name "namaValidator" \
 --telemetry-url "wss://telemetry.creditcoin.network/submit/ 0" \
 --public-addr "/dns4/IP.VPS.MU/tcp/30333" \
 --chain test \
 --bootnodes "/dns4/testnet-bootnode.creditcoin.network/tcp/30333/p2p/12D3KooWG3eEuYxo37LvU1g6SSESu4i9TQ8FrZmJcjvdys7eA3cH" "/dns4/testnet-bootnode2.creditcoin.network/tcp/30333/p2p/12D3KooWLq7wCMQS3qVMCNJ2Zm6rYuYh74cM99i9Tm8PMdqJPDzb" "/dns4/testnet-bootnode3.creditcoin.network/tcp/30333/p2p/12D3KooWAKUrvmchoLomoouoN1sKfF9kq8dYtCVFvtPuvqp7wFBS" \
 --validator \
 --base-path /creditcoin-node/data \
 --port 30333 
```

### Cek Logs

```yml
docker logs -f creditcoin-validator
```

### Explorer
Pilih itu

<img width="839" alt="Screenshot_21" src="https://github.com/Megumiiiiii/credit-coin/assets/98658943/b11e7630-0e9c-4b46-b878-6ef38699fdb5">


https://telemetry.creditcoin.network/#list/0xc2e43792c8acc075e564558f9a2184a0ffe9b0fd573969599eee9b647358c6cf

Jika namamu sudah ada disana = aman

## Aktifkan Validator

### Generate akun di vps 
Generate 2 akun, lalu simpan pharse. Import ke polkadot.js(extension)

```yml
docker exec -it creditcoin-validator creditcoin-cli new
```

Lalu kirim token dari faucet lewat [Polkadotjs](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.creditcoin.network%2Fws#/accounts) ke akun pertama, 14600 atau berapa terserah. Dan kirim ke akun kedua 100

### Lanjut stake

```yml
docker exec -it creditcoin-validator creditcoin-cli wizard -a 14000
```
`14000` bisa diganti berapapun, itu nominal yang akan di stake

Untuk `stash` isi dengan pharse akun pertama, dan `controller` isi dengan pharse akun kedua

Output yang benar:


>🧙 Running staking wizard...
>
>Using the following parameters:
>
>💰 Stash account: 5CGBosx2Fw34u9jJtSgEQkoNTtHkPLKgsfjJiE3mDSWb44MW
>
>🕹️  Controller account: 5E1tpiU3SnunxwbtvTc7U7gykNYspTZu9yqTcch2pHamAvw5
>
>🪙  Amount to bond: 10000 CTC
>
>🎁 Reward destination: Staked
>
>📡 Node URL: ws://127.0.0.1:9945📡 Node URL: ws://127.0.0.1:9945
>
>💸 Commission: 0
>
>🔐 Blocked: No
>
>Continue? (y/n): y


Sudah, selanjutnya cek disini https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.creditcoin.network%2Fws#/staking Jika ada addressmu, tinggal menunggu aktif.

#

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/Megumiiiiii)

#

<div id="header" align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMzNmZTIxZmE3ZmY3MzRiMDcwNDJhYTQ5ZmNlY2YxMWE1OWIyYmVkNSZlcD12MV9pbnRlcm5hbF9naWZzX2dpZklkJmN0PWc/mVBlqOD4ra9jQiI3cC/giphy.gif" height="125" width="420"/>
</div>
