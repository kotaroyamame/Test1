# 問題
野菜と果物を一つづつ箱詰めされたパックの売上履歴データを返す関数getProductDataListがあります。
このデータを使い、売上履歴データをテーブルで一覧表示するツールをモダンフロントエンドフレームワーク(Vue.js,Angular,React等)を使い、実装してください。


## 条件１

以下のようなUIの任意の条件でAND条件で絞り込みができます。
### 条件グループ1
- 赤いもの（fruits:Apple, Vegetables:Chili）
- 東京のきゅうり(Vegetables:Cucumber && Origin:Tokyo)
- 埼玉のりんご(fruits:Apple && Origin:Saitama)

### 産地
- 東京
- 千葉
- 埼玉

例として、赤いものと東京のきゅうりのチェックが両方ついている場合は、

赤いもの∩東京のきゅうり

は∅ですので、

表示されるデータは０件です。

## 条件２

ProductDataの配列の長さnは、n<10^2です。



## UI例

<img width="953" alt="image1" src="https://user-images.githubusercontent.com/13118113/116193771-d2cdb280-a76a-11eb-8b6d-a67b31fea0c1.png">


## データ構造

ProductDataの配列を返すgetProductDataListという関数があります。
ProductDataのInterface(Typescript)は以下のとおりです。

```

function getProductDataList():Array<QuestionnaireData>;

interface ProductData{
	Id:number;
	Fruits:"Apple"|"Orange"|"Peach";
	Vegetables:"Cucumber"|"Chili"|"BeanSprouts";
	Origin:"Tokyo"|"Saitama"|"Chiba";
}

```

## 例

```

const ProductDataList = getProductDataList();

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
function getProductDataList():Array<QuestionnaireData>{
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

interface ProductData{
	Id:number;
	Fruits:"Apple"|"Orange"|"Peach";
	Vegetables:"Cucumber"|"Chili"|"BeanSprouts";
	Origin:"Tokyo"|"Saitama"|"Chiba";
}
```
