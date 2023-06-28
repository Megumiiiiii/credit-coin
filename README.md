# Credit Coin

<div id="header" align="center">
  <img src="https://media.giphy.com/media/aXE4aGVPDs1pGcm0y4/giphy.gif" height="338" width="600"/>
</div>

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

## Guide akan di update setelah faucet masuk
