# ステップ間のデータ共有
## GITHUB_OUTPUT環境変数の利用
- 以下、使用例
    - GITHUB_OUTPUT環境変数へ、キーバリュー形式の文字列を書き出す
    - steps.<step-id>.outputs.<key>で参照する
```yml
name: GITHUB_OUTPUT
on: push
jobs:
    share:
        runs-on: ubuntu-latest
        steps:
            - id: source
                run: echo "result=Hello" >> ${GITHUB_OUTPUT} # GTIHUB_OUTPUTへ書き出し
            - env:
                RESULT: ${{ steps.source.outputs.result }}

```