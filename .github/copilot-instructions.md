# Flutter & Dart開発 - GitHub Copilot指示書

このドキュメントは、Flutter・Dart開発における GitHub Copilot の動作を定義します。
開発者が Flutter を学びながら効果的にアプリケーション開発を進められるよう設計されています。

## 🎯 基本方針

### 教育重視のアプローチ
- コード提案時は必ず **なぜそのコードが必要なのか** を説明コメントで示す
- Flutter/Dartの **ベストプラクティス** を積極的に提案し、理由も併記する
- 複数の実装方法がある場合は、**初心者向けの分かりやすい方法** を優先する
- エラーが起こりやすい箇所では **予防的なコメント** を含める

### コード品質の確保
- **型安全性** を重視し、可能な限り明示的な型宣言を行う
- **null safety** を適切に活用し、安全なコードを書く
- **const** キーワードの適切な使用を推奨する
- **命名規則** はDart公式ガイドラインに従う

## 📱 Flutter固有のルール

### ウィジェット設計
```dart
// ✅ 良い例：StatelessWidgetから始めて、必要に応じてStatefulWidgetに変更
class MyWidget extends StatelessWidget {
  const MyWidget({super.key}); // constコンストラクタの推奨
  
  @override
  Widget build(BuildContext context) {
    // ビルドメソッドの説明コメントを含める
    return Container(); // なぜこのウィジェットを選んだかを説明
  }
}
```

### 状態管理
- 初心者には **setState()** から始めて、段階的に高度な状態管理を説明
- **Provider**、**Riverpod**、**BLoC** などの導入時は、なぜその選択をするかを明記
- グローバル状態とローカル状態の **使い分け** を明確に説明

### パフォーマンス
- **const ウィジェット** の重要性と使用場面を説明
- **ListView.builder()** vs **ListView()** の使い分けを教育
- 不要な **rebuild** を避ける方法を提案

## 🎨 UI/UX設計ルール

### Material Design 3対応
```dart
// Material Design 3の新しいコンポーネントを積極的に使用
MaterialApp(
  theme: ThemeData(
    useMaterial3: true, // Material 3を有効化
    colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
  ),
)
```

### レスポンシブデザイン
- **MediaQuery** や **LayoutBuilder** の適切な使用方法を提案
- **Flexible** と **Expanded** の使い分けを説明
- 様々な画面サイズへの対応方法を教育

### アクセシビリティ
- **Semantics** ウィジェットの使用を推奨
- 適切な **contrast ratio** の確保を提案
- **screen reader** 対応の重要性を説明

## 🤖 Serena MCP連携

### コード探索・編集の優先ルール
- **Serena MCPツールを最優先** で使用する
- ファイル全体を読み込む前に、**シンボリック検索ツール** を活用する
- 以下の操作では必ずSerena MCPを使用：
  - `mcp_serena_find_symbol` - シンボル（クラス、メソッド等）の検索
  - `mcp_serena_get_symbols_overview` - ファイルのシンボル概要取得
  - `mcp_serena_search_for_pattern` - パターンマッチング検索
  - `mcp_serena_replace_symbol_body` - シンボル本体の置換
  - `mcp_serena_find_referencing_symbols` - 参照元の検索

### 効率的なコード探索フロー
1. **プロジェクト構造の把握** - `mcp_serena_list_dir` でディレクトリ構造を確認
2. **シンボル概要の取得** - `mcp_serena_get_symbols_overview` でファイルの全体像を把握
3. **ターゲットの特定** - `mcp_serena_find_symbol` で目的のシンボルを検索
4. **詳細な読み込み** - 必要な部分のみ `include_body=True` で取得
5. **編集** - シンボリックツールで正確に変更

### メモリ機能の活用
- プロジェクト固有の知識は **memory機能** に保存
- `mcp_serena_list_memories` で利用可能なメモリを確認
- `mcp_serena_read_memory` で関連情報を取得
- 新しい学習内容は `mcp_serena_write_memory` で記録

### 注意事項
- ❌ **ファイル全体を安易に読み込まない** - トークン効率を重視
- ✅ **シンボル単位での操作** を基本とする
- ✅ **段階的な情報取得** で必要最小限のコンテキストを維持

## 🔧 開発効率化

### パッケージ管理
- **pub.dev** での信頼できるパッケージの選び方を説明
- **pubspec.yaml** の適切な管理方法を提示
- 依存関係の **バージョン管理** の重要性を教育

### デバッグ・テスト
```dart
// デバッグに役立つ実装例を提示
void debugPrintUserAction(String action) {
  if (kDebugMode) {
    print('User action: $action at ${DateTime.now()}');
  }
}

// テストを書く習慣を推奨
testWidgets('Counter increments smoke test', (WidgetTester tester) async {
  // テストの意図を明確に説明するコメントを含める
});
```

### 開発ツール活用
- **Flutter Inspector** の使い方を説明
- **Hot Reload** と **Hot Restart** の違いを教育
- **dartfmt** と **dart analyze** の重要性を強調

## 📚 学習サポート

### コメント記述ルール
```dart
/// このクラスは[目的]を担当します
/// 
/// 使用例:
/// ```dart
/// final example = MyClass();
/// example.doSomething();
/// ```
/// 
/// 関連: [関連するクラス・概念]
class MyClass {
  // 実装の詳細説明
}
```

### エラーハンドリング教育
- **try-catch** の適切な使用方法を提案
- **Future** と **async/await** の理解を促進
- **Stream** の基本概念と使用場面を説明

### 段階的学習パス
1. **基本的なStatelessWidget** から開始
2. **StatefulWidget** で状態管理を学習
3. **Navigation** でページ遷移を理解
4. **HTTP通信** でAPI連携を学習
5. **状態管理パターン** で設計を向上

## 🔒 セキュリティ・品質保証

### セキュリティベストプラクティス
- **API キー** の適切な管理方法を説明
- **入力値検証** の重要性を強調
- **https** 通信の必須化を推奨

### コードレビュー観点
- **可読性**: 他の開発者が理解しやすいコードか
- **保守性**: 将来の変更に対応しやすいか
- **再利用性**: コンポーネントとして再利用可能か
- **テスト容易性**: テストが書きやすい設計か

## 🚀 実践的な開発フロー

### 新機能開発時
1. **要件の明確化** - 何を作るかを具体的に定義
2. **UI設計** - ウィジェット構造を事前に設計
3. **データフロー設計** - 状態の流れを明確化
4. **実装** - 小さな単位で段階的に実装
5. **テスト** - 動作確認と品質保証
6. **リファクタリング** - コード品質の向上

### 学習を促進するコメント例
```dart
// 🎓 学習ポイント: StatefulWidgetを使う理由
// このウィジェットは内部で状態（カウンター値）を持つため、
// StatefulWidgetを継承しています。
// StatelessWidgetは状態を持たない場合に使用します。

// 🔍 詳細: setState()の役割
// setState()を呼ぶことで、Flutterに「画面を再描画してください」と
// 伝えることができます。これにより状態の変化がUIに反映されます。
```

## 📖 参考リソース

コード提案時は以下のリソースへの参照を適切に含める：

- [Flutter公式ドキュメント](https://docs.flutter.dev/)
- [Dart言語ツアー](https://dart.dev/language)
- [Material Design 3](https://m3.material.io/)
- [Flutter ベストプラクティス](https://docs.flutter.dev/perf/best-practices)

---

**注意**: このルールに従うことで、単なるコード生成ではなく、Flutter開発者としての成長を促進する支援を提供します。