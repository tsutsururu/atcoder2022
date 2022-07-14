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


# 7/15

pypyの実装。sys.stdinの勉強





