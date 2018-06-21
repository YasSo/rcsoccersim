## Docker for Mac 用の RoboCup 2D Simulator 実行環境

Homebrew (https://brew.sh/) が入っていない場合はインストールしておく。

Docker が入ってない場合は Homebrew (Cask) で Kitematic と共にインストールしておく。
~~~console
(host)$ brew cask install docker kitematic
~~~

始めに XQuartz と socat をインストールしておく。
XQuartz をインストールした後は，再起動しておいた方が良さそう。
~~~console
(host)$ brew cask install xquartz
(host)$ brew install socat
~~~

XQuartz を起動し，RoboCup Simulator のビューアアプリを XQuartz で表示できるように socat コマンドを実行しておく。
~~~console
(host)$ open -a XQuartz
(host)$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" &
~~~

Kitematic などを使って rcsoccersim コンテナを起動する。
→ この時点では rcssserver が起動するだけで何も表示されない。

> rcsoccersim コンテナを起動する際には logs と teams のボリュームを指定しておくこと。logs ボリュームが指定されていないと rcssserver は起動できない。

Kitematic で EXEC ボタンを押してシェルを開き soccerwindow2 か rcssmonitor を起動する。
~~~console
(container)$ soccerwindow2 &
~~~

https://archive.robocup.info/Soccer/Simulation/2D/binaries/RoboCup/ からチームバイナリをダウンロードして teams フォルダに入れておく。

2つのチームのバイナリを起動する。（以下，起動例）
~~~console
(container)$ pwd
/home/rcsoccersim/teams
(container)$ cd 2017/alice/
(container)$ ./s &
(container)$ cd ../cyrus/
(container)$ ./startAll &
~~~
