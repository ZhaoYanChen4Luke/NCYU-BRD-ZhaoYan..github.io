# NCYU-BRD-ZhaoYan..github.io

title : WOW

author :
  name : 昭延陳
  
  



## 一、	家庭背景

我是陳昭延，出生在一個可愛的小家庭，裡頭有五個家庭成員，分別是爸爸、媽媽、姐姐、我以及弟弟，我在家中排行老二，是個會幫忙父母照顧弟弟的好哥哥。爸爸的工作為研究員，也因父親的工作讓我朝著科學研究方面邁進。我會教弟弟功課且替他解惑。而我有學業上的問題都會問姊姊，在一些勞作或是其他等作業，也會請教姊姊，她都會給我一些建言。
    偶爾，我也會請教姊姊人生課程。平時我都會與媽媽分享在學校發生的事情，讓媽媽了解我在校情形。最後是我人生的心靈導師¬¬-爸爸。爸爸總是在我意志消沉時，給我鼓勵；在我墮落荒廢時，給我當頭棒喝。總之，我真的很幸運、幸福，每當我需要幫助時有援手伸出，當我需要訴苦時有人傾聽。感謝老天爺所給予我這麼好的家人。

## 二、	個人特質及生活態度

我的個性溫和、內向、樸實，是個很好溝通的人。每當遇到沮喪或瓶頸，我都會以積極正向的態度去面對。在學校生活裡，我以親切有禮貌的態度與老師同學相處，人際關係十分融洽，也從中獲益良多。我對於生活的態度就是「不管對或錯只要對自己負責」。

## 三、	求學歷程

在高一寒假時加入圖書館志工，為民眾服務，體驗公務員的職場生活，在升高二時參加監理站的小志工，學習公務人員基本的文書處理。約在三月去成功大學一日的教育參訪之旅，又在七月參加清華大學物理系辦的「輻射與原子核能隱形能量知識深耕」科學營。
    上國立嘉義大學後，我積極參與系上的活動，大採、小採等活動。開始投入對生物的認識，雖說不是很懂或該說生物是越去認識他越是不了解他，這也是生物迷人之處。我也參與學校的社團-水上活動社。從不會游泳到會游泳，積極學習其他水上活動，例如水球、獨木舟、救生等等。現在擔任副社長，努力推廣水上活動給學校全體同學認識。讓他們對於水域安全及水上活動有更深一成的認識。



大家好～歡迎來到阿延的繁星夜空------第八夜


晚安各位 謝謝你們的閱讀與支持
祝你們有個好眠，明天又是美好的一天
期待下次與你的分享
若有悄悄話歡迎隨時密我，這裡是專屬你的天空
阿延的繁星夜空下次見 掰掰

2016.12.30
#參考老師的網址
https://gist.github.com/mutolisp/d6cc6db990c9e50eb0530bad49a3ce40
Quick-R graphics 網址
http://www.statmethods.net/graphs/
 
data (iris)

#使用iris資料繪圖
#histogram 柱狀圖

sepalLength <- iris$Sepal.Length
hist(sepalLength , breaks = 15)

#點圖
#R plot pch 可以搜尋得到點樣子的種類
plot(sepalLength)
plot(sepalLength , type = 'p', pch = 19) 

# 1.1 改變顏色和符號(pch)
plot(sepalLength, type = 'p',
     pch = 19, col = 'green')
# 1.2 加上 title
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = 'Sepal Length (cm)')
# 加上 x & y labels
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = 'Iris data — sepal length',
     xlab = 'index\n(sequence)', ylab = 'Sepal length (cm)')
# 加上文字(text)
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = 'Iris data — sepal length',
     xlab = 'index', ylab = 'Sepal length (cm)')
# \n 代表換行
text(5,7,'Iris\n data \nexample')
# 加上矩型
rect(xleft = 5, ybottom = 6, 
     xright = 25, ytop = 7)

# 控制 axes
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = 'Sepal Length (cm)', axes = FALSE)
# side 1, 2, 3, 4 分別代表下左上右
axis(side = 2)
axis(side = 4)

# 開啟繪圖裝置，windows 系統請用 windows()
# MacOS 請使用 quartz()，GNU/Linux 可使用 x11()
# 這些會直接於螢幕上繪出
# 如果要輸出成不同格式，要使用 png, pdf, etc.
pdf(file = '~/Desktop/test.pdf')
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = 'Iris data — sepal length',
     xlab = 'index\n(sequence)', 
     ylab = 'Sepal length (cm)')
dev.off()

# 如果碰到中文的問題，可以使用 Cairo 套件來解決
library(Cairo)
CairoFonts(regular = "Noto Sans T Chinese:style=Light", bold = "Noto Sans T Chinese:style=Regular")
Cairo(1200, 1200, file ='/tmp/test_cairo.pdf', 
      type = 'pdf',
      pointsize=8, dpi = 150)
plot(sepalLength, type = 'p',
     pch = 19, col = 'red', 
     main = '鴛尾花資料集',
     xlab = 'index', 
     ylab = '萼片長度 (cm)')
dev.off()

# boxplot
# 使用 boxplot 繪製 sepal length
boxplot(sepalLength)
# 使用 boxplot 繪製 sepal length, setal width,
# petal length 以及 petal width
boxplot(iris[,1:4])
boxplot(iris[,1:4], col = '#ff0000')

# 調整 margin
par(mar = c(3, 4, 5, 3) )
boxplot(iris[,1:4], lwd = 0.8, col = '#ff0000')


# 把圖組合起來
# 可以使用 graphical parameter mfrow
# 或是用 layout 來控制
par(mfrow = c(2,1))
par(mar = c(2,2,2,2)+0.5 )
boxplot(iris[,1:4]*rnorm(1), lwd = 0.8, col = '#ff0000', main = 'Species A')
boxplot(iris[,1:4]*rnorm(1), lwd = 0.8, col = 'darkgreen', main = 'Species B')

#加上趨勢線
-------
plot(iris$Sepal.Width, iris$Sepal.Length,
     xlab = 'Sepal.Length' ,
     ylab = 'Sepal.Width')
lm.results <- lm(Sepal.Width-Sepal.Length, data=iris)
abline(lm.results)
abline(h=4.5, lty = 4)
legend(4.5, legend = 'a')
-----
# 折線圖
plot(sepalLength, type = 'l',
     pch = 19, col = 'green')

