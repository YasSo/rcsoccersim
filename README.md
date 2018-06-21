## Docker for Mac 用の RoboCup 2D Simulator 実行環境

~~~shell
$ brew install socat
$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" &
$ brew cask install xquartz
$ open -a XQuartz
~~~

Kitematic などを使って rcsoccersim コンテナを起動する → rcssserver が起動するだけ

（logs と teams のボリュームを指定しておく）

Kitematic で EXEC ボタンを押してシェルを開き soccerwindow2 か rcssmonitor を起動する

~~~shell
$ soccerwindow2 &
~~~

https://archive.robocup.info/Soccer/Simulation/2D/binaries/RoboCup/ からチームバイナリをダウンロードして teams フォルダに入れておく

2つのチームのバイナリを起動する（以下，起動例）

~~~shell
# cd 2017/alice/
# ./s &
# cd ../cyrus/
# ./startAll &
~~~
