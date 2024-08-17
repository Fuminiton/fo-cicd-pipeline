# 起動方法の整理
## 手動実行定義 + GitHub CLI
```sh
gh workflow run manual.yml -f greeting=goodbye
```

## choice型による列挙値の指定
```yml
inputs:
    log-level:
        type: choice # 入力パラメータを特定の値に制限
        options: # 受け付ける入力値を列挙
            - info
            - warm
            - error
```
## 定期実行
```yml
name: Schedule
on:
    schedule: # 定期実行イベント
        - cron: '*/15 * * * *' # 15分ごとに起動するcron式
jobs:
    run:
        runs-on: ubuntu-latest
        steps:
            - run: date
```