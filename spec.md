# BLANK STORE — stationery/mono Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-23
**Updated:** 2026-05-23

---

## 1. Overview

### Problem Statement
学生向け文房具ECは「店ごとの個性」より「品揃えのパターン化」に陥りやすく、必要なものを最短で買う層に対しても、不要に装飾過多になりがち。シンプルかつ強い視覚アイデンティティの両立例が少ない。

### Goal
モノクローム＋ビビッド黄一色だけで構築した架空の文房具店「BLANK STORE」を実装し、「装飾ゼロ × 強い視覚記号」が成立する条件を検証する。

### Non-Goals
- カート / 決済
- 商品検索 / フィルタ
- 多言語対応

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 大学生〜社会人 | 何が売られているか即座に把握したい | 迷わず選べる |
| US-02 | 同上 | 装飾より商品を見たい | 余計な情報で疲れない |
| US-03 | 同上 | 信頼できる店であることを感じたい | リピートできる |

---

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | 白×黒×ビビッド黄のみの配色 | P0 |
| FR-02 | 商品 6 アイテム（SVG）| P0 |
| FR-03 | カテゴリ 4 区分 | P0 |
| FR-04 | 店主の一言（中央寄せ引用） | P1 |
| FR-05 | 店情報セクション | P0 |
| FR-06 | ヒーローに余白を多く取る | P0 |
| FR-07 | ナビホバー時のみ黄色のアンダーライン | P1 |
| FR-08 | モバイル対応（375px 基準） | P0 |

---

## 4. Key Design Decisions

| Decision | Chosen | Rationale | Rejected |
|----------|--------|-----------|----------|
| 配色 | 白×黒×蛍光黄 | 「最小限の装飾＋強い記号」のため | パステル多色 |
| 書体 | DM Sans | クセが少なく、可読性が高い | Inter（過剰に使われている） |
| 装飾 | 線のみ・余白 | テーマ「シンプル」の純粋形 | 写真背景・グラデ |
| ホバー演出 | 黄色アンダー1色 | アクセントの差し色を行動の合図にも転用 | ボタン拡大 |
| カートUI | 無し | 「店舗紹介＋来店誘導」に振り切る | EC化 |

---

## 5. Design System

```css
--bg:#ffffff;
--fg:#0a0a0a;
--muted:#6a6a6a;
--line:#dcdcdc;
--hi:#eaff00;        /* 唯一の差し色 */
--font:'DM Sans','Noto Sans JP',sans-serif;
```

---

## 6. References

- [navigator README](../README.md)
- Font: [DM Sans](https://fonts.google.com/specimen/DM+Sans)
