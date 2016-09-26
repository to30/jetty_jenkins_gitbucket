# README
/optの下にansibleフォルダを作成し、その下にこれらのファイルを配置してください。  

## このプレイブックで構築されるもの
ユーザ（jetty）とグループ（jetty）  
java (Oracle JDK)  
Jetty (APサーバ)  
Gitbucket(jettyにデプロイ)  
Jenkins(jettyにデプロイ)  

## 構築環境に合わせて変更が必要なもの  
ansible.cfg    -> リモートユーザ名と鍵の情報を修正  
JMXポート　　　-> group_varsのgy01グループでは12345
                  host_varsのe-gy01-jetty01では1099で設定
site.yml       -> 構築設定関連（あるべき姿）はこっち
site2.yml      -> べきとう性の不要なスポット作業　障害対応/アカウント追加 運用時に一時的に必要な作業はこっち
               -> アプリのデプロイなんかもこっちか？



## 実行方法
確認
ansible-playbook -i library/zabbix.py -l e-gy01-jetty01.vmtest.local site.yml --list-tasks --list-hosts
実行
ansible-playbook -i library/zabbix.py -l e-gy01-jetty01.vmtest.local site.yml

## 動作確認
http://IPアドレス:8080/gitbucket/  
http://IPアドレス:8080/jenkins/  
jconsoleにてIPアドレス:1099

## 残課題
JAVA_HOME設定もれ  
javaのバージョンが固定されているが変数にするべきだった 
JMXのセキュリティ設定
 
