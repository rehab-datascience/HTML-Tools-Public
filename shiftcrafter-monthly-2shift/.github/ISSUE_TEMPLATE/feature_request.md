---
name: Feature request
about: Suggest an idea for this project
title: ''
labels: ''
assignees: ''

---

name: Feature request (Monthly 2-Shift)
description: 月次二交代版への機能追加・改善提案
title: "[Feature] "
labels: ["enhancement"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        実運用シナリオと「なぜ必要か」を書いていただけると優先度を判断しやすいです。

  - type: input
    id: motivation
    attributes:
      label: 目的 / 課題
      placeholder: 例）特定の曜日だけ夜勤必要人数を増やしたい
    validations:
      required: true

  - type: textarea
    id: proposal
    attributes:
      label: 提案内容（UI/仕様）
      placeholder: |
        例）
        - 画面左に「日別必要人数」テキストエリアを追加
        - フォーマット：YYYY-MM-DD need_day need_night
        - 空行は無視、未指定日は全日共通の数値を使用
    validations:
      required: true

  - type: checkboxes
    id: outputs
    attributes:
      label: 影響範囲（複数選択可）
      options:
        - label: 自動割当ロジック
        - label: CSV出力（wide/long）
        - label: ICS出力（勤務時刻/タイトル表記）
        - label: 検証CSV（指標の追加・変更）
        - label: UI（入力/プレビュー/バリデーション）

  - type: textarea
    id: acceptance
    attributes:
      label: 受け入れ条件（達成基準）
      placeholder: |
        例）
        - 指定日の need_day/need_night が割当に反映される
        - required_slots_filled_pct が 100% を維持
        - 既存MVPのNight→翌Day禁止が維持される
    validations:
      required: false

  - type: textarea
    id: additional
    attributes:
      label: 参考（任意）
      description: 競合事例・スクショ・関連Issue/PRなど
