# 07/13

# ABC255B Light It Up

解答状況 TLE　→　AC 

解答時間 40分over 

問題把握：8分 発想確立:13分

備考

➀2点間距離行列作成について

Ans c=np.sqrt(np.sum((a-b)**2,axis=1))

* 7/20 追記(234B後の見直しによって修正)

これは原点からの各点の距離を求める場合にのみ限定される。


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


⑤ 2条件の and or ,not の処理に時間がかかっているかもしれない

→ 条件成立状況と非成立状況を考え、breakするにはどちらが適切かしっかり考える



# ABC245B Mex

解答遷移 Re*3 → AC

問題把握 00:40 　発想確立 02:29  baseコード作成 02:08  デバック　11:07  計16:25


備考

➀ コーナーケース漏れ

今回ではansという変数がコーナケースの場合に定義されていないことで漏れを気づくことができたはず。


➁ 境界の簡易化

この問題のコーナーケース　N=3 A=[0,1,2] の場合、Aの要素としてありえない数3000を何個かAに追加することでi=Nを調べることが可能になる




# 244B Go Straight and Turn Right

解答遷移 AC

問題把握 01:22  発想確立  01:21  baseコード作成 03:22  デバッグ&提出 01:05  計 07:11


#  246B Get Closer

解答遷移 AC

問題把握 01:00  発送確立 00:41  baseコード作成 03:31 デバック&提出　01:49 計07:03

備考

➀複素数型

Z=a+b*1j　によって複素数の表現が可能 abs(Z)により大きさを算出することもできる。複素数通しの演算(掛け算等)も可




# 243B Hit and Bit 

解答遷移 AC

問題把握 01:06  発想確立 01:59  baseコード作成 02:14  デバック&提出01:33 計06:53


備考

➀ 計算量 Cで1秒間に10**8程度処理するらしい。よって今回のN=1000における(N^2)はいけそうだと発想段階で考察できる。逆にO(N^3)となるとTLEだろうと判断できる


➁ len(set(A)&set(B))によって二つの集合A,Bに共通する要素の数がfor ループなしで出力できる。

ここからfor i in range(N) if A[i]==B[i] によって求めた位置も同じ要素の数を引くことでこの問題を解凍できる。

また、辞書化することでもfor ループを一つなくすことが可能。

Bの要素をkeyに、indexを要素にした辞書を作り、Aの要素がBのkeyのどれかに一致する場合にB_dict[A[i]]がiに一致しなければ位置が異なるcountを+1する処理によって実現できる。


# 242B MinimizeOrdeing

解答遷移 TLE → AC

問題把握 03:37 発想確立 04:02 baseコード作成　14:34  別コード作成&提出 06:32  計28:46


備考

➀ Nはmax 2*10**5であるので2重ループはできないと発想段階で考えておかなくてはならなかった。

➁ 文字列もsortできる


# 241B Pasta

解答遷移 AC

問題把握 01:54  発想確立 02:10  baseコード作成 02:40  デバック&提出 00:59  計 07:45

備考

➀ リストAから要素aを削除  A.remove(a) (破壊的処理)

➁ collections.counter

B=collections.counter(A)によってAの要素をkeyにその頻度をvalueにした辞書っぽいcounterBを作成できる。

辞書と違って存在しないkeyにアクセスでき、その場合0が返る。


* 07/17 A問題後 追記

辞書の場合は not in  key により存在しないkeyにアクセスする場合の処理が可能。辞書を扱うときに混在しないようにcounterの場合もこのように操作するべきかもだが、0が返ってくるメリットすごすぎるので使い分けられるようにする。




#　240B Count Distinct Integers

解答遷移 AC

問題把握 00:11 発想確立 00:00   baseコード作成 00:43  デバック&提出 00:43  計 01:38




# 07/17

# 239B Integer Division

解答遷移 AC

問題把握 00:41  発想確立 01:00 baseコード作成 01:36  デバック&提出  00:17



# 237B 

解答遷移 AC

問題把握 00:51  発想確立  00:02  baseコード作成 01:54  デバック&提出 01:30  計 04:35



# 236B Who is missing

解答遷移 AC

問題把握 01:51  発想確立 00:00  baseコード作成 05:46(collectionsの使用が曖昧でデバックもやってた)  デバック&提出 00:11  計07:49



#  07/17 ABC 

# A  A Unique Letter

解答遷移 AC　解答時間 05:13

# B  Better Student Are Needed!

解答遷移 AC  解答時間 69:47

備考

➀　リスト操作における未熟さからの大幅なtime loss

特定の要素を除いた中で最も大きい要素のindexが知りたい！！！

A,特定の要素を除いた中で → 1, その要素を除いた新しいリストを作成  or 2, その要素にアクセスしない

1の方しか頭に浮かばなかった。

B, 最も大きい要素のindex　→ 1, sorted([要素,index]reverse=True)  2, for i in range(N): if[tmp] < [i] tmp=i

3, リストを編集してMax()


➁ 二重リストのsort 

要素であるリスト同士のi=0における大小で決定し、等しい場合にはi=1以降の大小関係を参照する。


③ ループの目標に応じた使い分け

for はループを指定した回数だけ確実に行いたい場合に扱う。whileは条件を指定し、それを満たすまでの回数がわからなくても条件達成までループを処理したい場合に扱う。


④ 処理速度問題

for ループの回数が同じにもかかわらず、２つのコードの処理速度に大きな違いが生じた。

考察

➀リストや変数の数の違い？　→ 入力の工夫等でやらせないか





# 07/20 

# 238B Pizza 

解答遷移 AC

問題把握 01:08  発想確立  10:11  baseコード作成  10:41  デバック&提出 00:20  計  22:21


備考

➀　コード作成の遅さ

単純な1重ループを何回か処理するだけのコードに10分を要した。range(N)における最後のindexが何なのか、Nの値が増減するだけで細かな確認を繰り返したことが原因。また新しいリストを作るたびにデバックしたのも原因。

デバックは最後にまとめてbaseをさっさと完成させる方がよいか？




# 235B Climbing Takahashi

解答遷移  AC

問題把握 01:02  発想確立 00:17  baseコード作成  02:57  デバック&提出 01:53  計 06:10



#  07/20

# 234B Longest Segment

解答遷移 AC

問題把握 00:56  発想確立  00:00  baseコード作成 05:34  デバック&提出 00:36 　計 07:07


備考

➀　速度ボトルネック

この問題では入力におよそ2分程度費やしてしまった。冷静に考えればよくある形式だったのだが、一度整理しなおさないと誤った思考が解消しない状態に陥ってしまった。

➁ itertools.combinations(iter,r=n)

N<=100だったので二重ループで全探索しても問題ないと思い脳死で重複を含めた処理を行ったが、2点を選ぶ方法はnC2の組み合わせである。そこで今回ではfor i,j in itertools.combinations(range(N),2):こうして1回のループで処理してしまうべきだった、

③ if x>ans : vs ans=max(ans,x)

意識しないと前者になってしまう。(いまのところ問題ないはずだが、max処理も頭に浮かべられるように注意

④ np.sqrt = **0.5

わざわざnumpy使わなくてよい






















