# 問題
野菜と果物を一つづつ箱詰めされた商品Aの売上履歴データを返す関数getQuestionnaireDataListがあります。
このデータを使い、売上履歴データをテーブルで一覧表示するツールをモダンフロントエンドフレームワーク(Vue.js,Angular,React等)を使い、実装してください。


### 条件１

以下のようなUIの３つの条件でAND条件で絞り込みができます。
- 赤いもの（fruits:Apple, Vegetables:Chili）
- 東京のきゅうり(Vegetables:Cucumber && Origin:Tokyo)
- 埼玉のりんご(fruits:Apple && Origin:Saitama)

例として、赤いものと東京のきゅうりのチェックが両方ついている場合は、

赤いもの∩東京のきゅうり

は∅ですので、

表示されるデータは０件です。

### 条件２

QuestionnaireDataの配列の長さnは、n<10^2です。



## UI例

<img width="964" alt="image1" src="https://user-images.githubusercontent.com/13118113/116181646-f0dce800-a755-11eb-9d9b-f2987591694c.png">


## データ構造

QuestionnaireDataの配列を返すgetQuestionnaireDataListという関数があります。
QuestionnaireDataのInterface(Typescript)は以下のとおりです。

```

function getQuestionnaireDataList():Array<QuestionnaireData>;

interface QuestionnaireData{
	Id:number;
	Fruits:"Apple"|"Orange"|"Peach";
	Vegetables:"Cucumber"|"Chili"|"BeanSprouts";
	Origin:"Tokyo"|"Saitama"|"Chiba";
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
		Vegetables:"Chili",
		Origin:"Tokyo"
	},
	{
		Id:2,
		Fruits:"Orange",
		Vegetables:"Cucumber",
		Origin:"Tokyo"
	},
	{
		Id:3,
		Fruits:"Peach",
		Vegetables:"Cucumber",
		Origin:"Saitama"
	}
]

**/

```

## 評価ポイント

- バグがないこと
- 無駄がないこと
- 仕様変更に強いこと（例えば、フルーツの種類や絞り込み条件が増えた時、コードの変更箇所が少なければポイントアップ）


## 以下のコードはご自由にお使いください
```
function getQuestionnaireDataList():Array<QuestionnaireData>{
	const mapper = 	{
		Fruits:["Apple","Orange","Peach"];
		Vegetables:["Cucumber","Chili","BeanSprouts"];
		Origin:["Tokyo","Saitama","Chiba"]
	};
	const res:Array<QuestionnaireData> = [];
	const n = Math.floor(Math.random()*100);
	for(let i=0;i<n;i++){
		res.push({
			id:i,
			Fruits:mapper.Fruits[Math.floor(Math.random()*mapper.Fruits.length)],
			Vagetables:mapper.Vegetables[Math.floor(Math.random()*mapper.Vegetables.length)],
			Origin:mapper.Origin[Math.floor(Math.random()*mapper.Origin.length)],
		});
	}
	return res;
};

interface QuestionnaireData{
	Id:number;
	Fruits:"Apple"|"Orange"|"Peach";
	Vegetables:"Cucumber"|"Chili"|"BeanSprouts";
	Origin:"Tokyo"|"Saitama"|"Chiba";
}
```
