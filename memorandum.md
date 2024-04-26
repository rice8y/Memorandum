# 忘備録

- [XAMPPを利用してlocalhostでページを表示できない](#XAMPPを利用してlocalhostでページを表示できない)
- [XAMPPを利用してローカル環境でメール送信したい](#XAMPPを利用してローカル環境でメール送信したい)

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

## XAMPPを利用してローカル環境でメール送信したい

### Try. 以下の手順で設定ファイルを修正
#### 1. PHPの設定ファイル(C:\xampp\php\php.ini)の修正

修正内容：

```
[mail function]
SMTP = localhost
smtp_port = 25
sendmail_path = "\"C:\xampp\sendmail\sendmail.exe\" -t"
mail.add_x_header = Off
```
   
#### 2. sendmailの設定ファイル(C:\xampp\sendmail\sendmail.ini)の修正

修正内容：

```
[sendmail]
smtp_server=smtp.mydomain.com
smtp_port=465
smtp_ssl=auto
auth_username=hogehoge@mydomain.com
auth_password=hogehoge
force_sender=hogehoge@mydomain.com
```

#### 3. Apacheの再起動

### Reference
> [【XAMPP】ローカル開発環境でメール送信をできる様にする](https://miya-system-works.com/blog/detail/xampp-send-mail/#:~:text=%E3%80%90XAMPP%E3%80%91%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%81%A7%E3%83%A1%E3%83%BC%E3%83%AB%E9%80%81%E4%BF%A1%E3%82%92%E3%81%A7%E3%81%8D%E3%82%8B%E6%A7%98%E3%81%AB%E3%81%99%E3%82%8B%201%20STEP1.%20PHP%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E7%B7%A8%E9%9B%86%E3%81%99%E3%82%8B%20%E3%81%9D%E3%82%8C%E3%81%A7%E3%81%AF%E4%BB%8A%E5%9B%9E%E3%81%AE%E4%BD%9C%E6%A5%AD%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6%E8%A7%A3%E8%AA%AC%E3%82%92%E8%A1%8C%E3%81%84%E3%81%BE%E3%81%99%E3%80%82%20...%202%20STEP2.,PHP%E3%83%BBsendmail%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E4%BF%AE%E6%AD%A3%E3%81%8C%E7%B5%82%E3%82%8F%E3%81%A3%E3%81%9F%E3%82%89%20%E6%9C%80%E5%BE%8C%E3%81%ABApache%E3%81%AE%E5%86%8D%E8%B5%B7%E5%8B%95%20%E3%82%92%E8%A1%8C%E3%81%84%E3%81%BE%E3%81%99%E3%80%82%20...%204%20STEP4.%20%E3%83%A1%E3%83%BC%E3%83%AB%E3%81%8C%E9%80%81%E4%BF%A1%E3%81%A7%E3%81%8D%E3%82%8B%E3%81%8B%E7%A2%BA%E8%AA%8D%E3%81%99%E3%82%8B%20)
