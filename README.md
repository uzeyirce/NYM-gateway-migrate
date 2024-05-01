
# <h1 align="center">![nym logo](https://github.com/uzeyirce/Nimble/assets/85512132/9a8e16a1-54b7-4949-9258-df37dbb5f4f9)</h1>

# <h1 align="center">NYM GATEWAY MIGRATE</h1>

* [Twitter](https://twitter.com/nymproject)
* [Discord](https://discord.gg/nym)
* [Website](https://nymtech.net/)
* [Docs](https://nymtech.net/operators/nodes/nym-node.html)


*Çalışan bir gateawayınız varsa migrate işlemi yapmanız gerekmektedir.

*Uyarı: Bu yönerge SYSTEMD kurmuş olan kişiler için rehber niteliğindedir. 

*Daha fazla bilgi için üstteki resmi dökümandan bilgi alabilirsiniz.





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


3. Servisi durduralım.

```bash
sudo systemctl stop gateway
```


4. Migrate işlemi yapacağımız nym-node dosyasını indirelim.
   

```bash
wget https://github.com/nymtech/nym/releases/download/nym-binaries-v2024.3-eclipse/nym-node
```

5. Erişim izni verelim.

```bash
chmod +x nym-node
```



```bash
curl
```



```bash
curl
```



```bash
curl
```



```bash
curl
```
