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

* 追記 0723 ABC182C解答後

joinは文字列のリストの要素を追加する。このansなら"".join(map(str,ans))として"123"を出力できる

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




# 240B Count Distinct Integers

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





# 07/19

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

➀ X=collections.Counter(x)の最頻値

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

int(),//,math.floor()など。ただし、intは０に近づけるように丸める。//はガウス。負値において違いが生じる

ex) -130//10=-14,int(-130/10)=-13

roundは偶数丸め(14.5 → 14)のように境界で偶数になるように丸める

また、atcoderの環境ではなぜかnumpuyで求めた値をroundで丸めてもfloat型になってしまう。


➁ 整数の各桁の数字を評価

1. %10 → //10 を繰り返して各桁の数字を取得

2, f"{s:0x}" 0埋めしてx桁になるように調整した文字列として取得





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

今回ループの上限を計算で求めたが、計算量に余裕があれば適当な大きい値を入れて実装時間を短く済ませることもできた。


# 226B Counting array

解答遷移 TLE*2 → AC

問題把握　01:47 　発想 04:34  base 15:52  発想変更*2含むデバック&提出 17:51  計15:52


備考

➀　リストはset化できないが、tupleであれば使用を知らずリストで試してこの方針をやめてしまった。

➁ *

1, 残りの要素のアンパック a.*b=list("tsuru") b=["s","u","r","u"]

2, 関数に各要素を一度に代入する　print(*A) これはprintが可変数の入力をスペース区切りで出力する関数であるためである

![image](https://user-images.githubusercontent.com/109026838/180125030-2b12b427-25bd-4ad5-8e9c-8d461f363ad7.png)


 # 225B Star or Not
 
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





#  255B Light It Up 2回目

解答遷移 AC

問題把握 00:54  発想 05:48  base 08:43  デバック&提出 02:39  計 18:07


備考

➀ 発想の変化

模範解答を作成する能力の向上を実感した。しかしながら1回目の自由な発想によるforループ1回の実装もすばらしいと感じた。numpyを使わなくなった弊害か。



# 256 Practical Computing　2回目

解答遷移 AC

問題把握 02:10  発想 00:12  base 05:16  デバック&提出 00:30  計  08:08  


備考

なし


# 253 Distance Between Tokens 2回目

解答遷移 AC

問題把握 01:30  発想 00:19  base 04:36 デバック&提出 00:42  計 07:08

備考

➀ 今回初めて"o"を見つけたときが初めてか否かflagで管理したが、リストにappendして管理するのが綺麗。



#  250B Enlarged Checker Board 2回目

解答遷移 AC

問題把握 03:38  発想 02:34  base 03:50  デバック&提出 02:18  計 12:22

備考

➀ S[i][0]"."のときに、S[i]=("."*B+"#"*B)*(N//2)+("."*B)*(N%2)としたが、N<=10であるのでS[i]=("."*B+"#"*B)*N/2として後から必用な長さ(B*N)だけスライスで取り出すこともできた。




# 247B Unique Nicknames 2回目

解答遷移 WA　→ AC

問題把握 00:58  発想 02:11  base 06:18  デバック&提出 08:57  計 18:25

備考

➀ リストの平坦化　itertools.chain.from_iterable(A)




#  245B Mex 2回目

解答遷移 RE → AC

問題把握 00:24  発想 00:47  base 02:51  デバック&提出 10:26  計 14:30


備考

➀ rangeの範囲を誤った。その結果存在しないindexにアクセスしてしまうパターンがあった。(range(N)としてしまうと0 0 1 2 3 などの場合ではエラーが生じる)

➁ for i in range(N)として iがsetにないとしてもよかった。

③ set(range(N+1))の集合を作り差集合の最小値をとる方針もよい。Sの差集合なので必ずS-とすること。




# 241B Pasta 2回目

解答遷移 AC

問題把握 01:00  発想 00:29  base 03:09 　デバック&提出 00:56  計 05:35



# 0722 

# 223B String Shifting

解答遷移 AC

問題把握 01:16  発想  04:34  base  03:52  デバック&提出 03:29   計 13:12

備考

➀　文字列は大小関係を比較できるのだから、max,minも使える

➁ >>はbit右シフトで//2の意味



 # bit全探索
 
➀　 N=20くらいが限界。
 
➁　itertools.product

product(A,B) 

for a in A:
  for b in B:
    return (a,b)
   
 になる。例えばA="AB" B="XY" であれば("A","X"),("A","Y"),("B","X"),("B","Y")が返る。
 
 またproduct(A,repeat=3)はproduct(A,A,A)と同義。例えばproduct((0,1),repeat=2)で(0,0),(0,1),(1,0),(1,1)が返る。
 
 




# 190C Bowls and Dishes

解答遷移 AC

問題把握 time測定失敗  発想 03:02  base 09:31  デバック&提出  07:25  計 ? + 19:59


備考

➀発想

dpは無理そうだな → K<=16で皿CにおくかDにおくかの2通りをbit探索できそうだと感じて舵を切った。

➁　問題が1から始まる番号を設定している時

問題の値を-1してリストに入れる or 1つサイズの大きなリストを作成してそのまま入れる

③ 入力でtupleを要素にしたいときはtuple(int(a) for a in input().split())とすればよい




# 167C Skill Up

解答遷移 AC

問題把握  01:36  発想  06:30  base  09:48  デバック&提出  10:14  計 28:09


備考

➀　対象アルゴリズムが1つだけならdpでいけそうだが、複数だったのでおとなしくbit探索した。

➁ map(fuc,iter) iterの要素すべてにfuncを適応したiterを返す



# 182C To 3

解答遷移 AC

問題把握 01:35  発想  03:32  base & デバック 28:09  計 33:18


備考

➀　joinは文字列のリストでのみ扱える。要素に文字列以外があればmapするなどして変換が必用。



# 128C Switches

解答遷移 AC

問題把握 01:54  発想 03:57  base  14:24  デバック&提出 03:39  計 23:54


備考

➀　デバックのほとんどが変数間違いの修正だった。s,lではなくswitch,lightなど判別容易な名前を設定すべきかもしれない



#  137C H and V

解答遷移 AC

問題把握  04:33  発想 04:55  base  08:49  デバック&提出  10:06  計  28:25


備考

➀ 入力文字列をリストに変換　→ list(input())



#  222B Failing Grade

解答遷移 AC

問題把握 00:37  発想 00:22  base 02:07  デバック&提出  04:12  計 04:12


備考

なし




#  0723

# 260A  A Unique Letter 2回目


解答遷移 AC

問題把握 00:14  発想 00:00  base 03:14   デバック&提出  00:35  計 04:04


備考

➀　最頻値を用いて解いたが、valujeが1のものがあればansにkeyを代入してbreakする方針も可能


#  259A Growth Record　2回目

解答遷移 AC

問題把握  01:38  発想 00:02  base 03:24  デバック&提出 00:28  計 05:34


備考

➀　ボトルネックはコード作成フェーズに見えるが、普通にここでも紙で立式してたのでコード入力にのみ費やしているわけではない。


# 258A When?　2回目

解答遷移 WA AC

問題把握 00:38  発想 00:00  base 01:27  デバック&提出 01:35  計 03:42


備考

➀ 境界での誤り if K>60 HH=22 としてしまった 



# 257A A to Z String2

解答遷移 WA AC

問題把握 00:15  発想 00:00  base 03:32  デバック&提出 05:11  計 09:00


備考

➀大文字小文字変換 S.upper()でSを大文字の文字列に変換できる

➁ 2事象の連動を上手に考えられず、index番号と問題の数え方のズレを考慮した解法をなかなか作成できなかった。

X=index+1より X-1//Nで前から



# 256A 2^N

解答遷移 AC

問題把握 00:04  発想 00:00  base 00:10  デバック&提出  00:18   計 00:34


備考

なし



# 255A You should output ARC thorough this is ABC

解答遷移 AC

問題把握 00:17  発想 00:00  base 00:56  デバック&t提出  00:20  計 01:33

備考

なし



# 254A Last Two Digits


解答遷移  AC

問題把握 00:22  発想 00:00  base 01:22  デバック&提出 00:29  計 02:13


備考

➀ 桁数の調整(右寄せ、左寄せ)

S=101 のとき f"{S:0N (or0=N)}"でN桁になるように左からで埋めたSが出力できる 例えばN=5なら00101

またf"{S:>N}"とすればSを出力した後、N桁までの不足している個数スペースされる。f"{S:<N}"であれば先にスペースが出力され最後にSを出力してN桁になるような調整となる。

またNがlen(S)以下の場合、普通にSが出力される。

この問題ではS="101"文字列で入力しS[-2:]としても下二桁の文字列が返る。なお文字列はf_stringで桁を弄れない。整数or小数のばあいに限られる。



➁ 文字列の結合

文字列+文字列 ,　リスト+リストはできてもリスト+文字列は結合できない。




# ABC253A Median

解答遷移 WA  AC

計測ミス

備考

➀ A<B<Cの場合のみしか考えられなかった。リストの3要素の中央値はsorted()[1]で得られる。




# 0724


# 252A ASCLL code

解答遷移 AC

問題把握 00:24  発想 00:00  base 01:16  デバック&提出  00:24  計 02:05


備考

➀ アルファベットと整数の関係

ord(xx)でアルファベットxxに対応するASCII code(int型 整数)が出力できる。また逆にchr(XX)でASCII code XXに対応するアルファベットが出力できる。

![image](https://user-images.githubusercontent.com/109026838/180619131-d21b72f9-9683-4ad9-a4f3-73af9b387cd0.png)

1桁の整数文字列に対応したコードも存在するようである。





#  251A Six Characters

解答遷移  AC

問題把握 00:51  発想 00:00  base 00:53  デバック&提出 00:33  計 02:18


備考

➀　過剰作成→必要分取得パターンで条件処理を回避

S=input() SS="*10とすればSの長さによらず条件を満たす文字列を先頭にした文字列が出力できる



 
 # 250A Adjacent Squares
 
 解答遷移  AC
 
 問題把握  01:34  発想  00:00  base 03:55  デバック&提出  00:32  計 06:03
 
 
備考

なし




# 249A Jogging


解答遷移 WA AC

問題把握+発想 02:01   base 08:26  デバック&提出  02:41   計13:09

備考

➀ コード作成経緯

リストを作成し、%(A+C)で進んでいるか休んでいるか区別したい　→ よってZ秒経過後に対応するindexはZ-1になるような長さのリストを作る。今、X<=100なのでinde:0-99の長さ100のリストを作成。

ここでX秒経過後の距離が求めたいのでX-1までの要素の和を求める → sum([:X])


➁time loss

発想時点でのコードが正解を求められなそうだと感じ、さまざまな検討をしたことで時間的な遅れをとってしまった。

これはコーディング力というよりも解法力が足りないということだと思う。

ただindexの設定にもてこずった。ゆっくり考えればできるのだが、まだ高速で処理する力を持っていない。せっかく過剰に作成したものから必用なだけ得る解放を思いついたのに、その範囲の道程に時間をとられるのがもったいないと感じる。



③ 忘却

想定より時間をかけているあせりから、X秒後までという設定を失念して100秒後までの距離を出力してしまった。


結論

時間があれば模範解答を作成できるが、制限下で処理する能力が不足している。



# 248A  Lacked Number

解答遷移  AC

問題把握&発想　02:10  base &デバック 01:53  計 04:04


備考

➀　文字列のint化 およびリスト化

例えば S="0123456"　のとき int(S)=123456 にって先頭のは消滅する。またそのままlist(S)としても要素は文字列型になる。

整数型にしたい場合は list(map(int,S))とすること



# 247A Move Right

解答遷移 AC

問題把握&発想 01:02  base 01:07  デバック&提出 02:36  計 04:46


備考

➀ >> の出力は10進数。1001(10)>>1が100になるわけではない。

➁文字列のスライスはリストではない! 0埋めしたい場合などには"0"*Nを足す。ループの回数に対応した処理が必要な場合はfstringも便利



#  246A - 243A

計測結果および備考データ消滅



# ☆ 242A T-shirts

解答できず


備考

➀ nCrはn次第で簡単に計算量が莫大な数になってしまう。例えば100C5は 75,287,520 となり10**8を超える。

この問題は0<A<B<1001で n=B-Aは100を超える可能性がある。よってitertools.combinationsでループを回したりlen()で長さを求めることはできない


from scipy.special import comb　のcomb(n,r)によってnCrが計算できる。(atoder 環境でもscipy.special.combは使用可)




# 241A Digits Machine

解答遷移 AC

問題把握　01:10  発想  00:09   base 00:46  デバック&提出  00:36  計02:43


備考

なし


#  240 A Edge Checker

解答遷移 AC

問題把握  00:19  発想  00:00  base : 01:08  デバック&提出  04:37  計 06:06


備考

➀ a<b である。abs(a-b)とする必要はない

➁ 循環型なので条件設定を施すことなく余りでの分類を目指したが、10とセットの1と ２とセットの１が区別できなかったので、この場合は単純にコーナーケースのための条件を追加するのがよいと思われる。


# 239A  Horizon

解答遷移  AC

問題把握  00:21  発想  00:01  base 00:51  デバック&提出  00:18  計 01:30


備考

なし




# 238A Exponential or Quadratic

解答遷移 TLE  AC

問題把握　　00:05  発想 00:00  base 00:34  デバック&提出 03:06  計  03:47


備考

➀ 巨大な数の扱い

巨大な数はただ単純に扱うだけでも時間がかかってしまう。x**(10**7)になると処理が終了しない



# 237A Not Overflow

解答遷移 WA AC

問題把握  00:17  発想 00:00  base  00:44  デバック&提出 02:23  計 03:25


備考

➀打ち間違い -2**32としてしまった。




# 0725

# 221B typo

解答遷移  AC

問題把握  00:34  発想  03:16  base 07:57  デバック&提出  計 12:41


備考

➀文字列は要素の入れ替えができない　たとえばname="tsuru"のときname[0]="T"とすることはできない。

list(name)でリスト化するか、文字列のまま name="T"+name[:1]とすればよい。




# 220B  Base K 

解答遷移 AC

問題把握 00:19   発想 01:14  base 01:05  デバック&提出 00:24  計 03:03


備考

➀ int(X,base=N) で文字列XをN進数の整数に変換する。baseを指定しない場合Xは整数でもよいが、baseを明示している場合は文字列型である必要がある。




#  219B Maritozzo

解答遷移 AC

問題把握  01:34  発想 00:11  base 04:57  デバック&提出 00:32  計  07:16


備考

S=[S1,S2,S3]として　S[T[i]-1]で取り出せば条件を設定せずに済む。


# 218B qwerty

解答遷移 AC

問題把握 00:34  発想 00:00  base 02:01  デバック&提出 05:04   計  07:40


備考

➀　ord(XX) はアルファベットXXに対応するアスキーコードが出力され、chr(xx)はアスキーコードである整数xx二対応するアルファベットが出力される。小文字では"a","b","c"...が97,98,99...に対応している

したがって、この問題では1<=pi<=26なので S[P[i]-1 +97]とすることでabcdefg...と123456..が対応するようになる。

➁文字列結合とリストのjoin

前者は遅いらしく10**3繰り返すくらいになると後者が推奨されるようである。



# 217B AtCoder Quiz

解答遷移  AC

問題把握  00:09  発想 00:00  base 02:14  デバック&提出 00:24  計 02:49


備考

なし



# 261A  Intersection 復習

解答遷移  AC  終了時間  05:31

➀ A Bの共通区間をA&Bで考える。共通区間の長さはA&Bがから出ない場合、要素数つまりlen(A&B)-1であり、空の時は0になる。空か否か条件分岐せずともmax(0,len(A&B)-1)とすることで解を得られる。


# 261B Tournament Resultbn 復習

解答遷移 AC  終了時間 14:56

➀ トーナメント表AにおけるA[i][j]とA[j][i]が(W,L)か(L,W)か(D,D)であるか調べる。D-0,W=1,L=2とすれば正しい組み合わせの時にA[i][j]+A[j][i]%3=0になることを利用して条件分岐を設定せずに美しいコードがかける。

(どうして時間を競ってる本番でこの処理ができたのか不明)

# 262C NewFolder(1)  復習

解答遷移 AC  終了時間  06:51 

なし


# 216B Same Name

解答遷移　AC

問題把握 00:48  発想 00:00  base 03:15  デバック&提出 00:28  計  04:32


備考

➀ 問題を見てsetが使えそうだとかcounterはどうかといろいろ思案したが、time優先で脳死ループした。計算量も問題なかったため。

➁ 2重ループと組み合わせ

for i in range(N) for j in range(j)　でNC2通りの処理を実現




# 0726

# 215B Log2(N)

解答遷移 WA WA AC

問題把握&発想 01:34  base 01:00  デバック&提出 09:23  計 11:58


備考

➀　計算精度

N=2**50-1 において log(N)/log(2)は49.9999999....のように決して50にはならないが限りなく近い数として表されるはずであるが50が出力されてしまう。理由はpythonは小数点15桁付近で丸めこみが生じるので、それ以降の桁数での差が消滅してしまうためである。大きすぎる値を扱う場合には注意が必要

![image](https://user-images.githubusercontent.com/109026838/180994732-90cb44b3-d2f4-4eed-83d1-2ff2bae05e5d.png)



➁ bit演算による桁数の判定

10^N≦X<10^(N+1)を満たすXの桁数はN+1である。同様に,2^N<=X(2)<2^(N+1)を満たすX(2)の桁数は(N+1)である。

またX>>i&1を満たすiの最大値はXの桁数-1である。(i=0が1桁目に対応するため)

以上よりX>>i&1の最大値iと2**N<=X(2)を満たすNの最大値は一致する。


③ 桁数の表現

対数をとることでその整数の桁数を表現してきたが、シンプルにlen(str(X))としたり、len(bin(X))-3で桁数を表現できる。




# 214B How many?

解答遷移　AC

問題把握&発想 08:19  base 02:23  デバック&提出 22:18  計 33:01


備考

➀ 0<=a<=b<=c<=Sとしても一般性を損なわないとして(a,b,c)の組み合わせを求めたのち、a,b,cを入れかえることですべてのケースを求める方針をとったが、a!=b!=cの場合の並び替えが3通りであるとしているのが誤りである気づくのに時間がとてもかかってしまった。

➁ もともと3重ループの方針にしたのはS=100であるからだったので、0<=a<=b<=c<=Sとしなくてもすべての場合を処理できた。これであれば条件設定せずすべての条件を満たすケースを数え上げることで正解できた。


# 213B Booby Prize

解答遷移 AC

問題把握 00:09  発想 00:00  base 00:37  デバック&提出 02:43  計 03:31

備考

➀ 問題の把握間違い

概要はつかめているのだが、2番目に小さいスコアを求めるものだと認識していた。そのためデバック時に修正作業が必要になった。どう考えても一発で正しいコードを書く方が早いので、要点だけでなく何を求めるのかをもう少し時間をかけてもよいので正しく認識すべきと感じた。

➁　リストの要素でindex番号を検索するの方法は .index(x)である


#  212B Weak Password

解答遷移 AC

問題把握 03:11 発想 00:01  base 04:56  デバック&提出 02:50  計 10:59

備考

➀ 速度ボトルネック

入力が文字列１つであること、1桁目と4桁目が連番であることは関係ないことを正しく認識できておらずループをかける範囲と入力形式の修正に時間をかけてしまった。



# 211B Cycle Hit

解答遷移 AC

問題把握 00:18  発想 00:00  base 01:22  デバック&提出 00:27  計 02:08

備考

➀ N行の入力それぞれを要素にしたリストの作成

[input() for _ in range(N)]



# 210B Bouzu Merkuri

解答遷移 Ac

問題把握 01:20 発想01:24  base&デッバク&提出 02:31  計05:16


備考

➀.index(x) はindex番号が最も若い要素xのindex番号を返す。

➁ 文字列の要素はstr型である。要素を取り出してその要素で条件設定するときなどstr型を使う必要があることに気を付ける


# 209B Can you buy them all

解答遷移 AC

問題把握 00:34 発想 00:14  base 01:50 　デバック&提案 01:32  計 04:13

備考

なし


# 208 B Factorial Yen Coin

解答遷移 AC

問題把握 01:42  発想 01:34  base 26:55  以下計測失敗(ただしデバックはすぐ終了している)


備考

➀ dp か否か

dpで特にはP<=10**7の制約はあまりにも重い。解説にはdpでもいけるとあり、実際提出も見受けられたが、自分でやると2200でTLEしてしまった。

https://atcoder.jp/contests/abc208/submissions/24021716

通るかどうかわからないギリギリのラインで、コーディングにまだ時間のかかるdpの方針をとるのはリスクが過ぎると感じた。制約と相談しながら別の発想でやる方がよいと感じる。

今回はXi+1=Xi*(i+1)の関係から、Y(>Xi+1)円支払う場合、Xi+1をXiより優先して支払う方が枚数を減らすことが可能である。なぜならXi+1をA枚支払う行為をXiを優先した場合A*(i+1)支払うことになるからである。したがって、大きい硬貨から順に支払うアルゴリズムでこの問題を解くことができる。





# 236A chukodai

解答遷移 AC

問題把握 00:21 発想 00:00 base 02:20  デバック&提出 01:14  計03:56

備考

なし



# 235A 

解答遷移 AC

問題把握 00:52  発想 00:00 base 00:50  デバック&提出 00:28  計 02:12 

備考

なし



# 207B Hydrate

解答遷移 AC

問題把握 02:16 発想 02:08  base 02:19  デバック&提出 00:28  計 07:12

備考

➀ ループ回数

何も考えず、必ず条件を満たす場合(B<C*D)においてwhileループを作成したが、ループ回数はTLEである保証がどこにもない。

この問題ではA<=(C*D-B)*xなのでx<=10*5であることを示せるので実行可能であるが注意したい。




# 234A Weird Function

解答遷移 AC

問題把握 01:52   発想  00:00  base 00:59  デバック&提出 00:28  計 01:52

備考

なし



# 0727

# 205B Saving

解答遷移 AC

問題把握 00:26 発想 00:01  base 04:15  デバック&提出 00:29  計 05:12

備考

なし

# 204B Permutation Check


解答遷移　AC

問題把握 00:24  発想 00:00  base 01:20  デバック&提出 00:49  計 02:35

備考

なし


# 204B Nuts

解答遷移 AC

問題把握 00:53  発想 00:00  base 01:07  デバック 01:19  計 03:20

備考

なし


# 203B Atcoder Condominium

解答遷移 AC

問題把握 00:39  発想 00:02 base 01:54  デバック 00:48

備考

なし


# BFS勉強

# BFSと再起関数

G=[[1,4,2],[3],[],[4],[],[3],[5],[2,5,6]] のとき頂点０からスタートしてたどり着ける頂点を全て求めたい。

ただしC[i][j]は頂点iからjに行けることを表している。

ここで再起関数がとても有効である。

def dfs(g):
    seen[g]=True
    for g_next in G[g]:
        if not seen[g_next]:
            dfs(g_next)
            
このような関数を作成すると頂点gからスタートして、その行き先であるg_nestが現時点で未踏でなければg_nextの行先を新たなスタートにするというものである。このときdfs(0)を実行すると経路は以下の通りである。

0 1 3 4 (4) 2 

まずseen[0]がTrueになり、g_next=1になる。

次にdfs(1)が実行されseen[1]がTrueになり、g_nest=3になる。

次はdfs(3)が実行されseen[4]=Trueになるが、g_nextが存在しないのでdfs(3)に戻るがg_nextが存在しないのでdfs(3)も終了する。続けてdfs(1)に戻りdfs(1)が終了する。

ここでdfs(0)に戻りg_next=4になるがseen[4]はすでにTrueなのでここで処理は終わりg_next=2となる。

dfs(2)が実行されるがg_nextが存在しないため終了し、dfs(0)に戻る。これまででdfs(0)におけるg_nextも存在しなくなったのでdfs(0)が終了し全ての処理が修了する。

seenのTrue要素がたどり着いた頂点を示しているのでそれを出力して解答できる。


# ATC 001A

➀ 再起関数野限界とその調整

再起関数の繰り返し処理は1000程度で止められるようである。

sys.setrecursionlimit(設定したい上限数)で自由に上限を設定しなおせるようである。この問題ではマス目すべてが"."だった場合にすべて検出すると2.5*10^5の繰り返しが必要になるのでそれより大きな数を設定しないとREになるケースが生まれる。

またpypyだとTLEになったので再起関数を扱う場合にはpythonで提出するのがよいと感じる





















