## 外部APIの呼び出しのミニレポート
### Q3-1. 郵便番号APIについて説明せよ。
* エンドポイントと機能
    * zipcloud:https://zipcloud.ibsnet.co.jp/api/search
    * 日本郵便が公開している、郵便番号データを検索する機能をRESTで提供している。
* リクエストとレスポンスのフォーマット    
    * https://zipcloud.ibsnet.co.jp/api/search
        * このURLにリクエストパラメータを加え、リクエストを行います。
    *リクエストパラメータ
        * zipcode:郵便番号(7桁の数字。ハイフン付きでも可。完全一致検索。)
        * callback:コールバック関数名(JSONPとして出力する際のコールバック関数名。UTF-8でURLエンコードした文字列。)
        * limit:最大件数(同一の郵便番号で複数件のデータが存在する場合に返される件数の上限値（数字）　※デフォルト：20)
    * レスポンスのサンプル
```
	"message": null,
	"results": [
		{
			"address1": "北海道",
			"address2": "美唄市",
			"address3": "上美唄町協和",
			"kana1": "ﾎｯｶｲﾄﾞｳ",
			"kana2": "ﾋﾞﾊﾞｲｼ",
			"kana3": "ｶﾐﾋﾞﾊﾞｲﾁｮｳｷｮｳﾜ",
			"prefcode": "1",
			"zipcode": "0790177"
		},
		{
			"address1": "北海道",
			"address2": "美唄市",
			"address3": "上美唄町南",
			"kana1": "ﾎｯｶｲﾄﾞｳ",
			"kana2": "ﾋﾞﾊﾞｲｼ",
			"kana3": "ｶﾐﾋﾞﾊﾞｲﾁｮｳﾐﾅﾐ",
			"prefcode": "1",
			"zipcode": "0790177"
		}
	],
	"status": 200
}
```
### Q3-2. 各自で調査したAPIについて説明せよ。
* APIの名称と参照URL
	* Deck of Cards API([https://deckofcardsapi.com/]https://deckofcardsapi.com/)
* エンドポイントと機能
	* https://deckofcardsapi.com/api/deck/new/shuffle/?deck_count=1
 	* トランプカードの操作ができるWebAPI。
 	* カードをシャッフルする、カードを引く、デッキ作成などの操作が可能。
* リクエストとレスポンスのフォーマット
    * https://deckofcardsapi.com/api/
        * このURLにリクエストパラメータを加え、リクエストを行います。
    *リクエストパラメータの一例
        * deck_id:デッキID(string型。デッキの識別子。)
        * Cards:カード名(string型。コンマ区切り文字列としてのカード。)
        * deck_count:デッキの数(int型)
        * cards.image:カードの画像(string型)
        * cards.value:カードの値(string型)
        * cards.suit:カードのスーツ(string型)
        * cards.code:カードのコード(string型)
    * レスポンスのサンプル
```
{
    "success": true,
    "deckid": "kxozasf3edqu",
    "cards": [
        {
            "code": "6H",
            "image": "https://deckofcardsapi.com/static/img/6H.png",
            "images": {
                "svg": "https://deckofcardsapi.com/static/img/6H.svg",
                "png": "https://deckofcardsapi.com/static/img/6H.png"
            },
            "value": "6",
            "suit": "HEARTS"
        },
        {
            "code": "5S",
            "image": "https://deckofcardsapi.com/static/img/5S.png",
            "images": {
                "svg": "https://deckofcardsapi.com/static/img/5S.svg",
                "png": "https://deckofcardsapi.com/static/img/5S.png"
            },
            "value": "5",
            "suit": "SPADES"
        }
    ],
    "remaining": 50
}

```
  
### Q3-3. 感想
* 今回の課題で苦労したこと
	* それぞれのAPIの特性や、リクエストのフォーマットを参照するのが大変だと感じた。APIによっては、説明の少ないものもあると気がつき、使うまでにさらに苦労すると感じた。
* 演習を通して理解できたこと
	* WebAPIを使うことで、シンプルなコードで複雑な操作をさせることが可能。データベースの使用などに便利だと感じた。
* Web APIの利便性や課題など
	* 利便性
 		* 効率化:開発期間の短縮やコスト軽減
   		* システムと連携したプログラム:連携先のデータが更新されると、APIで連携されていれば自動で最新情報に更新
 	* 課題
  		* 連携先のサービスに依存:サービス提供が突然止まってしまう可能性がある
    		* セキュリティ対策が必要:データベースに穴をあけるためセキュリティが弱い
      		* データを失う可能性:インターネット回線を使用しているため
