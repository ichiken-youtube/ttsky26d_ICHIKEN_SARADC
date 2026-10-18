![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg)

# 6bit SAR-ADC by ICHIKEN.

Tiny Tapeout (ttsky26d) 向けのアナログ設計プロジェクト。6bit の SAR-ADC (逐次比較型 A/D コンバータ) を 1x2 タイルに実装したもの。トップモジュールは `tt_um_ICHIKEN_SARADC`。

## リポジトリ

- リポジトリURL: https://github.com/ichiken-youtube/ttsky26d_ICHIKEN_SARADC

### 最新版の入手方法

- ZIP でダウンロード: https://github.com/ichiken-youtube/ttsky26d_ICHIKEN_SARADC/archive/refs/heads/main.zip
  (または GitHub のページ右上 `Code` → `Download ZIP`)
- git clone:

```bash
git clone https://github.com/ichiken-youtube/ttsky26d_ICHIKEN_SARADC.git
```

## フォルダ構成

| パス | 内容 |
| --- | --- |
| `info.yaml` | Tiny Tapeout のプロジェクト情報(タイル数、ピン配置、アナログピン等) |
| `src/project.v` | トップモジュール `tt_um_ICHIKEN_SARADC` のラッパ(アナログ設計なので中身は GDS 側) |
| `gds/tt_um_ICHIKEN_SARADC.gds` | レイアウト(GDSII) |
| `lef/tt_um_ICHIKEN_SARADC.lef` | 配置配線用の抽象(LEF) |
| `docs/info.md` | データシート用の説明文 |
| `.github/workflows/` | GDS ビルドとドキュメント生成の GitHub Actions |

## ピン配置

- 入力: `ui[0]` = XRST, `ui[1]` = XCLK
- 出力: `uo[0]` = EOC, `uo[1..6]` = DIGITAL_OUT[5..0]
- アナログ: `ua[0]` = VREF, `ua[1]` = VIN
- 電源: VDPWR (1.8V) に加えて VAPWR を使用 (`uses_vapwr: true`)

詳細は [info.yaml](info.yaml) を参照。

## Tiny Tapeout について

- 公式ドキュメント: https://tinytapeout.com
- FAQ / 困ったとき: https://tinytapeout.com/faq/

GitHub Actions が失敗したときは、リポジトリの `Actions` タブで該当ワークフローのログを開き、エラー箇所をそのまま貼って相談するのが早い。
