# wsl-alma-docker
	このリポジトリを任意の場所にcloneしてください。
	この例では
	c:\wsl\repository\dev-default
	というディレクトリを作成し、その中に本リポジトリの内容をCloneした場合の例を提示していきます。
	※wsl-alma-dockerというDirは作成されないようにCloneしてます。
	
# 設定済みユーザー dockerはsudoなしで実行可能
## [user]
	developer
## [pass]
	developer
# SETUP
## 事前の確認
	wsl --version
	↑が実行できない場合は下記
	wsl -l
	も実行できない場合は、コンパネからWSLを有効化する
	wsl --update
	もしくは
	https://apps.microsoft.com/detail/9p9tqf7mrm4r?hl=ja-jp&gl=JP
	ここから最新のWSLをinstall
	
	コンパネから有効化したら下記を実行
	wsl --install --no-distribution
	対話にはyes
	※再起動が走ります。

## Image作成起動
	wsl --import AlmaDocker c:\wsl\alma-docker c:\wsl\repository\dev-default\alma-docker.tar
	とか
	wsl --import Test c:\wsl\test c:\wsl\repository\dev-default\alma-docker.tar
## ホストマシンのファイルにアクセスするには
	cd /mnt/
	でホストマシンをマウントしているような形です。Cドライブに諸々保存している場合
	/mnt/c/Users/{ユーザー名}/{projectまでのPath}
	とかでアクセスできます。
## docker
	上記のように、ホストマシン上のproject直下まで移動し、そこにdocker-compose.ymlなどがある場合
	docker-compose up -d 
	を実行することで即座に開発環境がたちあがります。
	VirtualBoxと比べて動作が早め、Macユーザーとも割と近しい状況になるかと思います。

# tips
## リスト確認
	wsl -l -v

## image削除
	wsl --unregister AlmaDocker

## 起動
	wsl -d AlmaDocker

## シャットダウン
	wsl --shutdown
##  指定して止める
	wsl -t AlmaDocker

## エクスポート 
	wsl --export AlmaDocker  c:\tmp\alma-docker.tar


## Docker-cmpose試したい人用↓
	https://github.com/yuichi-sano/laravel-2024
	https://github.com/yuichi-sano/vue-vite-sample-2024

	上記をWindows上の任意の場所にCloneし。WSLから該当のポイントまで移動したうえで
	docker-compose up -d

 