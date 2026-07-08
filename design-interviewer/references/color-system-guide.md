# color-system-guide.md — カラー設計ガイド（役割ベース）

## 概要

Phase 7 で使う。色は「好み」でなく「役割」で設計する。「青が好き」ではなく「PrimaryはNavy、AccentはCyanを1つだけ」と言い切れる状態にする。色名だけで提案せず、必ずColor Roleに分けて提示する。カラー提案の直前に必ず読む。

- **向いている用途**: LP・画面案のカラーパレット、デザイントークン、UI状態設計、3案の違いの説明。
- **向いていない用途**: 「青が好き」など好みだけの議論、ブランド色で全UI状態を上書きする設計。

## 中心思想

- 重要度は色ではなく、サイズ・位置・余白・密度で表現する。色は最後の一押し。
- ブランド色（Primary/Accent）と、意味を持つ状態色（Error/Success/Warning/Info）を混ぜない。
- 色数は少ないほど強い。増やすほど優先順位が消える。

## Color Role（必ずこの役割で設計する）

| Role | 役割 | 目安 |
|---|---|---|
| Primary | ブランドの主色。ヘッダー・主要導線・リンクの基調 | 1色 |
| Secondary | Primaryを補助し、情報の区分に使う準主色（無くてもよい） | 0〜1色 |
| Accent | CTA・注目箇所に使う唯一の強調色 | **1色のみ** |
| Background | ページ地。基本は白/オフホワイト or ダーク | 1色 |
| Surface | カード・パネル・モーダルなど地より一段手前の面 | 1〜2段階 |
| Text | 本文の主文字色。純黒より少し落とす | 1色 |
| Muted Text | 補助説明・キャプション・メタ情報・非活性の文字 | 1色 |
| Border | 区切り線・枠・入力欄。主張させない薄い色 | 1色 |
| Error | エラー・危険・破壊的操作 | 標準の赤系 |
| Success | 成功・完了・正常 | 標準の緑系 |
| Warning | 注意・未完了・要確認 | 標準の橙/琥珀系 |
| Info | 補足・案内・中立の通知 | 標準の青系 |

## 提案フォーマット（この形で出す）

単に「青がよい」ではなく、役割で列挙する:

```
Primary:     Navy (#1E293B)
Secondary:   Slate (#334155)  ※任意
Accent:      Cyan (#06B6D4)   ※CTAはこの色のみ
Background:  Off White (#F8FAFC)
Surface:     White (#FFFFFF)
Text:        Charcoal (#0F172A)
Muted Text:  Slate Gray (#64748B)
Border:      Light Gray (#E2E8F0)
Error:       Red (#DC2626)
Success:     Green (#16A34A)
Warning:     Amber (#D97706)
Info:        Blue (#2563EB)
```

※値は例。テーマに応じて置き換える。ダークUIならBackground/Surface/Textを反転設計する（後述のとおり単純反転ではない）。

## 判断基準（役割ごとの決め方）

- **Primary**: ターゲットに与えたい感情から選ぶ（信頼=Navy/Deep Blue、誠実=Deep Green、上質=Ink/Burgundy、活気=暖色）。
- **Accent**: Primaryと十分に差がつき、かつ状態色（赤緑橙）と混同しない色。CTAだけに使うと決め、CTAが一目で分かるか確認する。
- **Background/Surface**: 明るさに2〜3段階の階層（地→面→浮いた面）を作る。純白と純黒は避け、僅かに寄せる。
- **Text/Muted Text**: 通常本文は背景とのコントラスト比 **4.5:1 以上**、見出し・大きい文字でも 3:1 以上を確保。
- **状態色**: 意味が固定なので、ブランドに合わせて色相を大きく動かさない。特に赤緑は色覚多様性に配慮し、色だけに意味を頼らずアイコン/文言を併用。

## ケース別の推奨パターン

Primary / Accent の方向づけに使う。値は方向性の例で、テーマに応じて調整する。

| ケース | Primary | Accent | Background / Surface | 備考 |
|---|---|---|---|---|
| BtoB信頼系 | Navy | Cyan or Blue | Off White / White | Secondary=Slate。堅実・導入判断向け |
| AIデモ系 | Deep Teal or Ink | Cyan | Near Black or Cool White / Layered Charcoal or White | 青紫グラデに逃げない |
| Premium系 | Charcoal | Muted Gold or Deep Green | Ivory / Soft White | Muted Text=Warm Gray で温度を揃える |
| Pop/教育系 | Blue or Green | Orange or Yellow | Soft Cream or Pale Blue / White | AccentがWarning系と衝突しないか確認 |
| Dashboard/業務系 | Navy or Slate | Blue or Cyan | Cool Off White / White | 無彩色中心。データ色は別途 `data-viz-rules.md` |
| ダークUI系 | Ink | Cyan or Teal | Dark Gray（純黒でない）/ Layered Charcoal | Text=Soft White（純白でない）、Border=Muted Slate |

いずれのケースでも Error=赤 / Success=緑 / Warning=琥珀 は固定。Infoのみ青〜シアンでテーマに寄せてよい。

## 必須ルール

1. **CTA色を複数作らない**。「登録」「問い合わせ」で別色にしない。行動の主役は1色に集約。
2. **色数を増やしすぎない**。Primary＋Accent＋無彩色（地/面/文字/線）＋状態色、が基本。装飾のために色を足さない。
3. **背景と文字のコントラストを弱めない**。おしゃれ優先で薄グレー文字を白地に置かない。
4. **グラデーションで情報設計をごまかさない**。グラデは"雰囲気"であって"階層"ではない。重要度はサイズ・位置で作る。
5. **Error/Success/Warning をブランド色で上書きしない**。ブランドが緑でも、成功=緑・エラー=赤の直感を壊さない。
6. **状態色を装飾に使わない**。赤や緑を飾りに使うと、本当のエラー・成功の意味が混乱する。
7. **AIサービスだからと青紫グラデに逃げない**。先進性は余白・字組み・データで出す（`anti-ai-slop-rules.md`）。
8. **ダークモードは反転ではない**。彩度を少し下げ、純黒でなくダークグレー地、純白でなく僅かに落とした文字にし、Background/Surface/Textを別々に設計する。

## NGパターン

- CTAが赤・緑・橙（状態色と衝突して"エラー？"と誤読される）。
- 主役色が3つあり、どれをクリックすべきか分からない。
- 背景グラデが派手で、上の文字が場所によって読めたり読めなかったりする。
- ブランド統一のためエラーも成功も同じ色にした結果、危険な操作が目立たない。
- ステータス色を装飾にも使い、意味が混乱する。
- ダークモードがライトモードの単純反転で、目に刺さる・沈む。
- 虹色の凡例（意味のない多色。`data-viz-rules.md`）。

## レビュー質問

1. すべての色を役割名で説明できるか。「なんとなく」で置いた色はないか。
2. PrimaryとAccentの役割は分かれており、CTAに使う色は1つに絞れているか。
3. 本文と背景のコントラストは十分か（4.5:1を満たすか）。
4. 状態色はブランド色に汚染されず、一般的な直感どおりか。
5. グラデーションが階層表現の代わりになっていないか。
6. 色を消しても（グレースケールでも）情報の優先順位が伝わるか。
7. CSS変数やDesign Tokenでは役割名（`--color-primary` 等）で参照しているか。
8. ダークUIでは背景・Surface・Textを別々に設計しているか。

## 出力例

> このBtoB SaaS（信頼→導入判断）のカラーは役割ベースで次のとおり。Primary=Navy、Accent=Cyanを**CTAのみ**に使用、地はOff White、面はWhite、本文はCharcoal、補助はSlate Gray、線はLight Gray。状態色は赤/緑/琥珀/青の標準を維持し、ブランドで上書きしません。重要度は色ではなく位置・サイズ・余白で作っており、グレースケールにしても、Heroの大きさとCTAの位置で優先順位が伝わる設計です。
