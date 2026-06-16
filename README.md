# CI/CD Lab

GitHub Actionsを使って、pushすると自動でテストが走る仕組みを構築した記録。

## 構成
- Python(add, multiply関数)
- pytest(テストコード)
- GitHub Actions(自動テスト実行)

## やったこと

### 自動テストの構築
.github/workflows/test.ymlを作成し、mainブランチへのpushをトリガーに
GitHub側のクラウド環境で自動的にpytestが実行されるようにした。

### 意図的にテストを失敗させる
add関数の実装をわざと間違えてpush。GitHub Actions上でテストが失敗し、
赤いバツが表示されることを確認。
修正してpushし直すと緑のチェックマークに戻ることを確認した。

### つまずいたポイント
- Personal Access Tokenにworkflowスコープがないと
  .github/workflows配下のファイルをpushできない
- Dockerのイメージ・キャッシュでディスク容量が圧迫され、
  docker system pruneで解放する経験をした

## 学んだこと
- CI/CDは「人間が手動でテストする」を「自動でテストする」に置き換える仕組み
- バグが混入したコードをmainブランチに入れる前に検知できる
