# HTMLについて

## viewport

基本は、

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

で、拡大と縮小をさせたくない時は、

```
<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
<style>
  body {
    -webkit-text-size-adjust: 100%;
  }
</style>
```

を設定します。


## normalize.css と reset.css

```
<link rel="stylesheet" href="css/normalize.css">
```

または

```
<link rel="stylesheet" href="css/reset.css">
```

好みというか用途で使い分けましょう。


## IE8以下対応

```
<!--[if lt IE 9]>
  <script src="vender/html5shiv.js"></script>
  <script src="vender/css3-mediaqueries.js"></script>
<![endif]-->
```

できれはIE8以下は含めたくないですな。


## 計測・リマーケなどのタグ関係

グーアナさん。

```
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
  ga('create', 'UA-XXXXXXXX-Y', 'example.com');
  ga('send', 'pageview');
</script>
```

普段はGoogle Tag マネージャが便利なのでこれにまとめてます。

```
<noscript>
  <iframe src="//www.googletagmanager.com/ns.html?id=GTM-XXXXXXXX" height="0" width="0" style="display:none; visibility:hidden"></iframe>
</noscript>
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src='//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTM-XXXXXXXX');</script>
```

Yahoo タグマネージャーは使ったことがないのでわかりません。


## コンテンツ本体

```
<header role="banner">
  <h1></h1>
</header>

<nav role="navigation">
  <ul>
    <li></li>
  </ul>
</nav>

<main role="main">
  <article>
    <header>
      <h1></h1>
    </header>
    <p></p>
    <section>
      <h2></h2>
      <p></p>
    </section>
    <footer>
      <h1></h1>
    </footer>
  </article>
</main>

<aside rlole="complementary">
</aside>

<footer role="contentinfo">
  <small>Copyright &copy;</small>
</footer>
```

最低限これだけは。ってものを書きました。

## SNS

```
<meta name="description" content="">
<meta name="keywords" content="">
<meta name="author" content="">
<meta property="og:title" content="">
<meta property="og:type" content="website">
<meta property="og:url" content="http://<URL>">
<meta property="og:image" content="http://<URL>/og_image.png">
<meta property="og:site_name" content="">
<meta property="og:description" content="" />
<meta property="fb:app_id" content="">
```

と

```
<!-- Twitter -->
<a href="http://twitter.com/share?url=<URL>&text=<text>&via=<ID>" target="_blank">Twitter</a>

<!-- Facebook -->
<a href="http://www.facebook.com/share.php?u=<URL>" onclick="window.open(this.href, 'FBwindow', 'width=650, height=450, menubar=no, toolbar=no, scrollbars=yes'); return false;">Facebook</a>

<!-- Hatena -->
<a href="http://b.hatena.ne.jp/add?mode=confirm&url=<URL>&title=<title>">Hatena</a>

<!-- Google+ -->
<a href="https://plus.google.com/share?url=<URL>" onclick="window.open(this.href, 'Gwindow', 'width=650, height=450, menubar=no, toolbar=no, scrollbars=yes'); return false;">Googel+</a>

<!-- Pocket -->
<a href="http://getpocket.com/edit?url=<URL>&title=<title>" onclick="javascript:window.open(this.href, '', 'menubar=no, toolbar=no, scrollbars=yes, height=300, width=600'); return false;">Pocket</a>

<!-- Feedly -->
<a href='<a href="http://cloud.feedly.com/#subscription%2Ffeed%2F<URL>" target="_blank" style="cursor:help;display:inline !important;">http://cloud.feedly.com/#subscription%2Ffeed%2F<URL></a>' target='blank'>Feedly</a>

<!-- LINE -->
<a href="http://line.me/R/msg/text/?<text><URL>">LINE</a>
```

使うものだけチョイスして、`<URL>`、`<text>`、`<ID>`を書き換えます。


# CSSについて

## SMACSS

ページ内のオブジェクトを5つのカテゴリに分類してスタイルを定義します。

* Baseカテゴリ
    - 各要素のデフォルトのスタイルを定義
    - リセットやノーマライズなど
* Layoutカテゴリ
    - セクション、コンテンツエリアのスタイルを定義
    - プレフィックス'l-'
* Moduleカテゴリ
    - 個々のモジュールのスタイルを定義
* Stateカテゴリ
    - オブジェクトの状態の変化を定義
    - メディアクエリ等
    - プレフィックス'is-'
* Themeカテゴリ
    - テーマを定義
    - プレフィックス'theme-'


## メディアクエリとブレイクポイント

```
@media only screen and (min-width: 769px) {
  タブレット用
}
@media only screen and (min-width: 961px) {
  PC用
}
```

ブレイクポイントの設定は難しいけど上のが一般的っぽいのかも？


## フルードグリッド

```
body {
  width: 100%;
}
```

この時、子要素の横幅の指定は、

```
固定レイアウト時の要素の横幅 ÷ 固定レイアウト時の親要素の横幅 ✕ 100
```

で算出できます。


例） 横幅940pxのbodyの中に、main要素740px、aside要素180pxの2カラムが存在する固定レイアウトを可変レイアウトにするには

```
main {
  /* 740 ÷ 940 ✕ 100 */
  width: 78.7%;
}
aside {
  /* 180 ÷ 940 ✕ 100 */
  width: 19.1%;
}
```

## フルードイメージ

```
img {
  max-width: 100%;
  height: auto;
}

/* 背景をフルードイメージに */
.background {
  background-size: cover;
}

/* メディアをフルードメディアに */
embed, object {
  max-widht: 100%;
}
```

# その他レスポンシブデザインで気をつけること

## ボタンデザイン

レスポンシブデザインでのボタンデザインは最小サイズ44px以上でデザインすること。

## JavaScriptのタッチイベント

* touchStart
* touchMove
* touchEnd

を上手く使うこと。

## Retinaディスプレイ対応

Retinaディスプレイに画像を対応させる方法3つ。

1.表示させるサイズの四倍の大きさの画像を作る

2.image-set関数で画像を振り分ける

```
セレクタ {
  /* devicePixelRatioが1の時は小さい方、devicePixelRatioが2の時は大きい方 */
  background: -webkit-image-set( url(小さい方の画像), url(大きい方の画像) 2x);
  /* -webkit-image-setに未対応の時 :/
  background: url(...);
}
```

3.devie-pixel-ratioで対応する

```
/* 低解像度用 devie-pixel-ratio非対応ブラウザ用 */
セレクタ {
  background: url(low.jpg);
  height: 100px;
  width: 100px;
}

/* android用 */
@media only screen and (-webkit-min-device-pixel-ratio: 1.5), only screen and (min-device-pixel-ratio: 1.5) {
  セレクタ {
    background-size: 100px 100px;
    -webkit-background-size: 100px 100px;
    background: url(middle.jpg);
  }
}

/* 高解像度用 */
@media only screen and (-webkit-min-device-pixel-ratio: 2), only screen and (min-device-pixel-ratio: 2) {
  セレクタ {
    background-size: 100px 100px;
    -webkit-background-size: 100px 100px;
    background: url(high.jpg);
  }
}
```

## 参考

以下の書籍と記事を参考にさせていただきました。

> [Amazon.co.jp： レスポンシブWebデザイン「超」実践デザイン集中講義: 山崎 大助: 本(http://www.amazon.co.jp/exec/obidos/ASIN/4797373539/)

> [HTMLのテンプレート的なの - Qiita](http://qiita.com/matsui_q/items/8d26f66ded3560d3d004)

> [twitter/Facebook/LINEのシェアボタンのカスタマイズ方法 - Qiita](http://qiita.com/rico/items/a8ec7626e357ff34570b)

> [SNSボタンをカスタマイズ！はてなブログにオリジナル画像のSNSボタンを設置する方法 - iPhoneのこととかいろいろ](http://www.kototoka.com/entry/2014/07/24/hatena-blog-customizing-original-design-the-buttons-of-sns/)

> [[HTML5] 新要素まとめ【2014/2/14版勧告候補】 - Qiita](http://qiita.com/maccotsan/items/20c6ea274b0190dc2c05)

> [レイアウトで使うランドマークのrole属性【アクセシビリティ】【WAI-ARIA】 - E-riverstyle Vanguard](http://blog.e-riverstyle.com/2011/01/rolewaiaria.html)