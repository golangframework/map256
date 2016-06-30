# map256
map256是一种利用256叉树实现的树索引，map256读取效率高于原生map 35%左右，插入效率低于原生map16%,是一种牺牲空间来加速时间的树结构

## 用法
+ func GET(key)
+ func PUT(key)
+ func DET(key)

> same as PUT(nil)

+ func EXIST(key)

> same as (GET(key)!=nil)

## bench
```
insert(n)

     100		map	4.2376e-05	map256	5.2901e-05
    1000		map	0.000227041 map256	0.000408931
   10000		map	0.00223078	map256	0.004139328
  100000		map	0.043844378	map256	0.068796911
 1000000		map	0.53359707	map256	0.656570466
10000000		map	4.995001403 map256	6.510798805
20000000		map	9.169171322 	map256	10.956820013
30000000		map	15.179042239	map256	17.530382366
40000000		map	18.215705635	map256	22.872178363

由于内存40000000时候 map256已经占用光了16GB内存，所以无法再提高,map256目前来看内存占用是map的好多倍
14*1024*1024*1024/40000000=375

10*1024*1024*1024/250000000=42
find(n)

100             map256	2.0739e-05      map	1.1832e-05
1000		map256	0.000101596     map	0.000117562
10000	        map256	0.001093431	map	0.001727838
100000	        map256	0.013113676	map	0.01744656
1000000	        map256	0.1567763	map	0.209038154
10000000	map256	1.543412288	map	2.142344892
20000000	map256	3.238277679	map	4.273190382
30000000	map256	4.500983184	map	6.008312759
40000000	map256	6.165811638	map	9.203617515
100000000		                map	29.561792053
200000000		                map	59.91714011
```