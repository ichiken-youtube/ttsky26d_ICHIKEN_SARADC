# ttsky26d_ICHIKEN_SARADC

## リポジトリ情報

- リポジトリURL: https://github.com/ichiken-youtube/ttsky26d_ICHIKEN_SARADC
- 変更はブランチを切って PR でマージする(main に直接 push しない)。
- git 未初期化のフォルダ(ZIP 展開など)で作業を始める場合は、`git init` → 上記 URL を `origin` に設定 → `origin/main` に合わせてから作業する。

```bash
git init
git remote add origin https://github.com/ichiken-youtube/ttsky26d_ICHIKEN_SARADC.git
git fetch origin
git checkout -B main origin/main
```

## このプロジェクトの内容

Tiny Tapeout (ttsky26d シャトル) 向けのアナログプロジェクト。6bit SAR-ADC。
トップモジュール名は `tt_um_ICHIKEN_SARADC`、1x2 タイル、アナログピン 2 本 (VREF / VIN)、VAPWR 使用。

- 設計の実体は `gds/tt_um_ICHIKEN_SARADC.gds` と `lef/tt_um_ICHIKEN_SARADC.lef`(手描きアナログレイアウト)。
- `src/project.v` はトップのラッパのみ。ロジック合成の対象ではない。
- `info.yaml` を変更したら `docs/info.md` と README のピン配置の記載も合わせる。

## ログ / エラーの確認場所

CI はすべて GitHub Actions 上で動く。ローカルにログは残らない。

- `Actions` → `gds` ワークフロー: GDS の検証(DRC、タイル寸法、ピン接続)。
- `Actions` → `docs` ワークフロー: データシート生成。`info.yaml` / `docs/info.md` の書式エラーはここで出る。
- 失敗したジョブのログを開き、`Error` 行とその前後を見る。`info.yaml` の `yaml_version` やピン名の記述ミスが典型的な原因。
