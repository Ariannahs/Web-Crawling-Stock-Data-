# Web-Crawling-Stock-Data-东方财富网股票数据爬取

东方财富网的股票信息存在于行情中心页面的“table” tag里面，网页改版后，不能从源代码读取table信息，因此我们想要爬的股票信息不能直接从html网页获取，需要利用开发者工具分析网页请求来源。

Task: 获取东方财富网中当日沪深A股股票名称和交易数据

original url: http://quote.eastmoney.com/center/gridlist.html#hs_a_board

idea: urllib.request—>response—>bs4 parser—>get and transform json data—>save csv file  
__

url_shsz='http://78.push2.eastmoney.com/api/qt/clist/get?cb=jQuery1124048191705730265766_1570855507672\
&pn=1&pz=3823&po=1&np=1&ut=bd1d9ddb04089700cf9c27f6f7426281&fltt=2&invt=2&fid=f3&fs=m:0+t:6,m:0+t:13,\
m:0+t:80,m:1+t:2,m:1+t:23&fields=f1,f2,f3,f4,f5,f6,f7,f8,f9,f10,f12,f13,f14,f15,f16,f17,f18,f20,f21,\
f23,f24,f25,f22,f11,f62,f128,f136,f115,f152&_=1570855507749'  

headers={'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.87 Safari/537.36'}  
request = r.Request(url_shsz, headers=headers)  
response = r.urlopen(request)  
html = response.read().decode('utf-8','ignore')  
soup = BeautifulSoup(html,'html.parser')  
__

complete code in link: https://github.com/Ariannahs/Web-Crawling-Stock-Data-/blob/master/Python%20Web%20Crawling%20-%20%E8%82%A1%E7%A5%A8%E6%95%B0%E6%8D%AE%E7%88%AC%E5%8F%96.ipynb
