
# EC2

起動したインスタンスへの接続には秘密鍵（キーペア）が必要。

キーペアを作るとpem(秘密鍵)がDLされるのでこれを使ってログインする。

```
ssh -i "hoge.pem" ec2-user@fuga.ap-northeast-1.compute.amazonaws.com
```

