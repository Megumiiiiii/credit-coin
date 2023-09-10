<div align="center">
 
# Credit Coin

</div>

<div align="center">

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23e609e6)](https://github.com/sponsors/Megumiiiiii)

[![](https://img.shields.io/static/v1?label=Telegram&message=%E2%9D%A4&logo=Telegram&color=%23e609e6)](https://t.me/KatouMegumii)

<img align="top" src="https://komarev.com/ghpvc/?username=Megumiiiiii&color=e609e6&style=plastic&label=Visitors" height='35'/>

</div>

#

<div align="center">
  
## ${\color{violet} COPAS \space SERTAIN \space SUMBER \space SU}$

### ${\color{violet} DIKIRA \space BIKIN \space GINIAN \space GAK \space PERLU \space USAHA \space APA}$ 

</div>

## Official Links
- [Docs](https://gluwa.gitbook.io/creditcoin-pos-testnet-documentation/validator-guides?ref=creditcoin.org)
- [Discord](https://discord.gg/creditcoin)
- [Twitter Gluwa](https://twitter.com/gluwa)
- [Twitter Credit Coin](https://twitter.com/Creditcoin)
- [Website Gluwa](https://gluwa.com)
- [Website Credit Coin](https://creditcoin.org)

#


### Install Docker (Jika belum) & Open Port
Port

```yml
ufw allow ssh; ufw allow 30333; ufw enable
```
Docker

```yml
sudo apt update; sudo apt upgrade -y
```

```yml
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```

### RUN!
>> Ganti `namaValidator` dengan nama mu dan `IP.VPS.MU` dengan IP VPS mu.

```yml
docker run -d \
 --name ctc \
 -p 30333:30333 \
 -v credit:/creditcoin-node/data  \
 gluwa/creditcoin:latest \
 --name "namaValidator" \
 --telemetry-url "wss://telemetry.creditcoin.network/submit/ 0" \
 --public-addr "/dns4/IP.VPS.MU/tcp/30333" \
 --chain main \
 --bootnodes "/dns4/bootnode.creditcoin.network/tcp/30333/p2p/12D3KooWAEgDL126EUFxFfdQKiUhmx3BJPdszQHu9PsYsLCuavhb" "/dns4/bootnode2.creditcoin.network/tcp/30333/p2p/12D3KooWSQye3uN3bZQRRC4oZbpiAZXkP2o5UZh6S8pqyh24bF3k" "/dns4/bootnode3.creditcoin.network/tcp/30333/p2p/12D3KooWFrsEZ2aSfiigAxs6ir2kU6en4BewotyCXPhrJ7T1AzjN" \
 --validator \
 --base-path /creditcoin-node/data \
 --port 30333
```

### Cek Logs

```yml
docker logs -f ctc
```

atau jika tidak ingin melihat logs terlalu banyak

```yml
docker logs ctc -f --since 10s
```

### Explorer
Pilih itu

<img width="839" alt="Screenshot_21" src="https://github.com/Megumiiiiii/credit-coin/assets/98658943/5059d29e-a184-4989-8d8a-861bbed4e190">



[Telemetry](https://telemetry.creditcoin.network/#list/0xdd954cbf4000542ef1a15bca509cd89684330bee5e23766c527cdb0d7275e9c2)

Jika namamu sudah ada disana = aman

## Aktifkan Validator

### Generate akun di vps atau gunakan akun testnetmu

#### Skip jika menggunakan akun testnet, langsung [Stake](https://github.com/Megumiiiiii/credit-coin#stake) saja

Generate 2 akun, lalu simpan pharse. Import ke [Subwallet](https://chrome.google.com/webstore/detail/subwallet-polkadot-wallet/onhogfjeacnfoofkfgppdlbmlmnplgbn)(extension)

```yml
docker exec -it ctc creditcoin-cli new
```


### Stake

```yml
docker exec -it ctc creditcoin-cli wizard -a 1000
```
`1000` bisa diganti berapapun, itu nominal yang akan di stake

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
>🪙  Amount to bond: 1000 CTC
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


Sudah, selanjutnya cek disini [PolkadotJS](https://polkadot.js.org/apps/?rpc=wss://rpc.mainnet.creditcoin.network/ws#/staking) Connect ke Subwallet, jika ada addressmu, tinggal menunggu aktif.

### Tambahan

#### Command lain-lain

```yml
docker exec -it ctc creditcoin-cli --help
```

#### Jika ingin memberi nama ke Validator

1. Pergi ke [Polkadot](https://polkadot.js.org/apps/?rpc=wss://rpc.mainnet.creditcoin.network/ws#/accounts)
2. Pilih wallet `stash` mu
3. Set identity dan atur display name
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/credit-coin/assets/98658943/dd2acb27-2eea-4076-8be6-b91e46e55e00"></p>

#### Mengatur Comission Rate

1. Pergi ke [Polkadot](https://polkadot.js.org/apps/?rpc=wss://rpc.mainnet.creditcoin.network/ws#/staking/actions) bagian Staking -> Account
2. Pilih Validator mu
3. Klik validate dan atur mau berapa commision rate
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/credit-coin/assets/98658943/4cfd09de-2a26-438f-b4dd-d90d8546d7fb">"></p>

### Delete Node

```yml
docker stop ctc; docker rm ctc
docker rmi gluwa/creditcoin:latest
```

#

<div id="header" align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMzNmZTIxZmE3ZmY3MzRiMDcwNDJhYTQ5ZmNlY2YxMWE1OWIyYmVkNSZlcD12MV9pbnRlcm5hbF9naWZzX2dpZklkJmN0PWc/mVBlqOD4ra9jQiI3cC/giphy.gif" height="125" width="420"/>
</div>
