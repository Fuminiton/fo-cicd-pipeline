# ジョブ間のデータ共有
```yml
name: Share job data
on: push
jobs:
    before:
        runs-on: ubuntu-latest
        steps:
            - id: generate
            run: echo "result=HELLO" >> "${GITHUB_OUTPUT}" # ステップレベルの出力値
        outputs:
            result: ${{ steps.generate.outputs.result }} # ジョブレベルの出力値
    after:
        runs-on: ubuntu-latest
        needs: [before]
        steps:
            - env:
                RESULT: ${{ needs.before.outputs.result }}
            run: echo "${RESULT}"
```