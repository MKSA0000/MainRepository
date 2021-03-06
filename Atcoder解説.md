## ACした問題たちについて解説

* ABC140 D Face Produces Unhappiness
    > 数列圧縮 <br>
    > LRの配列を0-1compressionして一回回すあたり最大2つDisjointが消せることに気づけば解ける

* TOITESU C Different Strokes
    > シグマの中抜け・式変形 <br>
    > 幸福度は sigma(自分の皿) - sigma(相手の皿) <- 目的関数 <br>
    > 変形して sigma(全部の皿[自分+相手]) - sigma(相手の皿[自分+相手]) - sigma(全部の皿[相手]) <br>
    > 従って sigma(自分の皿[自分+相手]) - sigma(全部の皿[相手])

* AGC038 A 01 Matrix
    > 出力行列をゼロのみの行列・１のみの行列にすれば構成可能　<br>

* ABC154 E Almost Everywhere Zero
    > 10**100とアホでかいのでdpを考える <br>
    > 1.    dp[i][j][k] で下からi桁目について，その桁がjのとき，（そのj桁を含めて）ゼロでない数が何個あるか，をdp配列に記憶させる iをメインループで回して前処理 <br>
    > あとはs = input()で貰った数を，大きい桁から足し合わせてゆけば解ける <br>
    > 2.   ## 桁dpという解法があるらしい <br>
    > 大きい桁からN以下となるようにdpで決めてゆく，このときNより確実に小さい/Nより小さいかもで２つdpテーブルを作って，10**0桁目で辻褄を合わせれば解ける <br>

* AGC019 B Reverse and Compare
    > アルファベットが登場する系(-> N進数系)の問題 <br>
    > こういうのは全探索O(N**2)，想定解O(N)の場合が多い <br>
    > 二分探索・尺取法など？<br>
    > N進数系は同じ値について接続を取り段々に積み上げる図を書くとわかりやすい <br>

* ABC165 Many Requiments
    > わからないので写した <br>
    > 広義単調増加数列なので全列挙が可能->10**10で諦めないで全列挙も候補に残しておく <br>
    > ## Combination全列挙方法
    > 1. 長さ1の数列(初期状態= {1})からi\>j => A_{i} \>= A_{j}を利用して，数列を順次生成する全部作ってO(nCk) <br>
    > 1. https://betrue12.hateblo.jp/entry/2020/05/02/233025
    > 1. https://note.com/nanigashi/n/n7cb379e2f3fd
    > 2. Pythonモジュール丸パクリ
    > ```python
    > from itertools import combinations_with_replacement as comb_rplc
    >   for seq in comb_rplc(range(1, 4), 2):
    >       print(seq)
    >
    >   (1, 1)
    >   (1, 2)
    >   (1, 3)
    >   (2, 2)
    >   (2, 3)
    >   (3, 3)
    > ```
    > 2. https://qiita.com/u2dayo/items/386142030a70d2db4e58

* ABC 039 D 画像処理
    > S->ImgSとする
    > 逆写像f^(-1)をGreedy searchで実装
    > S != Inv(ImgS)ならImpossible

* AGC 014 B Unplanned Queries
    > 接続辺をdirectに(u,v)で結んだ図を書いてみる <br>
    > どうやらすべての頂点についてrankが2nであることが必要十分ぽい <br>
    > GraphはTreeなのでDirectEdgesのうちいくらかを削除するが，削除する際にいい感じに回るから．<br>
    > 想定解法はLCAを使ってdist(u,v) = dist(r,u) + dist(r,v) - 2*dist(lc,u==v)になるからmod2でいい感じに処理できる <br>

* AGC 032 B Balanced Neighbors
    > 完全グラフからけずってゆく <br>
    > ### 教訓 構築系は
    > 1.    ゼロから追加
    > 2.    完全状態から削減

* CODEFESTIVAL 2017 Final C Time Gap
    > N~50と2**50に見えるがそうではない．<br>
    > 3回以上登場すれば答えはゼロ確定 <br>
    > 2回登場するときもd,24-dにバラして確定 <br>
    > 残った時刻について全探索しても2**12で余裕 <br>
    > ### time.max() - time.min()の差分を考えましょう!! e.g.: diff(22,0) = 2 <br>

* ARC 069 D Menagerie
    > 最初の2種類を決めたらあとは一意に定まる-> O(4) <br>
    > 演算規則を考えるのがめんどい <br>
    > 構成し終えたら全部チェックして合ってたらOK <br>

* ARC 097 D Equals
    > 典型的なgroupingの問題 <br>
    > 無向グラフを考えて，無向辺でつながっているgroup同士で数値の行き来は自由 <br>
    > 理想形({1,,,N})とグループごとでのsetを作りintersectで共通部分を取れば行ける <br>

* ABC 1-6 D AtCoder Express 2
    > N ~ 500で狭いのでN**2のi->jテーブルを作って<br>
    > (i,j) -> (x,y)の長方形に含まれる列車を数える，２次元累積和使えばO(1)でqueryを処理できる <br>
    > accum2Dのクラス作った，sum_squareも <br>

* ABC 152 E Flatten
    > Pythonなら脳死で通る <br>
    > ## LCM/GCDの計算方法 <br>
    > ### 数Xを素因数分解してmin(lp[i],rp[i]),max(lp[i],rp[i])をprime-wiseにかければgcd/lcmが出る <br>
    
* ABC 073 D joisino's travel
    > WarshallFloydで全点間最短経路->旅行する頂点を全部回す <br>
    > WarshallFloydのクラスをようやく作ったO(V**3) <br>
    > next_permutation(v.begin(),b.end())の使い方を覚えた do while <br>

* ABC 168 E Count Median
    > 最小値のMedianが取りうるMedianの下限 <br>
    > 最大値のMedianが取りうるMedianの上限は予想できる <br>
    > NがEvenかOddかで答えがだいたい２倍程度違う <br>
    > あとはindexを適当に調節するだけ <br>

* AGC 020 B Ice Rink Game
    > 各Roundのあとの生存人数をI[i]で管理する <br>
    > 計算量は各round O(1)で間に合う <br>
    > 下限は max(A[i],A[i]*ceil(I[i+1][0]/A[i])) <br>
    > 上限は A[i]*(floor(I[i+1][1] + 1)) <br>
    > I[i][0] > I[i][1]でアウトbreak  <br>
    > 面白い問題 <br>

* ABC 119 D Lazy Faith
    > STLのLower_boundで検索できる  <br>
    > 近くにある神社(up to 2)と寺(up to 2)を全探索 <br>

* AGC 039 B Graph Partition
    > むずすぎ３日悩んだ
    > dfsでunflodはunfoldの方向指定ができないので罪 <br>
    > 結果的に全点についてdfsして最大距離求める事になった <br>
    > 想定解はWarshall-Floydで全点間距離を求めてmax(dist[i][j])出だせる <br>
    > warshall-Floyd == 全点dfsのmax更新　の知見を得た <br>

* AGC 047 A Integer Product
    > めんどくさい　頭使う問題じゃない... <br>
    > ただの誤差論 double使うときはprecise converterと作る必要がある <br>
    > dotがある場合のconverterまでは実装した <br>

* AGC 031 B Reversi
    > 方針は昔から建てられていたが全然通らなかった <br>
    > 同じ数で分解してi番目のpositionにいる時点で最大何種類の塗り方が可能かdpする <br>
    > 勘違いしていたのはC_{i] < Sizeof Inputだと思ってたこと <br>
    > あとMOD取るのも最初忘れていた <br>
    > 実践だと通せないかも <br>

* ABC 059 C Sequence
    > 適当にやったら解けてしまった <br>
    > 初項を正にするか負にするかで2つ貪欲で調べて終わり <br>

* ARC 030 B ツリーグラフ
    > start indexが指定されていることを忘れていた，WAの嵐 <br>
    > 始点からbfsで根付き木に変換，後はLCAで一個ずつ頂点を追加していくだけ <br>

* ABC 128 D Equeue
    > 競プロの定石「操作は最後にまとめて」or「順序の可換性」<br>
    > 拾う数をT,take from left, take from right をそれぞれ定めて探索 R**3*logr程度 <br>

* ABC 117 D XXOR
    > bit-wise探索
    > 上の位からbitを建てるか考える, bitsetは速いので毎回to ulongに変換しても間に合う <br>
    > bitwiseにゼロの個数とイチの個数を数えてXORするから多いほうと反対のbitを選べば良い，このときKより大きくなるとアウトになる点にだけ注意する <br>
    > これが最適になる理由は考察していません． <br>
    > 上から数えたほうが得られるscoreが大きいので下から決定はありえんだろう，多分 <br>

* ABC 100 D Patisserie ABC
    > max(abs(sum x_ki)+abs(sum y_ki) + abs(sum z_ki)) <br>
    > ただの数学的式変形，非自明なんだが..... <br>
    > 変形すると max (+- x_ki +- y_ki +- z_ki)になる <br>
    > 要暗記 <br>

* ## 競プロ定石(for binary search)
    > min{max(F)}系の問題は maxFをbinary searchで決め打ちすればO(logN)でかなり自由度が高くなる <br>
    > minmaxF: 最大値の最小化 <br>　
    > 直近ではCDF Bandit in a city 最終的に捕まる数をFとすれば　すべてのleafでF人以下となるものを構成できれば良い <br>
    > 別の類題はABC E-Logs　構成できるLog Lengthを Fで決め打ちする <br>

* ABC 032 C 列
    > 最近水色50%帯の問題で停滞気味...最低一日１ACはしたい <br>
    > 尺取り法の典型問題 <br>
    > 尺取り法マスターしよう <br>
    > https://scrapbox.io/pocala-kyopro/%E3%81%97%E3%82%83%E3%81%8F%E3%81%A8%E3%82%8A%E6%B3%95 <br>


* ## 尺取り法
    > [left,right)の区間で考える left==rightなら空集合 <br>
    > leftのインクリメントをfor loopに吸収させてrightのインクリメントとleft==rightの処理だけ考える <br>
    > 基本的にleft == rightなら処理を初期化してright++でOK <br>
    > leftのインクリメントが自動なのでfor loopの最後でleft++処理の下準備をしておく <br>
    > rightそのもので条件が満たされるときright+1して半開区間のincrementを実行する <br>
    > ```c++
    > signed main(){
    > int N,K; cin >> N >> K;
    > vector<int> vec(N);
    > bool zflag = false;
    > rep(i,N){
    >     cin >> vec[i];
    >     if(vec[i] == 0) zflag = true;
    > }
    > 
    > auto chakutori = [&](){
    >     int right = 0;
    >     int val = 1;
    >     int res = 0;
    >     for(int left = 0; left < N; left++){
    >         while(right < N && val * vec[right] <= K){
    >             val *= vec[right];
    >             right += 1;
    >             
    >             res = max(res,right-left);
    >         }
    > 
    >         if(right == left){
    >             val = vec[right];
    >             right++;
    >         }else{
    >             val /= vec[left];
    >             left++;
    >         }
    >     }
    >     return res;
    > };
    > int ans = chakutori();
    > if(zflag){
    >     ans = N;
    > }
    > cout << ans << endl;
    > ``` 
    > ### コードスニペット２号
    > ```c++
    > int right = 0;
    > for(int left = 0; left < n; left++){
    >   while(right < n && 条件){
    >     rightを右に動かす処理
    >   }
    > 
    >   何かしらの処理
    > 
    >   if(left == right){   // leftがrightに追いついたら
    >     どうにかする
    >   }
    > }
    > ```

* Tenka1 2014 Preliminary B Eternal Static Final
    > DPの典型問題，区間の指定で迷って時間をかけてしまった <br>
    > 基本競プロで範囲を"プログラムする"ときは半開区間[l,r)で考える，クエリに答えるときだけ調節する <br>
    > 今回の範囲はdp[i]を[0,i)までのfrac_spellの組み合わせの数とした <br>
    > 即ち，[0,i]を埋め尽くすfrac_spellの順列の数 <br>
    > str.substr(offset,count)なのでこのsubstrが取り出す範囲は[offset,offset+count)となることに注意！！->範囲の右端が飛び出ることはない <br>

* ABC 098 D Xor Sum 2
    > ## 競プロ定石 a + b - (a xor b) = 2 * (a and b)
    > が成立するから一般に a xor b <= a + bが成り立つ <br>
    > 等号成立条件はbがaのビットを一つも下げないこと <br>
    > [L,R]でRを増やしてゆくとき等号成立条件はstrictly stricterに変化してゆくので[L,R]で成立するならばその中では全部成立する <br>
    > 尺取り法が使える <br>
    > 尺取り法の定石を抑えよう <br>

* Codefest 2016 C
    > 左右から上を抑えてゆく，各山についてPossible Range [mi,Mi]を定めておいてviolationが発生したら終わり <br>

* ABC 142 E Get Everything
    > Nが12と小さいのでNについてbit全探索を考える <br>
    > まず状態をxxxoooxoxoというように開けられる宝箱の位置がtrueになるようなbitsetを考える <br>
    > 各鍵を使って遷移できる状態を鍵ごとに辺として張る <br>
    > 即ち開けられる宝箱の状態bitsetをノードとして鍵を買うことによる遷移を辺とするグラフ <br>
    > あとはxxxxxxからooooooへDjikstraで探索，最小値を出して終わり <br>

* Codefest 2015 B ヘイホーくんと削除
    > 平方文はどこかに必ず対称線があるからその対称線について全探索 <br>
    > 対称線についてきりだして最長共通部分列(LCS)の長さを考えて一番でかいのが答え <br>
    > LCSの解法学んだ <br>

* ABC 153 F Silverfox vs Monster
    > 座標圧縮して貪欲で潰す <br>

* ABC 105 D Candy Distribution
    > 天才解法
    > 値 A_{i}について半開区間の累積を取ると S_{i}
    > for some i,j: sum[a_{i} +++ a_{j}]とはS_{j+1} - S_{i+1}だから <br>
    > この差がmodMでゼロとはすなわちS_{j+1} == S_{i+1}ということ <br>
    > あとはあまりをmapで管理してNC2すれば終わり！！ <br>
    > ## "このような「Mで割った余りが〜」系の問題は、元からMで割った余りを出しておくと考察が上手くいくことが多いです…"

* Codefest 2014 Easy C 身体バランス
    > 始点sと終点tからDijkstraで最短経路求めるx2で同じ距離の点が存在すればOK <br>

* ABC 022 C Blue Bird
    > タスクはindex0を含むような最短閉路を見つけること <br>
    > 自分の解法: 閉路であるとき0でないNode uを通るから u ---> zeroでまずDijkstraで距離を求める　帰りがけにこのルートをweight => infで潰しておく <br>
    > もう一度 Dijkstraで距離を求める　足してnode u についてforeach minを取れば答え <br>
    > 想定解: 閉路であるとは0から２つedgeが生えているからzero indexからdist < 2の部分を引っこ抜けば良くて，Warshall-Floydで残ったnodeたちに全点対最短経路を求めておけば適当に足せば答えが求まる <br>
    > ランダウOの計算量はだいたい同じはずなのに差が大きすぎ... <br>

* ABC 161 F Division or Subtraction
    > 自分の解法: 適当に式変形すれば N = K**p * (1 + qK) と分かる　このときp = 0, p = 1の場合がN ~ **12 で直接計算不能なので約数前列挙する <br>
    > O(sqrt(N))なので間に合う <br>
    > p > 1は適当にやっても間に合う <br>
    > 想定解は一度もdivisionが怒らないK <=> N mod K == 1 でN-1の約数全列挙で終わり <br>
    > 一度以上divisionがある時これらはNの約数であるから約数全部調べて終わり <br>
    > 今回の想定解はdivison ----------> subtractionの変わり目に注目した，すなわち一度以上divideするor NOT
    > ## 教訓 操作の変わり目に注目せよ | 操作をそもそも行うかに注目せよ

    
