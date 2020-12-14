## 第1章 コンピュータとプログラム

コンピュータが，プログラムの指示によって動作することを説明します． 本書ではJavaScriptプログラムを例として使っています． JavaScriptプログラムは，ウェブブラウザを使って実行することができるので，PCですぐに動作させることができます．

たとえば，以下をエディタで入力して，example1.htmlというファイルとして保存し，そのファイルをクリックしてみてください． ファイルに記述されたJavaScriptプログラムが実行されます．

```html
<!DOCTYPE html>
<head>
<html>
<meta charset=utf-8>
<script type="text/javascript">
document.write('Hello ');
document.write('World!');
</head>
</script>
<body>
</body>
</html>
```

実際のプログラムは以下の2文だけです．
```JavaScript
document.write('Hello ');
document.write('World!');
```

入力済みのファイルは次のリンクから左クリックでダウンロードできます． クリックすれば直接実行できます．
[(example1.html)](example1.html)

本書のほとんどは，このようなプログラムの総称であるソフトウェアに関する内容ですが， この章では，コンピュータの機械部分，つまり，ハードウェアについても，簡単に説明します．

## 第2章 アルゴリズム

プログラムの動作原理であるアルゴリズムについて説明します． まず，アルゴリズムの基本構造である，連続，選択，繰り返しの3要素について学びます． そして，簡単なアルゴリズムとして，ユークリッドの互除法(最大公約数を求めるアルゴリズム)と，数が素数かどうかを判定するアルゴリズムを考えます．

### ユークリッドの互除法

最大公約数を計算します． 下のプログラムでは27と72の最大公約数を求めます．

```JavaScript
var x = 27, y = 72;
while (y > 0) {
  var mod = x % y;
  x = y;
  y = mod;
}
document.write('Answer: ' + x);
```
[gcd.html](gcd.html)

素数判定アルゴリズム
入力された整数が素数かどうか判定します．
```JavaScript
var N = parseInt(prompt('N?'), 10);
var divisible = false;
var sq = Math.sqrt(N);
for (var i = 2; i <= sq; i += 1) {
  if (N % i === 0)
    divisible = true;
}
if (divisible === true)
  document.write(N + ' is not a prime number.');
else
  document.write(N + ' is a prime number.');
```
[prime2.html](prime2.html)

## 第3章 基本的なアルゴリズム
アルゴリズムの多くは，複数のデータを効率的に操作するために設計されています． 特に，データを順番にならべるソーティングと，必要なデータを探す探索は，もっとも基本的で重要な処理といえます． これらの二つの処理について，具体的なアルゴリズムとプログラムを通して学びます．

バブルソート
単純なソーティングアルゴリズムです．

[bubble.html](bubble.html)

## 第4章 関数と再帰アルゴリズム
アルゴリズムのよく使う部分を，独立したモジュールとして切り出したものが，関数です． 関数を使うと，自分自身を呼び出す再帰プログラムが実現できます．

### ハノイの塔
再帰プログラムの有効性を示すため，ハノイの塔というパズルを解くアルゴリズムを考えます．

パズル自体はこちら [(hanoi_game.html)](hanoi_game.html)．円盤の塔を左端に移してください． カーソルキーで動かします．


パズルを解くアルゴリズムはこちらです．

[hanoi.html](hanoi.html)


## 第5章 データ構造
データを管理・操作するための機構である，データ構造について学びます．

### 2分木
2分木をデータ構造として利用して，英文中の単語の出現回数を数えるプログラムです． （now is the time for all good men to come to the aid of their partyという文を例にしています．）

[binarytree.html](binarytree.html)

## 第6章 文字処理
文字処理に関する簡単な問題を例として，有限オートマトンや形式文法などの基本概念を学びます．

### 逆ポーランド記法
逆ポーランド記法をつかった電卓プログラムです． `10×2-1`なら，`10 2 * 1 -`と入力します．

[poland.html](poland.html)

## 第7章 人工知能
人工知能の例として，ゲームのアルゴリズムを考えます． 石取りゲーム(Nim)についは，アルゴリズムとともに，以下のプログラムも示します． 石山が三つあるときに，最後の石を相手に取らせるには，どの山から何個石を取れば良いか，示してくれます．

また，チューリングテストや中国語の部屋といった，哲学的なテーマも紹介します．

### 石取りゲーム
三つの石の山，それぞれの石の数を入力すると，次に山から何個ずつ石をとればよいか計算するプログラムです．

[nim.html](nim.html)

## 第8章 アルゴリズムの限界
決定不能問題 (Yes/Noを決定する問題で，アルゴリズムが存在しない難問題)や，NP完全問題 (答が正しいかどうかは簡単に分かるが，正しい答を効率的に得るアルゴリズムの発明に誰も成功していない問題) の存在など，コンピュータ科学の代表的な理論的成果について簡単に説明します．

また，ライフゲームや結婚問題も紹介します．