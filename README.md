# 問題
野菜と果物を一つづつ箱詰めされた商品Aの売上履歴データを返す関数getQuestionnaireDataListがあります。
このデータを使い、売上履歴データをテーブルで一覧表示するツールをモダンフロントエンドフレームワーク(Vue.js,Angular,React等)を使い、実装してください。

- 条件１

以下のようなUIの３つの条件でAND条件で絞り込みができます。
- 赤いもの（fruits:Apple, Vegetables:Chili）
- 東京のきゅうり(Vegetables:Cucumber && Origin:Tokyo)
- 埼玉のりんご(fruits:Apple && Origin:Saitama)

## UI例

<img width="964" alt="image1" src="https://user-images.githubusercontent.com/13118113/116181646-f0dce800-a755-11eb-9d9b-f2987591694c.png">


## データ構造

QuestionnaireDataの配列を返すgetQuestionnaireDataListという関数があります。
QuestionnaireDataのInterface(Typescript)は以下のとおりです。

```

function getQuestionnaireDataList():Array<QuestionnaireData>;

interface QuestionnaireData{
	Id:number;
	Fruits:Set<"Apple"|"Orange"|"Peach">;
	Vegetables:Set<"Cucumber"|"Chili"|"BeanSprouts">;
	Origin:Set<"Tokyo"|"Saitama"|"Chiba">;
}

```

### 例

```

const QuestionnaireDataList = getQuestionnaireDataList();

/**

[
	{
		Id:1,
		Fruits:"Apple",
		Vegetables:"chili",
		Origin:"Tokyo"
	},
	{
		Id:2,
		Fruits:"Orange",
		Vegetables:"Cucumber",
		Origin:"Tokyo"
	}
]

**/

```
