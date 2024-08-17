# 環境変数
## 環境変数の定義と参照方法
```yml
name:  Environment variables
on: push
jobs:
    run:
        runs-on: ubuntu-latest
        env:
            BRANCH: main # ジョブレベルで環境変数を定義
        steps:
            - run: echo "${BRANCH}" # シェルコマンドからジョブレベルの環境変数を参照
            - uses: actions/checkout@v4
                with:
                    ref: ${{ env.BRANCH }} # envコンテキスト経由でジョブレベルの環境変数を参照
```
## VariablesとSecretsの利用
- リポジトリページのsettingsから設定する
- 以下使用例
```yml
name: Variables
on: push
jobs:
    print:
        runs-on: ubuntu-latest
        env:
            USERNAME: ${{ vars.USERNAME }} # Variablesの参照
        steps:
            - run: echo "${ USERNAME }"
```
```yml
name: Secrets
on: push
jobs:
    print:
        runs-on: ubuntu-latest
        env:
            PASSWORD: ${{ secrets.PASSWORD }} # Secretsの参照
        steps:
            - run: echo "${PASSWORD}" # ログ出力はマスクされる
            - run: echo "${PASSWORD:0:1}" ${PASSWORD#?} # ログ出力はマスクされない

```
