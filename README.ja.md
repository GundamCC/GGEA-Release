# GGEA 旧クライアント向け互換配布

[简体中文](README.md) | 日本語

ソースコード、製品紹介、不具合報告、今後の正式リリースは [GGEA メインリポジトリ](https://github.com/GundamCC/GGEA)に集約します。

- [正式リリース](https://github.com/GundamCC/GGEA/releases)
- [日本語の使い方](https://github.com/GundamCC/GGEA/blob/main/README.ja.md)
- [不具合・要望](https://github.com/GundamCC/GGEA/issues)
- [旧版・移行パッケージ](https://github.com/GundamCC/GGEA-Release/releases)
- [コミュニティ QQ グループ](https://qm.qq.com/q/zkxGhEiVQQ)

## 移行状況

移行版はまだ公開していません。メインリポジトリに正式パッケージがない場合は、このリポジトリの既存の正式版を利用してください。ソースのバージョンからダウンロードURLを推測しないでください。既存の配布ファイルはそのまま保持します。過去に削除されたパッケージは復元しません。

旧クライアントはこのリポジトリの正式Releaseと添付ファイルのURLを検証します。今後、公開の承認を得てから、メインリポジトリと同一の検証済み移行ZIPおよびSHA-256ファイルをここにも公開します。更新後のプログラムはメインリポジトリを参照します。外部リンクだけのReleaseでは移行できません。

ルートの `update-sources.json` は旧クライアントの予備配布先検出用です。空のv1設定は有効ですが、主配布先を切り替える機能ではありません。旧クライアントの移行確認まで互換入口を停止せず、その後も既存のダウンロードと設定ファイルを保持します。通常の新バージョンはメインリポジトリで公開します。

[移行と検証の手順（中国語）](https://github.com/GundamCC/GGEA/blob/main/docs/release-migration.md)

## 整合性とライセンス

ZIPと同名の `.zip.sha256` を取得し、PowerShellの `Get-FileHash -Algorithm SHA256` で確認してください。SHA-256は電子署名ではありません。ソースのコミットとファイルのハッシュはパッケージ内の `build-info.json` に記録されます。

過去の説明は `releases/` に保持します。各パッケージのライセンスはそのパッケージに同梱されたものを参照してください。[現在の第三者ライセンス](https://github.com/GundamCC/GGEA/blob/main/resources/common/licenses/NOTICE.txt) · [任意の拡張機能](https://github.com/GundamCC/GGEA-Extensions)
