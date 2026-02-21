# AINDF-Spec (AI-Native Document Format Specification)
[English](./README.md)
AIに二度手間をさせない。コンテキスト（文脈）をコードに封じ込める、新しいデータ構成の提唱。

## 1. Introduction

AIエージェントによるコード生成は劇的に進化しましたが、依然として「開発者の意図」と「AIの出力」の間には深い溝があります。

* **プロジェクトの背景を何度も説明するのがだるい**
* **AIが勝手にライブラリや数値を推論して、既存の設計を壊す**
* **修正指示を出しても、どの箇所の話かAIに伝わらない**

AINDF (AI-Native Document Format) は、これらの「だるさ」を構造的に解決するために生まれました。  
プロンプトエンジニアリング（言葉による指示）に頼るのではなく、**データ構造そのものにAIへの制約と事実を組み込む**ことで、100%の再現性を実現します。

---

## 2. The Triple-Layer Architecture

AINDFは、1つのファイルを以下の3つの論理レイヤーで構成することを提唱します。

### Layer 1: Context Layer (The Rule)
AIに対する「前提条件」と「外部制約」を強制するレイヤーです。
* **役割**: 使用ライブラリ（例: Tailwind v4, shadcn/ui）、ビューポート、開発者の目的（Intent）を明文化。
* **効果**: AIは「どの技術スタックを使うべきか」の推論を止めることができ、環境の不一致によるエラーを根絶します。

### Layer 2: Implementation Layer (The View)
人間が読み書きし、プログラムとして実行可能なレイヤーです。
* **役割**: 具象的なコード表現（TSX, XAML, Kotlin等）。AIが生成・変換を行う対象。
* **効果**: 既存の資産（React, Android, Windowsアプリ等）と高い親和性を保ち、人間がコードベースで最終調整を行うことを可能にします。

### Layer 3: State Layer (The Truth / SSOT)
AIとエディタが共有する「不変の事実」を保持するレイヤーです。
* **役割**: 構造化データ（JSON等）。GUIの状態、要素の一意なID、不変のプロパティ値。
* **効果**: コードが書き換えられても「設計図としての事実」を維持。AIにとっての「解答集」となり、修正のブレを物理的に封じ込めます。

---

## 3. Core Principles

* **Stop Guessing, Start Defining**: AIに「空気を読ませる」のをやめ、「事実」を渡す。
* **Context Encapsulation**: 1つのファイルに全ての文脈を閉じ込め、ポータブルな開発体験を実現する。
* **Human-AI Symbiosis**: 人間が直感（GUI/Code）で伝え、AIが論理（Metadata/State）で応える協調構造。

---

## 4. Implementation Example: .moc Format

AINDFの概念をUI Builder（VSCode拡張 Mocker）に適用したリファレンス実装です。

* **[.moc ファイル形式仕様書](https://github.com/Mui-MuiMui/moc-spec/blob/main/READNE_JP.md)**
  * *人間・GUI・AIエージェントが協調して開発を行うための統合データ形式の実例。*

> ※ 本仕様はUI向けですが、AINDFの概念はAPI定義、データベースマイグレーション、ビジネスロジック記述など、あらゆるAI駆動開発に転用可能です。
> また、バージョンにより伝えるためのデータが増えた場合、タグなどが増える場合があります。しかし、基本的な概念は変わりません。

---

## 5. License

MIT License