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


# 252B Takahashi`s Failure

解答遷移　AC

問題把握 02:00 発想確立 01:52 baseコード作成 02:21 デバック 03:21  計09:36


# ☆ 251B At Most 3 (Jude ver.)

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

# 250B Enlarged Checker Board

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


# 249B Perfect String

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


# 233B A Reverse

解答遷移  AC

備考

➀ ハードウェアつけてからのPCの重さ&不具合

vscodeは落ちて実装時間測定できないし、githubは保存されないしでふんだりけったり。

➁　文字列とリストの逆順リスト作成

A[::-1]で後前を反転できる


# 232B Caesar Cipher

解答遷移 WA → AC

問題把握　01:12  発想 07:04  baseコード 06:19  デッバク&提出　09:14 (vscode　が落ちて曖昧)  計　23:50


備考

⓪ PCの不具合

➀　WA

コーナーケースの存在は把握できたがうまく処理できなかった。

z → a と b → c を同義に扱えなくてはならないが前者は a-z=-25  c-b=1 のままではそうならないとWAを出すまで気付けなかった

➁　循環するルールにおける余りの優位性

例えば、N=3 a～cを進みcはaに続く場合、a=0,b=1.c=2　進んだ数=xとすれば (期位置+x)%N でどこにたどり着くか調べることができる。


③　ただ一種類のみ条件を満たすとき

ans=[]　に出力を追加し、set(ans)==1なら条件達成とできる



# 231B  Election

解答遷移　AC

問題把握 00:29  発想　00:59  baseコード作成 06:04 デバック&提出 03:42  計 11:16

備考

➀ X=llections.Counter(x)の最頻値

X.most_common()にて(元の要素,出現回数)のタプルが要素になったリストが作成できる。またこれは出現回数の降順になっているので最頻値はX.most_common()[0][1]にて取得可

➁ zip (この問題に関係ないが)

zip(A,B)でAの要素とBの要素を要素にしたiterを作成する。長さはA,Bと同様。

例) AとBの要素を同時に取り出すfor ループ  for  a,b in zip(A,B):

これは[(A0,B1),(A1,B1) .....]が作られ、そこから順に(Ai,Bi)が取り出され、a=Ai b=Biになり以降の処理を行っている。




# 230B TripleMetre

解答遷移 WA → AC

問題把握　00:54  発想確立　05:22  baseコード作成 06:47  デバック&提出 06:13  計 19:17

備考

➀ 文字列の部分集合

S in T でSがTの部分集合かどうか判定可能




# 229B hard Caluculation

解答遷移　RE*2 → AC

消してしまったが、➀に記載したroundのatcoder側の仕様を知らなくて30分程度要した

備考

➀　小数の切り捨て

int(),//,math.floor()など。ただし、intは０に近づけるように丸めるが//はガウス。負値において違いが生じる

ex) -130//10=-14,int(-130/10)=-13

roundは偶数丸め(14.5 → 14)のように境界で偶数になるように丸める

また、atcoderの環境ではなぜかnumpuyで求めた値をroundで丸めてもfloat型になってしまう。


➁ 整数の各桁の数字を評価

1. %10 → //10 を繰り返して各桁の数字を取得

2, f"{s:0x}" 0埋めしてx桁にＭなるように調整した文字列として取得





# 07/21 


# 228B Takahashi`s Secrtet

解答遷移 WA → AC

問題把握 02:03 　発想 03:42 baseコード 06:37 デバック&t提出 05:16  計 17:40

備考

➀　1<=i<=Nのとき　index番号と合わせるためにリストの先頭に[0]を付け加える調整をほどこすことができる


# 227B KEYENCE building

解答遷移 AC

問題把握 01:26  発想　06:29  baseコード 08:04  デバック&提出 00:30 　計 16:29

備考

➀ 実装速度と曖昧さ

今回ｍループの上限を計算で求めたが、計算量に余裕があれば適当な大きい値を入れて実装時間を短く済ませることもできた。


# 226B 

解答遷移 TLE*2 → AC

問題把握　01:47 　発想 04:34  base 15:52  発想変更*2含むデバック&提出 17:51  計15:52


備考

➀　リストはset化できないが、tupleであれば使用を知らずリストで試してこの方針をやめてしまった。

➁ *

1, 残りの要素のアンパック a.*b=list("tsuru") b=["s","u","r","u"]

2, 関数に各要素を一度に代入する　print(*A) これはprintが可変数の入力をスペース区切りで出力する関数であるためである

![image](https://user-images.githubusercontent.com/109026838/180125030-2b12b427-25bd-4ad5-8e9c-8d461f363ad7.png)


 # 225B Star or NOt
 
解答遷移 AC

問題把握 03:14   発想 00:00   base 04:15   デバック&提出 02:11  計 09:42


備考

なし



# 224 Mongeness

解答遷移 WA → AC

問題把握 03:54  発想 03:46  base 03:14  デバック&提出 14:58  計 25:54


備考

➀ itertools.combinations はイテレータ

A=itertools.combinations(range(3),2)


for x in range(2)
  
  for i, j in A
  
    print((i, j)
    
とすると、(0,1) (0,2) (1,2) が一度しか出力されない。2回目のループでも出力するならば再度作りなおす必要がある。

なのでAを作らずinにそのまま突っ込むのが良いと思われる。





#  255 Light It Up 2回目

解答遷移 AC

問題把握 00:54  発想 05:48  base 08:43  デバック&提出 02:39  計 18:07


備考

➀ 発想の変化

模範解答を作成する能力の向上を実感した。しかしながら1回目の自由な発想によるforループ1回の実装もすばらしいと感じた。numpyを使わなくなった弊害か
























