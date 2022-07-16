# 07/13

# ABC255B Light It Up

解答状況 TLE　→　AC 

解答時間 40分over 

問題把握：8分 発想確立:13分

備考

➀2点間距離行列作成について

Ans c=np.sqrt(np.sum((a-b)**2,axis=1))




# 07/14

# ABC254B_Practical Computing

解答遷移 AC

(累計時間) 問題把握：3:00　発想確立 6:45 デバック開始 13:00 終了28:00

備考

➀予め配列を作らない場合

box=[],boxes=[]

としてboxes.append(box) + boxを初期化すればよい。これで行数が異なる配列を作ることが可能

➁for i in range(N)

iを満たす数がなければ処理されない。

ex) N=3 で 実行前にi=2のとき。 N=0やrange(1,N)でN=1のとき



# ABC253B Distance Between Tokens

解答遷移 WA(変数間違い) → AC

問題把握 02:17 　発想確立 01:18  baseコード作成 05:27  デバック　07:18  計16:21


# Takahashi`s Failure

解答遷移　AC

問題把握 02:00 発想確立 01:52 baseコード作成 02:21 デバック 03:21  計09:36


# ☆ At Most 3 (Jude ver.)

解答遷移 TLE → 諦め

問題把握 01:30 発想確立 03:34 baseコード作成 23:02 終了 52:01


備考

➀pythonのためにTLE

発想自体は正解例と同じだったが、言語的理由でTLEになった。

この先、同じような事態が発生すればpypyやCを勉強必要がある。

➁range(a,b) (a>=b)

ABC254B_Practical Computingでもあったが、ifで場合分けをしなくともこの仕様を利用して簡単にかけるようにできることがある。

③動的計画法の応用

すべてのパターンを実行して、一行配列の各列にそれらを記録。

appendして not in することで重複を排除する処理よりも早い可能性がある。

④itertools.cominations

combinations(A,n)でリストAから任意にn個取り出したときの組み合わせのiterを作る。

ex) A=[1,2,3,4] n=3 

(1,2,3) (1,2,4) (1,3,4) (2,3,4)ができる。

⑤n以下の取り出し

例えばn=3のとき、1の場合でも２，３の場合でも処理が同じになるようにリストにあらかじめ[0,0]を加えておくことで、[0,0,a]で１つ取り出す状況を表現可能。


# 07/15

➀sys.stdin.readlineの実装

結論：処理速度にほとんど変化なし

➁itertool

処理速度を大幅に改善するものではなさそうなので、解答で気になったら勉強する感じにする。

③ pypy

ancondaでのインストール法を死ぬほど調べたがよくわからなかった。しかし、単にpythonのコードをatcoderにてpypyとして提出することができるのがわかった。

ただし、pythonでギリギリACだったものを大幅に改善することはできたものの、TLEのものを無理やりACにする力はないのかもしれない。要調査


# 07/16

# ABC250B Enlarged Checker Board

解答遷移 WA(出力形式誤り) →　AC

問題把握 04:22 　発想確立 07:05  baseコード作成 15:40  デバック　09:37  計36:46

備考

➀出力形式

ex) ans=[1,2,3]

1, *ans → 1 2 3 (スペース有)

2, "(連結したい文字)".join(ans) → 123(""の場合)

3, [print(ans[i]) for i in range(3)] → 1\n2\n3(改行)

➁文字列結合

("."*3+"#*3)*2 → ...###...### 


③変数範囲について

この問題ではタイルの枚数がN*Nであるが、N=10の有限的条件が使えないか考慮するべきだった。

④偶奇分け

あまり得意な考え方ではないかもしれない。2つの事象が規則的に入れ替わる場合などで特に意識する。

⑤問題設定と発想時間の遅さ原因

2事象(この問題ではマスとタイル)を連動させることを頭で処理することが難しいのかもしれない。そこに行列特有の番号が-1になることが絡み合って余計に時間がかかったと思われる。

解決策案：「行列の番号処理」「2事象の連動理論の早期発見」をできるよう訓練する


# ABC249B Perfect String

解答遷移 AC

問題把握 01:08  発想確立　00:55  baseコード作成 02:26  計05:05 


備考

➀ not in タイプのパターン化ができていると感じるが基本的にそれは模範解答でないことが多い。

今回の場合でもset(S) と　len(S) を比較してSにおける文字の重複をforループなしで検出できている。

➁　大(小)文字判定

1, S.islower() ： Sがすべて小文字でTrue

2, S.lower() : Sをすべて小文字化


#  ABC248B Slimes

解答遷移 AC

問題把握 00:38  発想確立 00:04  baseコード作成 03:59  デバック&提出 00:36 計 05:17



# ABC247B Unique Nicknames

解答遷移 WA →　WA　→ AC

問題把握(誤り)　01:52  発想確立 13:58  baseコード作成 05:07  デバック(発想に誤り) 34:55　計 55:53

備考

➀　題意誤りで生じた遅延

➁ itertoolsitertools.chain.from_iterable() →　多重リストを平坦化

⇅

numpy.flatten()　→　多重配列を1次元配列に

③ リストの結合 A[i+1:]+A[:i] (A[i]を除くAの要素のリスト)

⇅

配列の結合 np.concate([A[i+1:]+A[:i]) 


④　for ループ内において、2条件が異なるiで成立する場合を考える　→　flagで管理

ex) 3で割れる数と4で割れる数がそれぞれ1つ以上存在するか確認したい

flag1=flag2=False

ans="No"

for i in [5,8,11,9]:

  if i%3==0:
  
    flag1=True
    
  if i%4==0:
  
    flag2=True

if flag1 and flag2:

  ans="Yes


