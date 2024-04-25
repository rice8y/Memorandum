# 忘備録

- [XAMPPを利用してlocalhostでページを表示できない](#XAMPPを利用してlocalhostでページを表示できない)

## XAMPPを利用してlocalhostでページを表示できない

### Try. Apacheのポート設定を確認

xampp\apache\confにある httpd.conf を確認する. 

```
#Listen 12.34.56.78:80
Listen 80
```

ポート番号が80になっていた...   
今回の原因は, **設定ポート番号とブラウザに指定していたポート番号の不一致**であった.   
以下のように変更. 

```
#Listen 12.34.56.78:80
Listen 8080
```

改めて, http://localhost:8080 でアクセスする...   上手く表示された!!

### Reference   
> [【XAMPP】localhostでページ表示できない場合の原因・対処法](https://times-diary.hatenablog.com/entry/2017/08/19/090000)
