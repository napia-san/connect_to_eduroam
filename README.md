# connect_to_eduroam
raspberry piをeduroamに接続する方法（備忘録）

最新版のraspberry pi OSではeduroamに接続できないようです．<br>
そこで，wpa_supplicantをダウングレードすることによって接続を試みます．<br>
＊自己責任で行ってください．

## Useage
イーサネットもしくは，接続可能なWiFiを使ってインターネットに接続し，当リポジトリ内のシェルスクリプトを実行します．

次にネットワークの接続情報を設定します．<br>
ターミナルで以下のコマンドを入力し，エディタを起動します．<br>
```
$ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
以下を追加して，変更を保存します．
```
network={
         ssid="eduroam"
         scan_ssid=1
         key_mgmt=WPA-EAP
         eap=PEAP
         identity="eduroamのID"
         anonymous_identity="eduroamのID"
         password="eduroamのパスワード"
         phase1="peaplabel=auto peapver=auto"
         phase2="auth=MSCHAPV2"
}
```
`$ sudo reboot`で再起動します．
