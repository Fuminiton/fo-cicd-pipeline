# コンテキスト
- 実行時の情報やジョブの実行結果を保持するオブジェクト
- 複数のプロパティで構成され、各プロパティから値を取得できる
## 使用例
```yml
name: Contexts
on: push
jobs: 
    print:
        runs-on: ubuntu-latest
        steps:
            - run echo "${{ github.actor }}" # github コンテキストの参照
```