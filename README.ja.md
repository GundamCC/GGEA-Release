<div align="center">
  <h1>GGEA</h1>
  🌟 SDガンダム ジージェネレーション エターナル アシスタント 🌟
</div>

[简体中文](README.md) | 日本語

## 主な機能

- **デイリータスク**：戦艦の回収、ショップの無料デイリーパック購入、開発・強化各1回、強化育成ステージのスキップ、AP消費、報酬受け取りに対応。ドラッグで実行順序を変更できます。
- **報酬受け取り**：プレゼントとデイリーミッション報酬を受け取ります。設定により、ほかのデイリータスク完了後に最終報酬を受け取れます。
- **AP消費**：メインステージの作品とHARDステージを指定してスキップします。実行順序の変更と設定の保存に対応しています。
- **自動周回**：指定ステージを繰り返しプレイします。周回数や特定の状況での出撃を設定できます。
- **自動スカウト**：スカウト可能なキャラクターを自動でスカウトします。
- **自動攻略**：メインステージのHARDまでの進行、ヒストリーステージ（BOSSを含む）、強敵襲来の3難易度に対応しています。
- **強敵襲来**：毎日の強敵襲来をスキップします。デイリータスクにも追加できます。
- **ボール工場**：指定したGPを獲得するまで、ボールの生産と解体を繰り返します。

## はじめに

### ダウンロード

[GitHub Releases](https://github.com/GundamCC/GGEA-Release/releases) から最新版をダウンロードしてください。

### 使い方

1. ゲームをインストールしたAndroidエミュレーターを起動し、解像度を **1920 × 1080（横画面）** に設定してADBデバッグを有効にします。
2. ZIPファイルをすべて展開し、フォルダー内の `GGEA.exe` を起動します。実行ファイルだけを別の場所へ移動しないでください。
3. 右上の設定（「设置」）で、使用するエミュレーターの `adb.exe` を選択します。BlueStacksでは `HD-Adb.exe` を選択してください。
4. 設定でゲームのサーバーと言語を選択して保存します。メイン画面で更新（「刷新」）を押し、操作対象のエミュレーターを選択します。
5. ゲーム内のアカウントと画面を確認してから、必要な機能を選択してタスクを開始します。

## 注意事項

- 推奨エミュレーターはMuMuまたはLDPlayerです。
- 対応サーバー：グローバル版、日本版。
- 対応するゲーム内言語：簡体字中国語、日本語。これはGGEA自体の表示言語とは異なります。
- 動作確認済みのエミュレーター：MuMu 6、MuMu 12、LDPlayer 14、BlueStacks 5。環境によって動作が異なる場合があります。
- 対応OS：Windows 10/11 x64。配布パッケージには.NETランタイムが含まれており、別途インストールする必要はありません。
- 複数のエミュレーターを切り替えて使用できます。開始前に対象の端末を確認してください。
- 自動操作は現在 **1920 × 1080** の解像度に対応しています。
- 「修复主界面 Billing 查询卡顿」は、ホーム画面のBilling問い合わせによる停止を改善する任意の機能です。Rootを有効にしたx86_64 Androidエミュレーターでのみ利用できます。有効な間はゲーム内購入と購入の復元が利用できません。購入機能を使う前に、この設定を無効にしてゲームを再起動してください。
- AP消費プランは `config/ap_consumption_profiles.json` に保存されます。
- 初回は動作を見守りながら使用してください。ダイヤ消費、課金、認証、想定外の画面が表示された場合は停止して手動で確認してください。

## ダウンロードファイルの確認

Releaseには、ZIPと同名の `.zip.sha256` ファイルも添付されています。以下のファイル名を、ダウンロードしたZIPの名前に置き換えて実行してください。

```powershell
(Get-FileHash -Algorithm SHA256 -LiteralPath '.\GGEA-v1.2.15.3-win-x64.zip').Hash.ToLowerInvariant()
```

出力された値が `.zip.sha256` の先頭列と一致することを確認します。パッケージ内の `build-info.json` にはソースのコミットとファイルのハッシュが記録されています。SHA-256はファイルの整合性確認用であり、電子署名ではありません。

## 使用しているプロジェクト

- [.NET 8](https://dotnet.microsoft.com/en-us/) / [WPF](https://learn.microsoft.com/en-us/dotnet/desktop/wpf/overview/)：WindowsアプリケーションとUI。正式版は自己完結型で配布されます。
- [OpenCvSharp 4.13.0.20260627](https://github.com/shimat/opencvsharp) / [OpenCV 4.13.0](https://opencv.org/)：画像の読み込みとテンプレートマッチング。`OpenCvSharpExtern.dll` はパッケージに同梱されています。
- [ONNX Runtime 1.23.2](https://github.com/microsoft/onnxruntime) / [PaddleOCR PP-OCRv5](https://github.com/PaddlePaddle/PaddleOCR)：ローカルCPUでステージ番号とHARDの見出しを認識します。モデルとライセンスは `resources/ocr/` を参照してください。
- [LSPlant 6.4](https://github.com/LSPosed/LSPlant)、[xDL 2.4.0](https://github.com/hexhacking/xDL)、[Dobby 1.2](https://github.com/jmpews/Dobby)、[LLVM libc++ 18.1.8](https://libcxx.llvm.org/)：任意のBilling機能に使用します。ライセンスは `billing-runtime/licenses/` に同梱されています。
- [Android Debug Bridge (ADB)](https://developer.android.com/tools/adb)：エミュレーターへの接続、スクリーンショット取得、操作の送信に使用します。ADBは同梱されていません。エミュレーター付属のADBまたはAndroid SDK Platform-Toolsを使用してください。

## 不具合・要望

[Issues](https://github.com/GundamCC/GGEA-Release/issues) に、GGEAのバージョン、Windowsとエミュレーターの環境、再現手順、問題発生前後の操作を記載してください。ログは展開先の `logs/` に保存されます。共有前に個人情報や認証情報が含まれていないか確認してください。

[公式QQグループ：1002150086](https://qm.qq.com/q/zkxGhEiVQQ) でも不具合報告や機能の提案を受け付けています。
