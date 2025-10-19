# My Todo App

シンプルなTodoアプリから実務レベルのFlutter開発者へ成長するための学習プロジェクト

## 📋 プロジェクト概要

このプロジェクトは、Flutterの基礎から実務レベルのスキルまで段階的に学習することを目的としています。
Webアプリ開発経験者がスマホアプリ開発（Flutter）を習得するためのロードマップに沿って開発を進めます。

## 🎯 学習ロードマップ

### フェーズ1: コード構造の改善 (1-2週間)
**目標**: 保守性の高いコード構造を理解する

#### タスク
- [ ] プロジェクトのディレクトリ構造を作成
  - [ ] `lib/models/` ディレクトリを作成
  - [ ] `lib/screens/` ディレクトリを作成
  - [ ] `lib/widgets/` ディレクトリを作成
- [ ] Todoデータモデルクラスを作成 (`lib/models/todo.dart`)
  - [ ] `id`, `title`, `isCompleted`, `createdAt` プロパティを定義
  - [ ] `toggleComplete()` メソッドを実装
  - [ ] コンストラクタに `const` を使用
- [ ] 画面を個別ファイルに分割
  - [ ] `lib/screens/todo_list_page.dart` を作成
  - [ ] `lib/screens/todo_add_page.dart` を作成
  - [ ] `main.dart` から各画面をインポート
- [ ] Todoアイテムの機能を追加
  - [ ] チェックボックスで完了/未完了を切り替え
  - [ ] 削除ボタンを追加
  - [ ] 空のリスト時のメッセージ表示
- [ ] バリデーションを追加
  - [ ] 空文字チェック
  - [ ] 文字数制限の実装

**学習ポイント**:
- ファイル分割による可読性向上
- データモデルクラスの作成と型安全性
- イミュータブルなオブジェクト設計

---

### フェーズ2: 状態管理の導入 (2-3週間)
**目標**: Providerを使った状態管理を理解する

#### タスク
- [ ] Providerパッケージを追加
  - [ ] `pubspec.yaml` に `provider: ^6.1.1` を追加
  - [ ] `flutter pub get` を実行
- [ ] `lib/providers/` ディレクトリを作成
- [ ] `TodoProvider` クラスを作成 (`lib/providers/todo_provider.dart`)
  - [ ] `ChangeNotifier` を継承
  - [ ] `addTodo()` メソッドを実装
  - [ ] `toggleTodo()` メソッドを実装
  - [ ] `deleteTodo()` メソッドを実装
  - [ ] `incompleteTodoCount` ゲッターを実装
- [ ] `main.dart` で `ChangeNotifierProvider` をセットアップ
- [ ] 各画面で `Consumer` または `Provider.of` を使用してProviderにアクセス
- [ ] `setState()` の使用を最小限に抑える

**学習ポイント**:
- UIロジックとビジネスロジックの分離
- `ChangeNotifier` と `notifyListeners()` の仕組み
- Providerを使った依存性注入

---

### フェーズ3: データ永続化 (1-2週間)
**目標**: ローカルストレージを使ったデータ保存を実装

#### タスク
- [ ] SharedPreferencesパッケージを追加
  - [ ] `pubspec.yaml` に `shared_preferences: ^2.2.2` を追加
- [ ] `lib/services/` ディレクトリを作成
- [ ] `TodoStorageService` クラスを作成 (`lib/services/todo_storage_service.dart`)
  - [ ] `saveTodos()` メソッドを実装
  - [ ] `loadTodos()` メソッドを実装
  - [ ] JSON変換ロジックを実装
- [ ] `TodoProvider` に永続化機能を統合
  - [ ] アプリ起動時にデータを読み込み
  - [ ] データ変更時に自動保存
- [ ] Todoモデルに `toJson()` と `fromJson()` メソッドを追加

**学習ポイント**:
- `Future` と `async/await` の使い方
- JSON シリアライゼーション
- ローカルストレージの活用

---

### フェーズ4: UIの洗練 (2-3週間)
**目標**: Material Design 3を活用した美しいUIを実装

#### タスク
- [ ] Material Design 3を有効化
  - [ ] `ThemeData` で `useMaterial3: true` を設定
  - [ ] `ColorScheme.fromSeed()` でテーマカラーを定義
- [ ] ダークモード対応
  - [ ] `darkTheme` を設定
  - [ ] `ThemeMode.system` で自動切り替え
- [ ] カスタムウィジェットを作成
  - [ ] `TodoListItem` ウィジェット
  - [ ] `EmptyState` ウィジェット
- [ ] アニメーションを追加
  - [ ] リスト追加時のアニメーション
  - [ ] 削除時のスワイプジェスチャー
- [ ] レスポンシブデザイン対応
  - [ ] `MediaQuery` を使った画面サイズ対応
  - [ ] タブレット用レイアウトの追加

**学習ポイント**:
- Material Design 3の新コンポーネント
- テーマのカスタマイズ
- アニメーションの基礎

---

### フェーズ5: テストの導入 (2週間)
**目標**: テストを書く習慣を身につける

#### タスク
- [ ] 単体テストを作成
  - [ ] `test/models/todo_test.dart` - Todoモデルのテスト
  - [ ] `test/providers/todo_provider_test.dart` - Providerのテスト
  - [ ] `test/services/todo_storage_service_test.dart` - ストレージサービスのテスト
- [ ] ウィジェットテストを作成
  - [ ] `test/screens/todo_list_page_test.dart`
  - [ ] `test/screens/todo_add_page_test.dart`
- [ ] テストカバレッジを確認
  - [ ] `flutter test --coverage` を実行
  - [ ] カバレッジ80%以上を目指す

**学習ポイント**:
- `flutter_test` パッケージの使い方
- モックとスタブの作成
- テスト駆動開発(TDD)の考え方

---

## 🔥 インフラ学習ロードマップ

### フェーズ6: Firebase統合 (1-2ヶ月)
**目標**: Firebaseを使ったバックエンド連携を実装

#### タスク
- [ ] Firebaseプロジェクトのセットアップ
  - [ ] Firebase Consoleでプロジェクトを作成
  - [ ] FlutterアプリにFirebaseを追加 (`flutterfire configure`)
  - [ ] 必要なパッケージを追加
    - [ ] `firebase_core: ^2.24.2`
    - [ ] `cloud_firestore: ^4.13.6`
    - [ ] `firebase_auth: ^4.15.3`
    - [ ] `firebase_storage: ^11.5.6`
- [ ] Cloud Firestoreの実装
  - [ ] `lib/services/todo_firestore_service.dart` を作成
  - [ ] CRUD操作を実装
  - [ ] リアルタイムリスナーを実装
  - [ ] クエリ（orderBy, where）を実装
- [ ] Firebase Authenticationの実装
  - [ ] メール/パスワード認証を実装
  - [ ] Googleサインインを追加
  - [ ] ログイン画面を作成
  - [ ] 認証状態に応じた画面遷移
- [ ] Firebase Storageの実装
  - [ ] プロフィール画像のアップロード機能
  - [ ] 画像選択UI
  - [ ] アップロード進行状況の表示
- [ ] セキュリティルールの設定
  - [ ] Firestoreルールの作成
  - [ ] Storageルールの作成

**学習ポイント**:
- サーバーレスアーキテクチャ
- リアルタイム同期の仕組み
- NoSQLデータベース設計

---

### フェーズ7: AWS Amplify統合 (1-2ヶ月)
**目標**: AWS実務スキルをモバイルアプリに適用

#### タスク
- [ ] Amplify CLIのセットアップ
  - [ ] `npm install -g @aws-amplify/cli`
  - [ ] `amplify configure` で AWS認証情報を設定
  - [ ] `amplify init` でプロジェクト初期化
- [ ] Amplifyパッケージを追加
  - [ ] `amplify_flutter: ^2.0.0`
  - [ ] `amplify_auth_cognito: ^2.0.0`
  - [ ] `amplify_api: ^2.0.0`
  - [ ] `amplify_storage_s3: ^2.0.0`
- [ ] Cognito認証の実装
  - [ ] `amplify add auth` でCognitoを追加
  - [ ] サインアップ/サインイン機能
  - [ ] パスワードリセット機能
- [ ] AppSync (GraphQL API) の実装
  - [ ] `amplify add api` でAPIを追加
  - [ ] GraphQLスキーマを定義
  - [ ] クエリとミューテーションを実装
  - [ ] サブスクリプション（リアルタイム更新）を実装
- [ ] S3ストレージの実装
  - [ ] `amplify add storage` でS3を追加
  - [ ] ファイルアップロード/ダウンロード
- [ ] バックエンドのデプロイ
  - [ ] `amplify push` で全リソースをデプロイ

**学習ポイント**:
- GraphQLの基礎
- AWS各サービスの連携
- Infrastructure as Code (IaC)

---

### フェーズ8: ハイブリッド実装 (1ヶ月)
**目標**: バックエンドを切り替え可能なアーキテクチャ

#### タスク
- [ ] リポジトリパターンの実装
  - [ ] `lib/repositories/todo_repository.dart` (インターフェース)
  - [ ] `lib/repositories/firebase_todo_repository.dart`
  - [ ] `lib/repositories/amplify_todo_repository.dart`
  - [ ] `lib/repositories/local_todo_repository.dart`
- [ ] 依存性注入の改善
  - [ ] 環境変数でバックエンドを切り替え
  - [ ] `MultiProvider` での複数プロバイダー管理
- [ ] オフライン対応
  - [ ] ローカルキャッシュの実装
  - [ ] 同期ステータスの表示
  - [ ] コンフリクト解決ロジック

**学習ポイント**:
- クリーンアーキテクチャ
- デザインパターン（Repository, Strategy）
- オフラインファースト設計

---

## 🚀 追加の実務スキル（継続的）

### パフォーマンス最適化
- [ ] `const` キーワードの徹底利用
- [ ] 不要なrebuildの削減
- [ ] 画像の最適化とキャッシング
- [ ] Lazy loadingの実装

### CI/CD パイプライン
- [ ] GitHub Actionsのセットアップ
- [ ] 自動テストの実行
- [ ] 自動ビルド（Android/iOS）
- [ ] TestFlightへの自動デプロイ

### 高度な状態管理
- [ ] Riverpodへの移行検討
- [ ] BLoCパターンの学習

### 分析とモニタリング
- [ ] Firebase Analyticsの統合
- [ ] クラッシュレポート（Crashlytics）
- [ ] パフォーマンスモニタリング

---

## 📚 参考リソース

### 公式ドキュメント
- [Flutter公式ドキュメント](https://docs.flutter.dev/)
- [Dart言語ツアー](https://dart.dev/language)
- [Material Design 3](https://m3.material.io/)
- [Firebase Flutter](https://firebase.google.com/docs/flutter/setup)
- [AWS Amplify Flutter](https://docs.amplify.aws/lib/q/platform/flutter/)

### 学習サイト
- [Flutter Cookbook](https://docs.flutter.dev/cookbook)
- [Flutter ベストプラクティス](https://docs.flutter.dev/perf/best-practices)
- [pub.dev](https://pub.dev/) - パッケージ検索

### コミュニティ
- Flutter公式Discord
- Stack Overflow
- Reddit r/FlutterDev

---

## 🎯 学習の進め方

1. **各フェーズを順番に進める**: 基礎から段階的にスキルアップ
2. **実際にコードを書く**: 読むだけでなく手を動かす
3. **エラーを恐れない**: エラーは最高の学習機会
4. **コメントを残す**: 学んだことをコメントで記録
5. **定期的にリファクタリング**: コードを改善し続ける

---

## 📝 開発メモ

### 現在の状態
- ✅ 基本的なTodoアプリの実装完了
- 🔄 フェーズ1の実装準備中

### 次のアクション
1. ディレクトリ構造の作成
2. Todoモデルクラスの実装
3. ファイル分割の実施

---

## 📄 ライセンス

このプロジェクトは学習目的で作成されています。
