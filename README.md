# onepiece
用以爬取腾讯动漫上的航海王漫画

chromedriver.exe必须和脚本放在同一目录下
理论上支持腾讯动漫所包括的全部动漫，但现在在代码层面只设置了爬取航海王的
设置隐式等待时间为10s，当鼠标拖拽到具体图片时，会暂停（sleep）2s，保证图片加载完成，同时防止被反

不知道什么时候才做的改进方案
改用headless chrome，使得爬取时，更节省资源
记录上一次爬取的位置，从而可以在意外中断（关机）之后，继续爬取
结合上一条，做到章节更新的检测
提供更丰富的细节反馈，更简单地发现爬虫爬取数据时的异常

2018.6.6更新
将隐式等待时间更改为显式等待时间，当图片一准备好，马上开始下载，速度大为提升
经测试，原始版本爬取海贼王第904，905话，共用时150s，改进后用时48s

2018.6.9更新
在让小伙伴给我测试的时候，他提到，要是我没有chrome怎么办，这确实是我没有考虑到的问题
创建chrome的webdriver失败之后，会尝试创建IE的webdriver（未测试）
可以选择爬取之后的图片储存位置

2018.9.5
偶然发现，使用Kindle Comic Converter生成mobi漫画，看起来更舒服更好看
修改代码时，发现冗余的功能多了之后就不好管理了，遂重构加删除用不上的功能
新增
-使用headless chrome，爬取更省资源（吧）
-对代码进行了简单优化
-对大于两集的爬取，将从中间分割，交由两个进程共同处理。
删除
-没有chrome的处理
-选择保存的文件夹
之所以删除上述功能，是因为，多输入两次着实麻烦，写爬虫就是怕麻烦

2018.9.6
今天经大佬点播，发现其实用一个配置文件会更好，于是。。。
增加配置文件，爬取的动漫，保存的位置都可以在里面设置
配置文件中还有一项为最后爬取的集数，爬虫会将正常结束的最大集数写入，且在运行爬虫是，可以选择按照最后爬取的集数再往下爬取4集
新增多进程爬取，在选择集数时，会在后台打开两个浏览器进程，爬取更快更省时间

2018.9.7
修复上一版诸多bug

2018.9.9
配置文件改用明文，csv格式储存，可直接修改相应的设置
偶然发现并修复了一个bug
