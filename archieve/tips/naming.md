# ネーミング
- ログの読みやすさ、探しやすさのためにステップ名やワークフロー実行名にも配慮すべき

```yml
name: Naming
run-name: Run by @${{ github.actor }} # ワークフロー実行名の指定
on: push
jobs:
    print:
        name: Super Userful Job # ジョブ名
        runs-on: ubuntu-latest
        steps:
            - name: Amazon Script # ステップ名の指定
            run: echo "Hello"
```