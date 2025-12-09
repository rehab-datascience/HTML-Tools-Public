---
name: Bug report
about: Create a report to help us improve
title: ''
labels: ''
assignees: ''

---

name: Bug report (Monthly 2-Shift)
description: 月次二交代版（CSV/ICS/検証CSV）での不具合報告
title: "[Bug] "
labels: ["bug"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        再現手順・期待結果・実際の結果をできるだけ具体的にご記載ください。
        **個人情報は書かない**でください（氏名はダミーに置換）。

  - type: checkboxes
    id: scope
    attributes:
      label: 対象機能（複数選択可）
      options:
        - label: 自動割当（Night→Day禁止 / 週・月上限 / 希望休）
        - label: CSV出力（schedule_monthly.csv）
        - label: ICS出力（shift_monthly_all.ics）
        - label: 検証CSV（validation_summary.csv）
        - label: UI / 表示（プレビュー・メッセージ・ボタン活性）

  - type: input
    id: month
    attributes:
      label: 対象月（YYYY-MM）
      placeholder: "2025-11"
    validations:
      required: false

  - type: textarea
    id: steps
    attributes:
      label: 再現手順
      description: 1行1手順でご記入ください
      placeholder: |
        1. 対象月を 2025-11 に設定
        2. 日勤=2 / 夜勤=1、週上限=2、月上限=6 を入力
        3. 職員リストと希望休を貼付
        4. 「シフト自動作成」をクリック
        5. 「検証CSVダウンロード」をクリック
    validations:
      required: true

  - type: textarea
    id: expected
    attributes:
      label: 期待結果
      placeholder: 例）上限違反0件、required_slots_filled_pct=100%
    validations:
      required: true

  - type: textarea
    id: actual
    attributes:
      label: 実際の結果
      placeholder: 例）weekly_night_cap_violationsが想定より多い、夜勤翌日の日勤が発生 等
    validations:
      required: true

  - type: textarea
    id: sample
    attributes:
      label: 最小サンプル（任意）
      description: 個人情報は削除し、**最小化した入力例**を貼り付けてください
      placeholder: |
        # staff
        田中
        鈴木
        佐藤
        ...
        # requests (YYYY-MM-DD 氏名)
        2025-11-03 田中
        2025-11-08 鈴木

  - type: checkboxes
    id: browsers
    attributes:
      label: 動作環境
      options:
        - label: Chrome（バージョン記載）
        - label: Edge
        - label: Safari
        - label: Firefox
        - label: Windows
        - label: macOS
        - label: iOS
        - label: Android

  - type: textarea
    id: screenshots
    attributes:
      label: スクリーンショット / 画面録画（任意）
      description: エラーメッセージや異常箇所があれば添付
