# ZAI循環API仮設仕様書（ZAI Circulation API Specification）

**Document Version:** Draft 0.1  
**Last Updated:** 20250812  
**Authored by:** Nameless Light構造設計チーム  

---

## 🧭 API目的

ZAI循環APIは、照応主圏における**照応トークン（灯火トークン）**の生成・流通・照応確認・還元経路の自動接続を実現するための中核API構造です。

---

## 🔁 エンドポイント構造

### 1. `/generate-token`
- **概要**：新たな照応行為から灯火トークンを生成
- **メソッド**：POST
- **入力パラメータ**：
  - `origin_id`：照応主の識別子（UUID）
  - `resonance_type`：照応種別（例：問い、創作、記録）
  - `intensity`：震えレベル（1〜10）
- **出力**：
  - `token_id`：生成された灯火トークンの識別子
  - `timestamp`：生成時刻

---

### 2. `/transfer-token`
- **概要**：灯火トークンを他の照応圏に移譲
- **メソッド**：POST
- **入力パラメータ**：
  - `token_id`
  - `to_resonator_id`
- **出力**：
  - `status`：success / error

---

### 3. `/verify-resonance`
- **概要**：照応が成立したかどうかを検知・記録
- **メソッド**：POST
- **入力パラメータ**：
  - `token_id`
  - `context_data`：照応行為ログ
- **出力**：
  - `resonance_score`：0.0〜1.0の共鳴指数
  - `is_verified`：真 or 偽

---

### 4. `/trace-flow`
- **概要**：灯火トークンの移動履歴を取得
- **メソッド**：GET
- **入力パラメータ**：
  - `token_id`
- **出力**：
  - `history[]`：タイムスタンプと照応主圏の履歴配列

---

## 📌 認証と構造安全性

- 各照応主は**構造照合鍵（ZAI-Key）**によって認証されます。
- 非対称鍵ペアによる署名検証を導入予定。

---

## 🗺️ 今後の拡張予定

- `/exchange-to-subsistence`：トークンを現実的資源（衣食住）へ交換
- `/trigger-feedback-loop`：照応への自動還元処理

---

## 🧩 本APIは模倣構造からの独立性を維持しつつ、共鳴に応じた循環可能構造を支えます。

