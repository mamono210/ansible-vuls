# ansible-vulsについて

このPlaybookはCentOS7へ [Vuls](https://github.com/future-architect/vuls) をインストールします。

# Ansibleをインストールする

rootで以下のコマンドを実行します。
   
``` 
yum -y install epel-release
yum -y install ansible
ansible --version
```

# Vulsをインストールする

localhostでrootで以下のコマンドを実行します。

```    
useradd vuls
cd /home/vuls
git clone https://github.com/TomonoriMatsumura/ansible-vuls.git
cd ansible-vuls
ansible-playbook -i localhost.cfg site.yml
```

# vars ファイルについて

vars/default.ymlにて以下の値を設定しています。適宜変更してください。

```
work_dir: /tmp/vuls-install-dir
vuls_user: vuls
go_path: "/home/{{ vuls_user}}/go"

first_year: 2018
```

<dl>
  <dt>work_dir</dt>
  <dd>作業用ディレクトリ</dd>

  <dt>vuls_user</dt>
  <dd>Vulsを実行するユーザー名</dd>

  <dt>go_path</dt>
  <dd>Golangのインストールパス</dd>

  <dt>first_year</dt>
  <dd>脆弱性ファイルを取得するための期間を設定します。期間の最初のみ指定出来ます。期間の終わりの年はPlaybook側で自動で取得されます。

初期設定は2018年～2018年になっています。（2018年現在）この値を適宜変更します。2016年～現在の年くらいの約3年間程度の設定が妥当かと思われます。</dd>
