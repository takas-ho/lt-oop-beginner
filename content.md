# 2018.11.7

---

オブジェクト指向プログラミング(OOP)は<br><span style="font-size: 200%;">2</span>種類ある

<br>
今更気付いた <!-- .element: class="fragment" -->

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

1. <span style="color: orange; font-size: 200%;">真</span><span style="font-size: 70%;">オブジェクト指向プログラミング</span>
2. <span style="color: green; font-size: 150%;">手続き型</span><span style="font-size: 70%;">オブジェクト指向プログラミング</span>

---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## <span style="color: green; font-size: 150%">手続き型</span>オブジェクト指向<br>プログラミング

- 私がやってきたプログラミングの<span style="font-size: 200%;">99</span>%はコレだった

<!-- .element: class="fragment" -->

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## <span style="color: orange; font-size: 150%;">真</span>オブジェクト指向<br>プログラミング

- 世の<span style="color: orange; font-size: 150%;">偉人</span>たちの背中は、まだまだ遠い

<span style="font-size: small;">早く人間になりた〜い</span>

Note:
これを目指して励むしかないが、時間には限りがあるので（次）

--

<!-- .slide: data-background-image="./img/IDDD.jpg" data-background-size="40%" style="background-color:rgba(0,0,0,0.5); " -->
<!-- .slide: data-background-position="right" -->

# 技術書読んで実践

<span style="color: orange; font-size: 150%;">偉人</span>たちが残してくれた知見に<span style="color: lime; font-size: 150%;">感謝</span><span style="font-size: small;">の正拳突き</span>

<span style="color: aqua; font-size: 150%;">仕様一覧DB化</span>で実践中

## 乞うご期待！ <!-- .element: class="fragment" -->

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## <span style="color: orange; font-size: 150%;">真</span>オブジェクト指向<br>プログラミングがキマると

うれしい <!-- .element: class="fragment" -->

楽しい <!-- .element: class="fragment" -->

俺サイコー <span style="font-size: small;">ウェーイ</span>

<!-- .element: class="fragment" -->

Note:
ってなわけで（次）
---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## 何が<span style="color: green; font-size: 150%;">手続き型</span>か？

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## <span style="color: green; font-size: 150%;">データ</span>クラスと<br><span style="color: #AA0000; font-size: 150%;">ロジック</span>クラスの分離

<span style="color: green; font-size: 130%;">データ</span>を処理する<span style="color: #AA0000; font-size: 130%;">ロジック</span>が<br>あちこちに散在する

<br>一生懸命DRYを努めたけど、<br>なぜか<span style="color: #008BBB; font-size: 200%;">3000行</span>弱のUIクラスが

<!-- .element: class="fragment" -->

Note:
- これが良くなかった
- 分離するから、それを処理するロジックが散在する
- 3000行が出来上がって無力感に襲われる

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## <span style="color: green; font-size: 150%;">データ</span>クラス

# <span style="color: #AA0000;">Vo</span>や<span style="color: #008BBB;">Collection</span>

Note:
データクラスってのはVoとCollection

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

<span style="color: green; font-size: 150%;">データ</span>と<span style="color: #AA0000; font-size: 150%;">ロジック</span>の場所を分けるから

## 中央集権型の<span style="color: #AA0000; font-size: 150%;">巨大</span>な<br>ロジッククラスに
<!-- .element: class="fragment" data-fragment-index="1" -->

---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

## 何が<span style="color: orange; font-size: 150%;">真</span>オブジェクト指向<br>プログラミングか？

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

<span style="color: lime; font-size: 200%;">データ</span>と<span style="color: lime; font-size: 200%;">ロジック</span>のカプセル化

- データを不変オブジェクト(<span style="color: orange">ValueObject</span>)にして、そのデータ専用のロジックは、<span style="color: orange;">ValueObject</span>のメソッドにする
- `Vo`と`VoHelper`の2人3脚ではなく<span style="color: orange;">ValueObject</span>にメソッドを生やす、定数を生やす

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

<span style="color: orange; font-size: 200%;">ValueObject</span>

- IntegerやString,Dateで表現してた末端の値（ex.部品番号、員数、単価、質量）を<span style="color: orange;">ValueObject</span>にラップする

- 個々にラップした<span style="color: orange;">ValueObject</span>を、いくつかセットして纏めた別の<span style="color: orange;">ValueObject</span>を更に作る、というイメージ
    - 期間は開始日と終了日のセットとか

※<span style="color: orange;">ValueObject</span>はネストできる

Note:
- プリミティブやStringは使っちゃダメなんだよ
- 多分クラス数は跳ね上がる
- そして（次）

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

<span style="color: orange; font-size: 200%;">Collection</span>のカプセル化

- <span style="color: orange;">Collection</span>そのものは公開しない
- <span style="color: orange;">Collection</span>を簡単に増減できないようにする
    - 増減したら別インスタンスにする
    - 不変っぽい動きにする

```vb
Public Class EntityCollection
    Private wrappedList As List(Of Entity)
    Public Function Add(item As Entity) As CollectionObject
        Dim result As New List(of Entity)(wrappedList)
        result.Add(item)
        Return New EntityCollection(result)
    End Function
End Class
```
<!-- .element: class="fragment" -->

Note:
EntityのListを使いたい時にこんな感じにwrapして増減させるAddは公開してもAddした別インスタンスを返す

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

<span style="color: orange; font-size: 200%;">Collection</span>のカプセル化

```vb
Public Class EntityCollection
    Private wrappedList As List(Of Entity)
    Public Sub SetUpdatedItems()
        For Each e As Entity In wrappedList
            e.SetUpdatedItem
        Next
    End Sub
End Class
```

- <span style="color: orange;">Collection</span>操作のロジックをこのクラスに移動する

どんどん操作が増える！ <!-- .element: class="fragment" -->

<span style="color: lime; font-size: 200%;">CollectionObject</span> って呼ぶ

<!-- .element: class="fragment" -->

Note:
- `Collection`を使う側にロジックを書くのではなく、これに直接書く
    - 使う側のコードはシンプルになる
- そして真打ち登場（次）

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

### Hello
# <span style="color: orange;">ドメイン<br>オブジェクト</span>

- <span style="font-size: 150%;">DB</span>や<span style="font-size: 150%;">UI</span>に依存しない、「<span style="color: lime; font-size: 150%;">業務ルール</span>」「<span style="color: lime; font-size: 150%;">仕様</span>」を再現するだけの純粋なクラス

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

# <span style="color: orange;">ドメイン<br>オブジェクト</span>

- <span style="color: orange; font-size: 150%;">真</span>オブジェクト指向プログラミングが<span style="color: lime; font-size: 130%;">発揮</span>できる領域

- <span style="color: orange; font-size: 150%;">真</span>はDB/UIが絡むとやり難くなる

---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

実践中の今のルール

| Project |  |
| --- | ---- |
| Fhi.Fw.DesignSupport<br>┗ Domain | <br><span style="color: orange;">ドメインオブジェクト</span>置き場<br>真OOPで作る |
| DesignSupport<br>┣ Logic<br>┗ Ui | 旧来の書き方から↑↑↑<span style="color: orange;">ドメインオブジェクト</span>を使う |

Note:
- ドメインオブジェクトは、DBやUIを参照しないのでこの場所
- DesignSupport PROJは旧来のUI/Logicがある、その旧来のクラスからドメインオブジェクトを使う

--

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

実践中の今のルール

|| 命名ルール | memo |
| --- | --- | --- |
| <span style="color: orange;">ValueObject</span> | 業務ルールの名前そのまま | BuhinName,<br>BlockNo |
| <span style="color: orange;">CollectionObject</span> | XxxCollection | DetailCollection |
| Entity | XxxEntity | MajorEntity |
|  |  |  |
| Repository | XxxRepository | ( notドメイン ) |
| Factory | XxxFactory | ( notドメイン ) |

Note:
「業務ルールの名前そのまま」ってのはユビキタス言語とかってDDDだと言うみたい

--

<!-- .slide: data-background-image="./img/IDDD.jpg" data-background-size="40%" style="background-color:rgba(0,0,0,0.5); " -->
<!-- .slide: data-background-position="right" -->

けど試行錯誤中なので結果はまた今度

むずい

---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

# <span style="color: orange;">ValueObject</span><br>&<br><span style="color: orange;">CollectionObject</span>

これだけでも大分コードが変わる

Note:
変わる、と言うか変わった

---

<!-- .slide: data-background-image="./img/coding.jpg" style="background-color:rgba(0,0,0,0.5); " -->

# enjoy programming!
