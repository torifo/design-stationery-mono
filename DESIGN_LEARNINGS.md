# BLANK STORE Design Learnings

## 目的

「シンプルな学生向け文房具サイト」というお題で、装飾を全て排除した状態でも店として成立する条件を確かめるための実装。装飾の節度を試す研究。

このブランドは架空店舗であり、実在の店舗・商品ではない。

## 設計したこと

- 色を白×黒×蛍光黄の3色だけに絞り、黄色の使用面積を意図的に小さく保った（ホバー時の下線、商品の差し色、引用部分のハイライト）
- 装飾は線と余白だけ。アイコンも極力 SVG のシルエットのみ
- ヘッダーロゴはブランド名＋黒い四角の最小表示
- カテゴリは 1px の境界線だけで分割し、ホバー時に黄色に染まる
- 商品6点の image-img は白＋極薄罫で十分

## CSS

```css
:root {
  --bg:#ffffff;
  --fg:#0a0a0a;
  --hi:#eaff00;
  --font:'DM Sans','Noto Sans JP',sans-serif;
}

/* nav の hover line */
nav a::after {
  height: 2px;
  background: var(--hi);
  transform: scaleX(0);
  transform-origin: right;
  transition: transform .3s;
}

/* category hover で全面が黄色になる */
.cat:hover { background: var(--hi) }

/* 引用の text-highlight */
.voice blockquote .hi {
  background: linear-gradient(transparent 60%, var(--hi) 60%);
}
```

ハードコードの色は使わず、すべて var() 経由。差し色1色のみで運用すると、色変更が真ん中1行で済む。

## アニメーション

- ホバー時の下線・色変化のみ。それ以外の reveal や parallax は一切なし
- 「装飾を増やさない」という方針をアニメーション設計にも適用

## フォント

- DM Sans 単一書体
- 日本語フォールバックは Noto Sans JP（system 標準寄り）
- セリフ系・装飾系・モノスペースは併用しない

## ボタン

ボタンは存在しない。ナビゲーション、カテゴリ、商品リンク、すべてテキストリンク扱い。

## UI/UX

- ナビ3項目（商品 / カテゴリ / 店）。フィルタもカートもない
- 「店主の一言」は中央寄せの大型引用1個だけ
- 店情報はフッターと別セクションに分割せず、`section.info` 1ブロックに集約

## レイアウト

`max-width: 1200px` の中央寄せレイアウトを全セクションに適用。グリッドは `repeat(auto-fill, minmax(220px, 1fr))` の素直な可変グリッド。

セクション間に区切り線を入れず、章タイトル下の `border-bottom` だけで「ここから新セクション」を示す。
