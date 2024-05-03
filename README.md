
# <h1 align="center">![nym logo](https://github.com/uzeyirce/Nimble/assets/85512132/9a8e16a1-54b7-4949-9258-df37dbb5f4f9)</h1>

# <h1 align="center">NYM GATEWAY MIGRATE</h1>

* [Twitter](https://twitter.com/nymproject)
* [Discord](https://discord.gg/nym)
* [Website](https://nymtech.net/)
* [Docs](https://nymtech.net/operators/nodes/nym-node.html)


*Çalışan bir gateawayınız varsa migrate işlemi yapmanız gerekmektedir.

*Uyarı: Bu yönerge SYSTEMD kurmuş olan kişiler için rehber niteliğindedir. 

*Daha fazla bilgi için üstteki resmi dökümandan bilgi alabilirsiniz.

* önemli not NYM dosyanız hangi klasörde ise o klasörün içinde işlemleri yapmanız gerekmektedir. Benim dosyalarım ROOT da olduğu için direk orada işlemleri gerçekleştirdim.
![4](https://github.com/dymensionxyz/networks/assets/85512132/80e2b118-c31e-4ff0-8ed7-aa64cb29041e)


1. Öncelikle scripti indirelim.

```bash
curl -o network_tunnel_manager.sh -L https://gist.githubusercontent.com/tommyv1987/ccf6ca00ffb3d7e13192edda61bb2a77/raw/9d785d6ee3aa2970553633eccbd89a827f49fab5/network_tunnel_manager.sh && chmod +x network_tunnel_manager.sh
```

![1](https://github.com/uzeyirce/Nimble/assets/85512132/03961d32-5d03-4048-aac2-336e59b97de1)


2. Gateaway durumunu kontrol edelim. Görüntü aşağıdaki gibi ise işleme  devam edebilirsiniz. Statusten çıkmak için CTRL + C ile işlemi durduralım.
```bash
sudo systemctl status gateway
```

![2](https://github.com/uzeyirce/Nimble/assets/85512132/15fdd084-4d15-47eb-ae28-2f9324c309ab)

CTRL C ile durduralım.

3. Servisi durduralım.

```bash
sudo systemctl stop gateway
```


4. Migrate işlemi yapacağımız nym-node dosyasını indirelim.
   

```bash
wget https://github.com/nymtech/nym/releases/download/nym-binaries-v2024.3-eclipse/nym-node
```
![3](https://github.com/dymensionxyz/networks/assets/85512132/ddb15137-a941-4a05-ba1f-10b0ec73e8cb)

5. Erişim izni verelim.

```bash
chmod +x nym-node
```

6. Configfile dosyasını migrate yapalım. GATEWAY-ID kısmına kendi ID nizi yazın.
örnek: ./nym-node migrate --config-file ~/.nym/mixnode/uzo/config/config.toml mixnode

```bash
./nym-node migrate --config-file ~/.nym/gateways/<GATEWAY_ID>/config/config.toml gateway
```

7.nym-node service dosyasını açalım.

```bash
nano /etc/systemd/system/nym-node.service
```
İçine aşağıdaki bilgileri kopyalayalım. <GATEWAY_ID> değiştirmeyi unutmayalım.


```bash
[Unit]
Description=Nym Node
StartLimitInterval=350
StartLimitBurst=10

[Service]
User=root
LimitNOFILE=65536
ExecStart=/root/nym-node run --mode exit-gateway --id <GATEWAY_ID> --deny-init
KillSignal=SIGINT
Restart=on-failure
RestartSec=30

[Install]
WantedBy=multi-user.target
```
CTRL X ile çıkalım. 
Y dedikten sonra Enter tuşu ile kaydedelim.


8. Servis kontrolllerini yapalım sırasıyla.

```bash
./network_tunnel_manager.sh check_nymtun_iptables
```


```bash
./network_tunnel_manager.sh fetch_and_display_ipv6
```

```bash
./network_tunnel_manager.sh apply_iptables_rules
```

```bash
./network_tunnel_manager.sh fetch_and_display_ipv6
```

```bash
systemctl enable nym-node.service
```

```bash
systemctl daemon-reload
```


```bash
service nym-node start && journalctl -u nym-node -f -n 100
```



bütün değerler valid olmalı
```bash
ip addr show nymtun0
```


Komut sonrası iki şaka vermeli.
```bash
./network_tunnel_manager.sh joke_through_the_mixnet
```

ID key ve Spnix Key bilgilerini alalım.
```bash
./nym-node bonding-information --id <GATEWAY ID>
```


NYM WALLETTA GİDİP VERSİON 1.1.0 yazıyoruz ve imzalıyoruz. 

BİTTİ



































