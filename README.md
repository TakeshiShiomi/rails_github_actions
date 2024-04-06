# github actions 使い方(rails)

- github の actions へ行き、ruby on rails を選択するとテンプレートがあるのでそちらを利用する。
  他のプログラミングやフレームワークの場合は適宜変更する

- 必要な gem を入れる or github actions の yml ファイルから不必要な実行を消す

### yml ファイル内について

github actions の設定ファイルは、.github/workflows/ディレクトリに配置する。
on:
push:
branches: ["main", "develop"]
pull_request:
branches: ["main", "develop"]
で実行するブランチを指定できる。すべてのブランチで実行する場合は branches をコメントアウトする。

name: は、GitHub Actions の画面で表示されるジョブの名前。わかりやすい名前をつけると良い。
run: は、ジョブの実行内容を記述する。コマンドを記述する。
on: は、ジョブを実行するタイミングを指定する。push, pull_request, schedule, workflow_dispatch などが指定できる。
jobs: は、ジョブの設定を記述する。複数のジョブを記述することができる。
runs-on: は、ジョブを実行する環境を指定する。ubuntu-latest, ubuntu-20.04, ubuntu-18.04, windows-latest, windows-2019, macos-latest, macos-10.15 などが指定できる。

#### 今回作成で気づいたこと

- GitHub Actions の実行環境で使用されている Ruby のバージョン指定すること

```yml
- name: Install Ruby and gems
  uses: ruby/setup-ruby@55283cc23133118229fd3f97f9336ee23a179fcf # v1.146.0
  with:
    ruby-version: 3.2.0 #この箇所
    bundler-cache: true
```

プロジェクトに合わせて適宜編集しましょう
