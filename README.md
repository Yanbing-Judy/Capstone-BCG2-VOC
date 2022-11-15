# Capstone-BCG2-VOC


## Web Crawling Reference

**汽车之家--爬虫参考**

* 根据目前的研究，没有反爬虫限制

* https://www.cnblogs.com/c1033383881/p/15865985.html

* https://cloud.tencent.com/developer/article/1727209

* https://www.ycpai.cn/python/d94Y8uBJ.html

**爬虫具体步骤**
1. 先获取汽车之家上所有的车系和车型及对应的eid

  * 分别爬取A-Z开头的各个车型：https://www.autohome.com.cn/grade/carhtml/B.html
  
  * 归类：“在售”或者“未售/停售” （我们主要关注在售车型，若有时间再加上未售和停售车型）


2. 根据id，跳转口碑页面，每页返回数据条数为20条评论
  
  * 例如：Lexus-ES 口碑页面 -- https://k.autohome.com.cn/403
  
  * Lexus-ES 2nd page -- https://k.autohome.com.cn/403/index_2.html?#listcontainer
  

3. 爬取评分和评论跳转页面
  * 整体的维度评价，页面上的具体位置示例：<div class="score_score__f68lA">,具体数据内容{"seriesId":403,"newCarPPH":76,"newCarPPHUserCount":117,"seriesName":"雷克萨斯ES","score":"4.53","maxItemScore":"5.00","maxItemName":"舒适性","reliabilityPPH":96,"reliabilityPPHUserCount":206}

  * 评论页面提取：<a target="_blank" href="https://k.autohome.com.cn/detail/view_01ggp29g916gv3cc1p70t00000.html#pvareaid=2112108" rel="noreferrer">查看完整口碑<i class="list_arrow_right__EtpQA list_icon__aL4pn"></i></a>

4. 爬取口碑数据

  * 以<h1>作为不同variable提取内容，例如<h1>最满意</h1>、<h1>最不满意</h1>、<h1>空间</h1>等，其中空间等数据包括评分和内容，两部分内容

