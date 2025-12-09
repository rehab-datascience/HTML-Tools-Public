name: "🐞 Bug report / バグ報告"
description: "Something doesn't work as expected / 想定と異なる挙動"
labels: ["bug", "triage"]
body:
  - type: dropdown
    id: part
    attributes:
      label: "Which Part? / 対象パート"
      options:
        - Part 1 — Weekly 2-shift
        - Part 2 — Monthly 2-shift
        - Part 3 — Monthly 3-shift
        - Part 4 — Monthly 2-shift + Short
    validations: { required: true }

  - type: input
    id: version
    attributes:
      label: "Version/Commit"
      description: "Tag/commit or page URL used / 使用したタグ・コミット・URL"
      placeholder: "e.g., v0.1.3 or commit SHA / デモURL"
    validations: { required: false }

  - type: textarea
    id: repro
    attributes:
      label: "Steps to reproduce / 再現手順"
      description: "Numbered steps / 箇条書きで"
      placeholder: "1) Open page… 2) Input… 3) Click Generate…"
    validations: { required: true }

  - type: textarea
    id: inputs
    attributes:
      label: "Minimal inputs / 最小入力例"
      description: "Use dummy names; no PHI / 架空名で。個人情報は貼らないでください。"
      placeholder: |
        Month: 2025-12
        Need Day/Night: 2 / 1
        Staff(full): Alice, Bob
        Staff(short): Dana
        Requests:
          2025-12-03 Alice
    validations: { required: true }

  - type: textarea
    id: expected
    attributes:
      label: "Expected / 期待値"
      placeholder: "What you expected to see / 期待した結果"
    validations: { required: true }

  - type: textarea
    id: actual
    attributes:
      label: "Actual / 実際"
      placeholder: "What you actually saw / 実際の結果"
    validations: { required: true }

  - type: input
    id: env
    attributes:
      label: "Environment / 環境"
      placeholder: "OS, Browser & version / 例: Windows 11, Chrome 129"
    validations: { required: true }

  - type: checkboxes
    id: privacy
    attributes:
      label: "Privacy"
      options:
        - label: "No personal/clinical data included / 個人・臨床データは含みません" 
          required: true
