<!-- ![image](https://user-images.githubusercontent.com/44872783/92857172-49fa4480-f42f-11ea-923c-80339037493b.png) -->

![image](https://user-images.githubusercontent.com/44872783/93992285-533cc700-fdc8-11ea-8da1-62595a2f681c.png)

# 教養のコンピュータアルゴリズム（土屋達弘著，共立出版，2009）のサポート情報です．

## 正誤表

- 29ページ，最後のアルゴリズムのwhileの条件: 「または，前回のループで交換が起らなかった」->「または，前回のループで交換が起った」

- 37ページ，演習問題(2), ifの条件:「i番目の要素はxと等しいかxよりも前である」->「i番目の要素はxと等しいかxよりも後である」，
「i番目の要素はxと等しいかxよりも後である」->「i番目の要素はxと等しいかxよりも前である」

- 107ページ，アルゴリズムの最後にelse部が必要

###

    else  
        NOを出力する;


## 新しい書き方のプログラム

教科書のプログラムは今でも問題なく動作しますが，JavaScriptも変化しており，新しい書き方や機能が追加されています．
以下に，現在のJavaScriptの仕様に即したプログラムを掲載します．
（参考：[MDN web docs](https://developer.mozilla.org/ja/docs/Web/JavaScript)）

一番重要な点は，変数を宣言するためのキーワード`var`の代わりに，`let`を使うようにした点です．
宣言された変数が有効なプログラムの範囲をスコープといいますが，小さい方がプログラムの理解が容易になります．
`var`より`let`の方がスコープを小さくできます．
具体的には，`let`の場合は，ブロックという`{`と`}`で囲まれた範囲の中で用いられれば，スコープがそのブロックの中に限定されます．
また，`for`に続く`(` `)`の部分で用いられた場合は，`for`ループの本体がスコープです．
（なお，再代入しない変数には`let`ではなく`const`を使うべきなのですが，覚えることを少なくしたいので`let`で代用しています．）


あと，古いJavaScriptでも同様なのですが，記述ミスや誤解を少なくするため，ループの本体や，if構造，if-else構造のステップは，
1文しかなくても，`{`と`}`で囲んだ方がよいでしょう．

以下，各章からいくつか例を挙げます．

### 第1章

3ページ

    let i = 0;
    while (i < 10) {
      document.write('Hello ');
      document.write('World!');
      document.write('<br>');
      i += 1;
    }

### 第2章

13ページ

    let x, y;
    x = parseFloat(prompt('Celsius?'));
    // ファーレンハイト度 = 1.8 * セルシアス度 + 32
    y = 1.8 * x + 32;
    document.write(x + ' deg C = ' + y + ' deg F');

21ページ

    let a = [20, 4, 32, 18, 17];
    let max = a[0];
    for (let i = 1; i < a.length; i += 1) {
      if (a[i] > max) {
        max = a[i];
      }
    }
    document.write(max);

(参考）教科書の`for`, `in` は `for`, `of` で表現できるようになりました．

    let a = [20, 4, 32, 18, 17];
    let max = a[0];
    for (const element of a) {
      if (element > max) {
        max = element;
      }
    }
    document.write(max);


23ページ． 教科書のプログラムは4行目で`mod`を明示的に宣言すべきでした．
(下では`let`で宣言していますが，再代入しないので`const`の方が本当はよいです．)

    let x = 51;
    let y = 27;
    while (y > 0) {
      let mod = x % y;
      x = y;
      y = mod;
    }
    document.write('Answer: ' + x);

### 第3章

35～36ページ．教科書のプログラムは`i`を明示的に宣言すべきでした．

    let a = [4, 8, 9, 16, 25, 32, 49, 64, 81, 100];
    let x = parseInt(prompt('x?'), 10);
    let found = false;
    let low = 0;
    let high = a.length - 1;
    while (low <= high) {
      let i = low + Math.floor((high - low) / 2);
      if (a[i] === x) {
        found = true;
        break;
      }
      if (x < a[i]) {
        high = i - 1;
      } else {
        low = i + 1;
      }
    }
    document.write(found);i 

なお，分かりやすさ優先なら，`i`は以下のように計算できます（参考．`low`, `high`の値が巨大な場合，オーバーフローする危険性あり．）                                                

      let i = Math.floor((low + high) / 2);
      


以降については，適宜追加します．
