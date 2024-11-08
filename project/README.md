# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

```mermaid　
---
title: "keisan ER図"
---
erDiagram

users{
   increments id PK "主キー"
   string name "ログインユーザー名"
   string password "ログインPW（ハッシュ化）"
}

parameters {
   increments id PK "主キー"
   integer user_id FK 
   integer arg1_min "第1要素の最小値"
   integer arg1_max "第1要素の最大値"
   integer arg1_decimal "第1要素の小数点桁数"
   integer arg2_min "第2要素の最小値"
   integer arg2_max "第2要素の最大値"
   integer arg2_decimal "第2要素の小数点桁数"
   string operator "計算の演算子"
   integer res_max "計算結果の最大値"
}

result_summary {
   increments id PK "主キー"
   integer user_id FK 
   integer parameter_id FK 
   integer time "回答に要した時間"
   date date "テスト実施日"
}

result_detail {
   increments id PK "主キー"
   integer result_id FK 
   integer parameter_id FK 
   decimal arg1 "第1要素"
   decimal arg2 "第2要素"
   string operator "計算の演算子"
   decimal correct "計算の正解値"
   decimal answered "ユーザーの回答"
   boolean isCorrectly "ユーザーが正解したか"
}

users ||--o{ parameters : "1つのuserは、0以上のparameterを持つ"
parameters ||--o{ result_summary : "1つのresult_summeryは、0以上のparameterを持つ"
users ||--o{ result_summary : "1つのresult_summeryは、0以上のuserを持つ"
result_summary  ||--o{result_detail  : "1つのresult_summeryは、0以上のresult_detailを持つ"
```　
