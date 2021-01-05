# react-hanson

## create-react-app

まずは上記のコマンドを使って、Reactアプリのひな形を作成する。
※コンテナ内の`/code`に作成されるが、ホストマシンのカレントディレクトリに追加される。

```
├── Dockerfile.dev
├── README.md
├── docker-compose.yaml
└── hanson-app
    └── ***
```

```
docker run --rm -it -w="/code" -v $(pwd):/code  node:14.15.3-alpine3.10 /bin/sh
```

コンテナ内で`create-react-app`コマンドを実行する。  
※5分くらいかかる。  

```
npx create-react-app hanson-app
```

このコマンドの実行が終わると、ホストマシン上のこのディレクトリに`hanson-app`ができている。  
このディレクトリの中にReactのアプリのひな形ができているため、これを編集していく。  

## アプリの起動
`docker-compose.yaml`に実行に関する環境を作成している。  
そのため、以下のコマンドを実行するだけで良い。  

```
docker-compose up
```

実行すると、以下のようにReactアプリが起動するため、ブラウザでアクセスできる。  

```
web_1  | yarn run v1.22.5
web_1  | $ react-scripts start
web_1  | ℹ ｢wds｣: Project is running at http://192.168.32.2/
web_1  | ℹ ｢wds｣: webpack output is served from
web_1  | ℹ ｢wds｣: Content not from webpack is served from /code/public
web_1  | ℹ ｢wds｣: 404s will fallback to /
web_1  | Starting the development server...
web_1  |
web_1  | Compiled successfully!
web_1  |
web_1  | You can now view hanson-app in the browser.
web_1  |
web_1  |   Local:            http://localhost:3000
web_1  |   On Your Network:  http://192.168.32.2:3000
web_1  |
web_1  | Note that the development build is not optimized.
web_1  | To create a production build, use yarn build.
web_1  |
```

ユニットテストなどを実行する時は、コンテナの中に入って行う事もできる。  

```
docker-compose exec web /bin/sh
yarn test
```
